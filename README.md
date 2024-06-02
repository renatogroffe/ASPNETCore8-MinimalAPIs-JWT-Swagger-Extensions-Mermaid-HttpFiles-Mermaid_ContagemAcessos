# ASPNETCore8-MinimalAPIs-JWT-Swagger-Extensions-Mermaid-HttpFiles-Mermaid_ContagemAcessos
Exemplo de API REST para contagem de acessos criada com o .NET 8 + ASP.NET Core + Minimal APIs, empregando extensões definidas em uma Class Library para utilização de JWT (JSON Web Tokens) e de configurações para que o Swagger suporte tokens. Inclui arquivos .http para testes a partir do Visual Studio Code.

---

## Fluxo básico

```mermaid
sequenceDiagram
    actor Aplicacao cliente
    participant Login endpoint
    participant Contador endpoint
    Aplicacao cliente->>Login endpoint: POST /login
    Note over Aplicacao cliente,Login endpoint: Informar os atributos<br/>userID e password no JSON
    alt credenciais validas
        Login endpoint-->>Aplicacao cliente: 200 OK com Token JWT retornado
    else credenciais invalidas
        Login endpoint-->>Aplicacao cliente: 401 Unauthorized
    end
    Aplicacao cliente->>Contador endpoint: GET /contador
    Note over Aplicacao cliente,Contador endpoint: Token jwt informado como 'Bearer Token' no header Authorization
    alt Token JWT valido
        Contador endpoint-->>Aplicacao cliente: 200 OK com resultado da contagem
    else Token JWT invalido ou faltando
        Contador endpoint-->>Aplicacao cliente: 401 Unauthorized
    end
```