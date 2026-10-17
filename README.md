# Inverno D’Italia — Caffè & Pasticceria

Site responsivo baseado nos layouts enviados, com vídeo de fundo local, cardápio pesquisável, filtros, sacola persistente neste navegador, cupom e checkout demonstrativo.

## Desenvolvimento

Requer Node.js 20.19+ ou 22.12+ (validado com Node 24).

```sh
cd /workspace/Cafeteria
npm ci --cache /workspace/.npm
npm run dev -- --port 5173
```

```sh
npm run build
npm run preview -- --port 4173
npm test
```

Os testes usam o Chromium em `/usr/bin/chromium`. Em outra máquina, ajuste `playwright.config.js` para o navegador instalado ou remova `executablePath` e instale o Chromium do Playwright com `npx playwright install chromium`.

## Pagamentos simulados

Pix e cartão são exclusivamente demonstrativos, conforme solicitado. O cartão fictício é apresentado automaticamente; não há campos de número de cartão ou CVV. Não há backend, gateway, QR Code real, cobrança ou envio de pedido à cafeteria. Nome, e-mail, endereço e observações ficam apenas no formulário em memória. A sacola guarda somente IDs de produtos e quantidades no localStorage.

Cupom: `PRIMEIRAPAUSA`, com 5% de desconto nos produtos. Retirada gratuita; taxa de entrega simulada de R$ 6,00. Produtos, preços, endereço e horários foram extraídos/adaptados do material de referência e precisam ser confirmados com o proprietário antes da publicação comercial.

## Arquivos

- `src/main.js`: produtos, sacola, filtros e checkout.
- `src/style.css`: layout e adaptações para celular.
- `public/assets/cafe.mp4`: vídeo fornecido, reproduzido sem som e em loop. Há controle para pausar e respeito a movimento reduzido.
- `public/assets/poster.jpg`: quadro extraído do vídeo, exibido antes da reprodução.
- `public/assets/*.webp`: fotografias ilustrativas geradas para os seis produtos e para a seção da casa. Cada imagem é um arquivo local independente, com enquadramento responsivo; não depende de serviços externos. São imagens ilustrativas, não fotografias reais dos produtos ou do estabelecimento.

Fontes do Google são opcionais; fontes de sistema servem como fallback. Os documentos do ZIP foram utilizados como referência visual, sem executar scripts anexados.

Para receber pagamentos reais, uma tarefa futura deverá integrar o provedor escolhido pelo proprietário, com criação de cobranças no servidor, confirmação por webhook e armazenamento de pedidos. Não colocar credenciais no frontend.
