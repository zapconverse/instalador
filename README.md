# 🚀 Zapconverse - Instalador Automático

Sistema de atendimento multicanal com WhatsApp integrado.

## 📋 Sobre o Instalador

Este repositório contém o **instalador automático** do Zapconverse, permitindo instalação e gerenciamento completo do sistema através de um menu interativo.

## ✨ Funcionalidades

- ✅ **Instalação automática** de todas as dependências
- ✅ **Menu interativo** para gerenciamento
- ✅ **Multi-instâncias** no mesmo servidor
- ✅ **Configuração de SSL** automática
- ✅ **Gerenciamento de domínios**
- ✅ **Bloqueio/Desbloqueio** de instâncias

## 🛠️ Pré-requisitos

- Ubuntu 20.04 ou 22.04
- Acesso root via SSH
- Mínimo 2GB RAM (recomendado 4GB)
- Domínios apontados para o servidor (para SSL)

## 📦 Instalação Rápida

### 1️⃣ Acessar servidor via SSH
```bash
ssh root@SEU_IP
```

### 2️⃣ Baixar o instalador

**Opção 1:** Se o repositório for público:
```bash
cd /home
git clone https://github.com/zapconverse/instalador.git
cd instalador
```

**Opção 2:** Se o repositório for privado (substitua SEU_TOKEN):
```bash
cd /home
git clone https://zapconverse:SEU_TOKEN@github.com/zapconverse/instalador.git
cd instalador
```

### 3️⃣ Dar permissões
```bash
chmod -R 777 instalador
```

### 4️⃣ Executar instalador
```bash
./install_primaria
```

## 📱 Menu Interativo

Após executar o instalador, você verá o menu:

```
╔══════════════════════════════════════════╗
║          ZAPCONVERSE                     ║
╚══════════════════════════════════════════╝

💻 Bem vindo(a) ao Gerenciador Zapconverse

[0] Instalar Zapconverse
[1] Atualizar Zapconverse
[2] Deletar Zapconverse
[3] Bloquear Zapconverse
[4] Desbloquear Zapconverse
[5] Alter. domínio Zapconverse
```

## 🎯 Opções do Menu

### [0] Instalar
Instala uma nova instância do Zapconverse. Durante a instalação será solicitado:

- **Senha do banco de dados**
- **Nome da instância** (sem espaços ou caracteres especiais)
- **Quantidade de conexões WhatsApp**
- **Quantidade de usuários/atendentes**
- **Domínio do frontend** (ex: app.seudominio.com)
- **Domínio do backend** (ex: api.seudominio.com)
- **Porta do frontend** (ex: 3000-3999)
- **Porta do backend** (ex: 4000-4999)
- **Porta do Redis** (ex: 5000-5999)

### [1] Atualizar
Atualiza uma instância existente para a versão mais recente do código.

### [2] Deletar
Remove completamente uma instância do servidor (banco de dados, arquivos, etc).

### [3] Bloquear
Bloqueia temporariamente o acesso a uma instância.

### [4] Desbloquear
Desbloqueia uma instância previamente bloqueada.

### [5] Alterar domínio
Permite alterar os domínios (frontend/backend) de uma instância existente.

## 📂 Estrutura do Projeto

```
instalador/
├── install_primaria         # Script principal com menu
├── install_instancia        # Instalação de instâncias adicionais
├── lib/                     # Bibliotecas de funções
│   ├── _inquiry.sh         # Menu interativo
│   ├── _system.sh          # Instalação de dependências
│   ├── _backend.sh         # Configuração backend
│   └── _frontend.sh        # Configuração frontend
├── utils/                   # Utilitários
│   └── _banner.sh          # Banner ASCII
└── variables/               # Variáveis e configurações
    ├── _fonts.sh           # Cores do terminal
    └── _app.sh             # Variáveis da aplicação
```

## 🔧 Comandos Úteis

### Ver logs
```bash
pm2 logs nome-da-instancia-backend
pm2 logs nome-da-instancia-frontend
```

### Reiniciar serviços
```bash
pm2 restart nome-da-instancia-backend
pm2 restart nome-da-instancia-frontend
```

### Ver status
```bash
pm2 status
```

### Verificar portas em uso
```bash
netstat -tuln | grep :PORTA
```

## 🌐 Multi-Instâncias

É possível instalar múltiplas instâncias no mesmo servidor:

1. Execute `./install_primaria`
2. Escolha opção **[0] Instalar**
3. Use **nome diferente** para cada instância
4. Use **portas diferentes** (ex: 3000, 4000, 5000 para instância 1 / 3001, 4001, 5001 para instância 2)
5. Configure **domínios diferentes**

## 🔐 Configuração SSL

O instalador configura SSL automaticamente via Certbot quando você fornece domínios válidos.

**Importante:**
- Os domínios devem estar apontando para o IP do servidor (DNS configurado)
- Certbot irá validar o domínio antes de emitir o certificado
- Certificados são renovados automaticamente

## 📝 Dependências Instaladas

O instalador configura automaticamente:

- ✅ Node.js 20.x
- ✅ PostgreSQL
- ✅ Redis (via Docker)
- ✅ PM2 (gerenciador de processos)
- ✅ Nginx (proxy reverso)
- ✅ Certbot (SSL)
- ✅ Puppeteer dependencies

## 🆘 Troubleshooting

### Erro de permissão
```bash
chmod +x install_primaria
```

### Porta já em uso
```bash
# Verificar processo usando a porta
lsof -i :PORTA
# Matar processo
kill -9 PID
```

### Nginx não inicia
```bash
sudo nginx -t          # Testar configuração
sudo systemctl restart nginx
```

### PM2 não encontrado
```bash
npm install -g pm2
```

## 📞 Suporte

- **GitHub Issues:** https://github.com/zapconverse/instalador/issues
- **Documentação:** https://github.com/zapconverse/instalador

## 📄 Licença

Este projeto está sob a licença MIT.

---

**2025 © Zapconverse - Todos os direitos reservados**
