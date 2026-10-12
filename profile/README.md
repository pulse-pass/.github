# PulsePass

Plataforma de venda de ingressos para eventos, desenvolvida como trabalho final da disciplina de
Construção de Software. Organizadores cadastram eventos com setores numerados ou de capacidade
livre, compradores escolhem os assentos e pagam por PIX, e o ingresso chega por e-mail em PDF.

A plataforma é dividida em microsserviços, cada um em um repositório desta organização:

| Repositório | Papel |
|---|---|
| `client-app` | Aplicação web do comprador (vitrine, compra e ingressos) |
| `backoffice-app` | Aplicação web de organizadores e administradores |
| `client-gateway` | Entrada única das requisições do `client-app` |
| `backoffice-gateway` | Entrada única das requisições do `backoffice-app` |
| `onboarding-service` | Cadastro de pessoas e empresas, equipe e convites, login e logout |
| `organization-service` | Situação e aprovação das organizações, subconta de pagamento e extrato do saldo |
| `event-service` | Eventos, setores, lotes e assentos, vitrine e reserva do estoque |
| `purchase-order-service` | Checkout, pedidos, cobrança PIX e geração dos ingressos |
| `webhook-service` | Recebimento dos avisos de pagamento do Asaas |
| `notification-service` | Envio dos e-mails da plataforma |
| `papaleguas-service` | Disparo das tarefas agendadas nos serviços responsáveis |

A infraestrutura compartilhada (MySQL, Redis, Kafka, Keycloak, Mailpit e MinIO) fica em um
repositório próprio. Os repositórios são criados à medida que cada aplicação é desenvolvida.

Toda mudança chega à `main` por pull request, a partir de uma branch `feature/<ID>-<slug>` que
referencia a subtarefa do backlog.
