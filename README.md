# Comparação entre XmlHttpRequest, Fetch, Promises e Async/Await

Este repositório contém uma pesquisa comparativa entre diferentes formas de realizar requisições assíncronas em JavaScript: `XmlHttpRequest`, `fetch`, `Promise` e `async/await`.

Também estão disponíveis implementações do exercício `ajax3.html` utilizando as três abordagens modernas (`fetch`, `Promise`, `async/await`).

---

## 🔍 Pesquisa Comparativa

### 1. XmlHttpRequest

**Vantagens:**
- Compatível com todos os navegadores desde versões antigas.
- Permite mais controle sobre o request (ex: progresso, status).

**Desvantagens:**
- Verboso e difícil de ler/manter.
- Não trabalha nativamente com Promises.

### 2. Fetch API

**Vantagens:**
- Sintaxe moderna e limpa.
- Retorna uma Promise, facilitando o uso com `.then()` ou `async/await`.

**Desvantagens:**
- Menor suporte a versões antigas do IE.
- Não rejeita por padrão em erros HTTP (como 404), é necessário checar manualmente `response.ok`.

### 3. Promises

**Vantagens:**
- Facilitam o controle de código assíncrono.
- Permitem encadeamento de ações com `.then()`.

**Desvantagens:**
- A sintaxe pode ficar difícil de ler com muitos encadeamentos.

### 4. Async/Await

**Vantagens:**
- Torna o código assíncrono mais legível, parecido com código síncrono.
- Ideal para fluxos com múltiplas chamadas assíncronas em sequência.

**Desvantagens:**
- Requer tratamento de erros com `try/catch`.

---

## 💻 Implementações

### ✅ ajax3-fetch.html

```html
<!DOCTYPE html>
<html>
<head><title>Fetch API</title></head>
<body>
  <button onclick="carregar()">Carregar Dados</button>
  <div id="conteudo"></div>

  <script>
    function carregar() {
      fetch("dados.txt")
        .then(response => response.text())
        .then(data => {
          document.getElementById("conteudo").innerText = data;
        })
        .catch(error => console.error("Erro ao carregar:", error));
    }
  </script>
</body>
</html>
