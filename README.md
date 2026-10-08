# 💰 Painel Financeiro Pessoal

App estático (HTML + JS) para controle financeiro pessoal: saldo real x projetado, orçamento, metas, cartões com parcelas e gastos/entradas fixos.

## Arquitetura
- **Frontend único** (`index.html`), sem build. Chart.js via CDN.
- **Persistência:** `localStorage` do navegador. Nenhum dado vai ao GitHub ou a servidores. Use *Configurações → Backup JSON*.
- **Valores em centavos** (inteiros). Formato `R$ 1.234,56`, datas `DD/MM/AAAA`.
- **Modelo (chaves do JSON):** `tx` (lançamentos), `cats`, `acc` (contas), `cards`, `inc` (entradas fixas), `fix` (gastos fixos), `bud` (orçamento), `goals`, `set`. Parcelas de cartão são `tx` com `grp` em comum.
- **Projeção:** saldo realizado + entradas pendentes/fixas não lançadas − saídas pendentes/fixas não lançadas − (média diária variável × dias restantes).
- **Limite variável:** renda prevista − fixos − parcelas/cartão pendentes − metas mensais.

## Rodar localmente
Abra `index.html` no navegador, ou `python3 -m http.server 8000`.

## Deploy (GitHub Pages)
1. Crie um repositório **privado** (Pages privado exige plano pago; como não há dados no código, público também é seguro).
2. Envie estes arquivos. Em *Settings → Pages*, escolha branch `main`, pasta `/root`.

## Segurança
Dados ficam só no seu navegador. `.env` e PDFs estão no `.gitignore`. O `.env.example` é reservado para a fase com backend.

## Roadmap (ainda NÃO implementado)
Dívidas, patrimônio com bens/passivos e evolução mensal, importação CSV, relatórios PDF/Excel, **conciliação de fatura em PDF** (planejada com pdf.js no navegador, sem upload).
