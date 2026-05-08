# 🌾 Site 3M Agropecuária - Guia de Publicação

## 📁 Estrutura do Projeto

```
site-fazenda/
├── index.html          (Página Inicial)
├── fazenda.html        (A Fazenda - Contatos e Localização)
├── carreiras.html      (Vagas Disponíveis)
├── cadastro.html       (Formulário de Currículos)
├── css/
│   └── style.css       (Estilos Completos)
├── js/
│   └── script.js       (Interatividade)
└── README.md           (Este arquivo)
```

---

## 🚀 Como Publicar no GitHub Pages (100% GRATUITO)

### Passo 1: Criar Conta no GitHub

1. Acesse: https://github.com
2. Clique em **"Sign up"** (Cadastrar)
3. Use um e-mail profissional (ex: `rh.fazenda3m@gmail.com`)
4. Escolha um nome de usuário (ex: `fazenda3m`)
5. Confirme o e-mail

### Passo 2: Criar Repositório

1. Faça login no GitHub
2. Clique no botão **"+"** (canto superior direito) → **"New repository"**
3. Preencha:
   - **Repository name:** `site-fazenda` (ou qualquer nome)
   - **Description:** "Site institucional da 3M Agropecuária"
   - Marque: **✓ Public** (para usar GitHub Pages grátis)
   - Marque: **✓ Add a README file**
4. Clique em **"Create repository"**

### Passo 3: Upload dos Arquivos

**Opção A - Via Interface Web (Mais Fácil):**

1. No repositório criado, clique em **"Add file"** → **"Upload files"**
2. Arraste TODOS os arquivos e pastas do projeto:
   - `index.html`
   - `fazenda.html`
   - `carreiras.html`
   - `cadastro.html`
   - Pasta `css/` com `style.css`
   - Pasta `js/` com `script.js`
3. Adicione uma mensagem: "Upload inicial do site"
4. Clique em **"Commit changes"**

**Opção B - Via GitHub Desktop (Recomendado se você vai editar muito):**

1. Baixe: https://desktop.github.com
2. Instale e faça login
3. Clone seu repositório
4. Copie os arquivos para a pasta local
5. Commit e Push

### Passo 4: Ativar GitHub Pages

1. No repositório, vá em **"Settings"** (Configurações)
2. No menu lateral esquerdo, clique em **"Pages"**
3. Em **"Source"**, selecione:
   - Branch: **main**
   - Folder: **/ (root)**
4. Clique em **"Save"**
5. **AGUARDE 2-5 MINUTOS** (o GitHub está publicando)
6. Recarregue a página
7. Aparecerá um link verde: 
   ```
   Your site is live at https://SEU-USUARIO.github.io/site-fazenda/
   ```

🎉 **PRONTO! Seu site está no ar e GRATUITO!**

---

## 🔗 Integrando o Google Forms

### Passo 1: Criar o Formulário

1. Acesse: https://forms.google.com (logado na conta @gmail.com que você criou)
2. Clique em **"Criar formulário em branco"**
3. Título: "Cadastro de Currículos - 3M Agropecuária"
4. Adicione os campos (veja exemplo abaixo)

### Passo 2: Campos do Formulário

Configure exatamente estes campos:

1. **Nome Completo** (Resposta curta, obrigatório)
2. **CPF** (Resposta curta, obrigatório)
3. **E-mail** (Resposta curta, obrigatório, validação de e-mail)
4. **Telefone/WhatsApp** (Resposta curta, obrigatório)
5. **Cidade onde reside** (Resposta curta)
6. **Vaga de interesse** (Lista suspensa):
   - Tratador de Gado
   - Operador de Máquinas Agrícolas
   - Assistente Administrativo Rural
   - Cadastro Geral (sem vaga específica)
7. **Escolaridade** (Múltipla escolha):
   - Ensino Fundamental
   - Ensino Médio
   - Técnico
   - Superior Completo
   - Superior Cursando
   - Pós-Graduação
8. **Experiência anterior na área** (Parágrafo)
9. **Currículo (PDF)** → tipo: **"Upload de arquivo"**
   - Configurações: Permitir apenas tipos específicos → PDF
   - Tamanho máximo: 10 MB

### Passo 3: Vincular à Planilha

1. No Forms, clique na aba **"Respostas"** (topo)
2. Clique no ícone verde do Sheets (criar planilha)
3. Selecione **"Criar uma nova planilha"**
4. Nome: "Banco de Currículos - Fazenda"
5. Clique em **"Criar"**

Agora toda candidatura vai aparecer automaticamente nessa planilha!

### Passo 4: Incorporar no Site

1. No Google Forms, clique em **"Enviar"** (botão roxo, canto superior direito)
2. Clique no ícone **`< >`** (Incorporar HTML)
3. Copie o código que aparece (exemplo):
   ```html
   <iframe src="https://docs.google.com/forms/d/e/1FAI..." width="640" height="1200"></iframe>
   ```
4. Abra o arquivo `cadastro.html` no seu editor
5. **LOCALIZE** o bloco amarelo de aviso (linha ~185)
6. **APAGUE** todo o `<div class="embed-aviso">...</div>`
7. **COLE** o código do iframe no lugar
8. **AJUSTE** o width para `100%` (para ficar responsivo):
   ```html
   <iframe src="https://docs.google.com/forms/d/e/SEU_ID/viewform?embedded=true" 
   width="100%" height="1200" frameborder="0" marginheight="0" marginwidth="0">
   Carregando…
   </iframe>
   ```
9. Salve o arquivo
10. Faça upload novamente no GitHub (substitui o arquivo antigo)

---

## 📧 Notificação Automática por E-mail (BÔNUS)

Como você já domina Google Apps Script, adicione isto na planilha:

1. Na planilha de currículos, vá em **Extensões → Apps Script**
2. Cole este código:

```javascript
function notificarNovoCurriculo(e) {
  const linha = e.values;
  const timestamp = linha[0];
  const nome = linha[1];
  const cpf = linha[2];
  const email = linha[3];
  const telefone = linha[4];
  const cidade = linha[5];
  const vaga = linha[6];
  const escolaridade = linha[7];
  const experiencia = linha[8];
  const curriculo = linha[9]; // Link do arquivo no Drive
  
  const destinatario = 'rh@3magro.com.br'; // ALTERE PARA SEU E-MAIL
  
  const assunto = `Novo Currículo Recebido - ${nome}`;
  
  const corpo = `
    Um novo currículo foi cadastrado no site!
    
    📋 DADOS DO CANDIDATO:
    Nome: ${nome}
    CPF: ${cpf}
    E-mail: ${email}
    Telefone: ${telefone}
    Cidade: ${cidade}
    Vaga: ${vaga}
    Escolaridade: ${escolaridade}
    
    💼 EXPERIÊNCIA:
    ${experiencia}
    
    📄 CURRÍCULO:
    ${curriculo}
    
    ---
    Acesse a planilha completa: ${SpreadsheetApp.getActiveSpreadsheet().getUrl()}
  `;
  
  GmailApp.sendEmail(destinatario, assunto, corpo);
}
```

3. Salve (Ctrl+S)
4. Clique em **"Gatilhos"** (ícone de relógio, menu lateral esquerdo)
5. **+ Adicionar gatilho**
6. Configurações:
   - Função: `notificarNovoCurriculo`
   - Origem do evento: **Da planilha**
   - Tipo de evento: **Ao enviar formulário**
7. Salve

Agora você recebe e-mail instantâneo toda vez que chegar um currículo!

---

## ✏️ Personalizando o Site

### Trocar Cores

Edite o arquivo `css/style.css`, nas primeiras linhas:

```css
:root {
    --verde-escuro: #2D5016;    /* Cor principal escura */
    --verde-principal: #4A7C2C; /* Cor dos botões */
    --verde-claro: #7CB342;     /* Cor de destaque */
    --terra: #8B6F47;           /* Cor terracota */
}
```

### Adicionar Fotos

1. Crie uma pasta `images/` no repositório
2. Faça upload das fotos
3. No HTML, substitua:
   ```html
   <div class="placeholder-img">
       <p>📷 Insira aqui uma foto da fazenda</p>
   </div>
   ```
   Por:
   ```html
   <img src="images/foto-fazenda.jpg" alt="Fazenda 3M" style="width: 100%; border-radius: 15px;">
   ```

### Alterar Textos

Todos os textos estão nos arquivos `.html` em português claro. Basta abrir com qualquer editor de texto (Bloco de Notas, VS Code, etc.) e editar.

### Adicionar Google Maps

1. Acesse: https://google.com/maps
2. Busque o endereço da fazenda
3. Clique em **"Compartilhar"** → **"Incorporar um mapa"**
4. Copie o código `<iframe...>`
5. Cole no arquivo `fazenda.html` no lugar indicado (procure por "Insira aqui o código embed")

---

## 🌐 Domínio Próprio (Opcional - R$ 40/ano)

Se quiser um domínio tipo `www.fazenda3m.com.br`:

1. Compre no Registro.br (https://registro.br) - cerca de R$ 40/ano
2. Configure os DNS:
   - No Registro.br, adicione 4 registros tipo **A**:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - E um **CNAME**:
     ```
     www → SEU-USUARIO.github.io
     ```
3. No GitHub, em Settings → Pages, adicione o domínio customizado
4. Aguarde 24-48h para propagar

---

## 📱 Checklist de Lançamento

Antes de divulgar o site, confira:

- [ ] Todos os textos revisados (sem erro de português)
- [ ] Telefones, e-mails e endereço corretos
- [ ] Google Forms incorporado e testado
- [ ] Planilha de currículos vinculada
- [ ] Notificação por e-mail funcionando
- [ ] Fotos adicionadas (se possível)
- [ ] Testado em celular (responsive)
- [ ] Links do WhatsApp com número correto
- [ ] Rodapé com informações atualizadas

---

## 🆘 Problemas Comuns

**Site não aparece depois de 5 minutos:**
- Verifique se GitHub Pages está ativado (Settings → Pages)
- Certifique-se que o arquivo principal se chama `index.html` (com i minúsculo)

**Formulário não carrega:**
- Verifique se copiou o código `<iframe>` completo do Google Forms
- Teste o link do Forms diretamente no navegador

**Imagens não aparecem:**
- Verifique se os caminhos estão corretos: `images/foto.jpg` (sem barra inicial)
- Certifique-se que fez upload das imagens no GitHub

**CSS/JavaScript não funciona:**
- Verifique se as pastas `css/` e `js/` foram criadas corretamente
- Certifique-se que não há espaços nos nomes dos arquivos

---

## 📞 Suporte

Dúvidas? Entre em contato comigo ou consulte:
- Documentação GitHub Pages: https://pages.github.com
- Ajuda Google Forms: https://support.google.com/forms

**Criado com ❤️ para a 3M Agropecuária**
