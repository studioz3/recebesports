# Receba Digital

Site institucional e plataforma de eventos esportivos da **RecebeSports / Receba Digital** — protótipo estático em HTML/CSS/JS publicado via GitHub Pages.

## Estrutura do projeto

```
Receba-Digital/
├── *.html                  ← Páginas públicas e internas (38 telas)
├── css/                    ← Folhas de estilo
├── js/                     ← Scripts
├── assets/                 ← Imagens, ícones e logos (JPG/PNG/SVG)
└── README.md
```

### HTMLs principais

| Categoria | Arquivos |
|---|---|
| Home / institucional | `index.html`, `quem-somos.html`, `organizadores.html` |
| Eventos públicos | `detalhe-evento.html`, `resultados.html`, `resultado-evento.html` |
| Login / cadastro | `login.html`, `login-organizador.html`, `cadastro-1/2/3.html` |
| Inscrição (fluxo) | `inscricao-1/2/3.html`, `inscricao-pagamento.html`, `inscricao-concluido.html`, `inscricao-detalhes.html`, `inscricao-participante.html` |
| Ficha de saúde | `ficha-saude-1/2/3/4/5/6.html` |
| Perfil do atleta | `perfil-meus-dados.html`, `perfil-meus-amigos.html`, `perfil-saude.html`, `perfil-privacidade.html`, `perfil-alterar-senha.html` |
| Criar organizador | `organizador-criar-1/2/3/4.html` |
| **Painel do organizador** | `painel-organizador.html` |
| Protótipo | `recebesports-prototipo.html` |

### CSS por escopo

| Arquivo | Uso |
|---|---|
| `global.css` | Reset, tipografia, header/footer — carregado em todos os HTMLs |
| `plataforma.css` | Estilo do fluxo logado (inscrição, perfil, ficha saúde) |
| `painel.css` | **Painel do organizador** (dashboard interno) |
| `home.css` | Home institucional |
| `inscricao.css` | Fluxo de inscrição |
| `cadastro.css` | Telas de cadastro |
| `organizador.css` | Telas do organizador (criação) |
| `organizadores.css` | Página pública de organizadores |
| `detalhe-evento.css` | Página de detalhe do evento |
| `resultados.css` | Resultados de eventos |
| `login.css`, `login-organizador.css` | Telas de login |
| `quem-somos.css` | Página "Quem Somos" |

### JS

| Arquivo | Uso |
|---|---|
| `global.js` | Comportamentos globais (menu, scrolling) |
| `painel.js` | Aplicação do painel do organizador (router, views, gráficos SVG) |
| `organizador-criar-2.js` | Validações específicas do passo 2 da criação de organizador |

## Sobre o Painel do Organizador

O `painel-organizador.html` é uma SPA estática que renderiza várias views internas via roteador em hash (`#estatisticas`, `#financeiro`, `#inscricoes`, etc).

### Recursos
- **Tipografia:** Montserrat (Google Fonts)
- **Gráficos SVG** desenhados à mão (sem libs externas): linha/área, donut, sparkline, gauge semi-circular
- **Roteador interno** com hash navigation
- **Sidebar colapsável** + responsivo mobile com scrim
- **Menu de usuário** com opções "Voltar ao Site" e "Sair do Sistema"

### Views disponíveis
- `#estatisticas` — KPIs gerais, gauge de ocupação, breakdown por distância/categoria/método de pagamento, top cidades/equipes
- `#financeiro` — KPIs financeiros, painéis por método de pagamento (Boletos/PIX/Cartão/Adiantamentos), saldo disponível, gráfico diário, donut por método, tabelas de adiantamentos e serviços
- `#inscricoes` — Tabela de inscrições com filtros
- `#cupons` — Cupons de desconto
- `#eventos` — Gestão de eventos
- `#contratos` — Meus contratos
- `#organizador` — Cadastro do organizador
- `#usuarios` — Gerenciamento de usuários
- `#rel-*` — Relatórios diversos (cronometragem, inscrições, base completa…)

## Histórico de limpeza

Esta versão consolidou a estrutura, removendo arquivos duplicados e órfãos que causavam confusão sobre qual versão estava em produção:

### Removidos
- `assets/painel.css` (versão antiga — havia uma cópia mais nova em `css/painel.css` que não estava sendo carregada)
- `assets/painel.js` (mesma situação)
- `inscricao.css` (raiz, versão antiga — o ativo é `css/inscricao.css`)
- `resultados.css` (raiz, versão antiga — o ativo é `css/resultados.css`)
- `organizador-login.html` (versão antiga e diferente de `login-organizador.html`)

### Ajustado
- `painel-organizador.html` agora carrega `css/painel.css` e `js/painel.js` (antes apontava para `assets/`, motivo de commits do painel não surtirem efeito).

### Candidatos a revisão (mantidos por enquanto)
Os arquivos abaixo não têm referência em nenhum HTML. Avaliar se devem ser removidos:
- `css/legal.css`
- `css/organizador-criar.css`
- `js/cadastro.js`
- `recebesports-prototipo.html` (protótipo grande, possivelmente já obsoleto)

## Como rodar localmente

É site estático — basta abrir os HTMLs no navegador, ou servir a pasta via qualquer servidor estático:

```bash
# Python 3
python3 -m http.server 8080
# ou Node
npx serve .
```

E acessar `http://localhost:8080/index.html`.

## Publicação

O site está publicado via **GitHub Pages** a partir da branch `main`.
