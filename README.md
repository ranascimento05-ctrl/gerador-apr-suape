# 🚀 Gerador APR Suape — Orbit 360

Aplicação web para geração automatizada de APR (Análise Preliminar de Riscos) com fidelidade 100% ao template oficial Porto de Suape.

## 📋 Estrutura

```
.
├── public/
│   └── index.html          (Frontend — HTML + CSS + JS)
├── api/
│   └── generate.py         (Backend — Serverless Function)
├── vercel.json             (Config Vercel)
├── requirements.txt        (Dependências Python)
├── .env.local              (Variáveis de ambiente — local)
└── README.md
```

## 🛠️ Setup Local (Teste)

### 1. Clonar & Instalar

```bash
cd vercel_project
pip install -r requirements.txt
```

### 2. Variáveis de Ambiente

Copiar `.env.local` para `.env` (ou usar como está).

### 3. Rodar Localmente

```bash
# Para testar o frontend
python -m http.server 8000

# Abrir: http://localhost:8000/public/index.html
```

## 🌐 Deploy em Vercel

### 1. Requisitos

- Conta Vercel (grátis): https://vercel.com
- Git + GitHub/GitLab/Bitbucket

### 2. Passos

#### Opção A: Deploy via GitHub (Recomendado)

1. **Push para GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/seu-usuario/gerador-apr
   git push -u origin main
   ```

2. **Conectar Vercel**
   - Ir para https://vercel.com
   - Clicar "Import Project"
   - Selecionar repositório GitHub
   - Vercel detecta automaticamente

3. **Variáveis de Ambiente**
   - Ir para **Settings → Environment Variables**
   - Adicionar: `TEMPLATE_BASE64` = (valor de `.env.local`)
   - Deploy automático

#### Opção B: Deploy via CLI

```bash
# Instalar Vercel CLI
npm install -g vercel

# Deploy
vercel

# Setup interativo detecta estrutura
# Selecionar "Python 3.11" para runtime
```

### 3. Configurar Template (Importante!)

No Vercel Dashboard:
1. Projeto → Settings → Environment Variables
2. Adicionar variável:
   - Nome: `TEMPLATE_BASE64`
   - Valor: (copiar de `.env.local`)
3. Salvar e re-deploy

```bash
vercel --prod
```

## 📝 Como Usar (TST)

1. Abrir link da aplicação (ex: https://gerador-apr.vercel.app)
2. Preencher formulário com dados da atividade
3. Clicar "Revisar & Gerar"
4. Clicar "Gerar Excel Agora"
5. Arquivo baixa automaticamente ✅

## 🎨 Customização

### Mudar Logo
- Editar `public/index.html`, linha ~150
- Substituir SVG `data:image/svg+xml` pela sua imagem

### Mudar Cores (Orbit 360)
- Editar `:root { ... }` em `<style>`
- Cores atuais:
  - Azul: `#3b82f6`
  - Roxo: `#a855f7`
  - Verde: `#10b981`
  - Escuro: `#0a0e27`

### Adicionar/Remover Campos
- Editar formulário em `public/index.html`
- Mapear campos no `api/generate.py` função `preencher_apr_suape()`

## 🔧 Troubleshooting

### Erro 500 ao gerar
- Verificar se `TEMPLATE_BASE64` está configurado
- Ver logs em Vercel Dashboard → Functions

### Download não funciona
- Verificar CORS (já configurado)
- Testar em navegador diferente

### Template não preenchido
- Confirmar que arquivo `.xlsx` é válido
- Verificar mapeamento de células em `generate.py`

## 📊 Performance

- **Frontend**: ~50KB (HTML + CSS + JS inline)
- **Backend**: ~2-3s por geração (openpyxl)
- **Grátis**: Vercel: até 100 req/dia
- **Pro**: Vercel: unlimited (R$ 20/mês)

## 💼 Comercialização

### Preço Sugerido
- Free: 2 APRs/mês (teste)
- Basic: R$ 20/mês (5 APRs)
- Pro: R$ 50/mês (15 APRs)
- Enterprise: R$ 100/mês (ilimitado)

### Implementar Limite de Uso
Modificar `api/generate.py` para:
1. Receber token do cliente
2. Validar contra BD (Firebase, Supabase, etc)
3. Decrementar contador de APRs
4. Retornar erro se limite atingido

## 📞 Suporte

- Email: ralmeida@decalbrasil.com
- Documentação: https://github.com/seu-repo/wiki

## 📄 Licença

© 2026 Orbit 360 — Todos os direitos reservados.

---

**Deploy Status**: [![Vercel Status](https://img.shields.io/badge/vercel-deployed-blue)](https://vercel.com)
