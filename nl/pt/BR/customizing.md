---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Customizando
{: #customizing}

Com o [{{site.data.keyword.knowledgestudiofull}}
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/watsonknowledgestudio), é possível
estender o {{site.data.keyword.nlushort}} com modelos customizados que identificam entidades customizadas e relações
exclusivas para o seu domínio.
{: shortdesc}

## Introdução aos modelos customizados
{: #getting-started-with-custom-models}

> O plano Grátis do {{site.data.keyword.nlushort}} limita o tamanho e o desempenho de seu modelo
customizado. Para testar um modelo customizado para sua extensão integral, você precisará usá-lo com o
plano Standard do {{site.data.keyword.nlushort}}.

1. Se você ainda não tiver feito isso,
veja a [introdução](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) ao
{{site.data.keyword.nlushort}}.
2. [ Introdução ao  {{site.data.keyword.knowledgestudioshort}} ](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. [ Crie um modelo de aprendizado de máquina com o  {{site.data.keyword.knowledgestudioshort}} ](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutml_intro).
4. [Implemente o seu modelo para o {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. Para usar seu modelo, especifique o `modelo` que você implementou nas opções de
[entidades
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window}
ou [relações
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window}
da sua solicitação de API:
    - Arquivo *parameters.json* de exemplo:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}

    - Solicitação curl de exemplo:

        ```bash
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-09-21" \ --request POST \ --header "Content-Type: application/json" \ --data @parameters.json
        ```
        {: pre}

## Excluindo um modelo customizado
{: #deleting-a-custom-model}

O número de modelos customizados que você implementa no {{site.data.keyword.nlushort}} afeta a sua conta do {{site.data.keyword.nlushort}} de acordo com o seu [plano de precificação](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). Para evitar encargos para um modelo que você não usa mais, [remova a implementação do modelo com o {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model) ou com o método **[Excluir modelo](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**.

Solicitação curl de exemplo:

```bash
curl --user "apikey":"{apikey}" \
"{url } /v1/models/ {2}{0}{1}{8}-10-30 " \ -- request DELETE
```
{: pre}


## Suporte ao idioma para modelos customizados
{: #language-support-for-custom-models}

Verifique as colunas *Suporte ao modelo customizado* nas tabelas da página [Suporte ao idioma](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) para ver os modelos customizados que são suportados para cada idioma.

### Sentimento de destino para entidades de modelo customizado
{: #targeted-sentiment-for-custom-entities}

Somente para inglês, é possível obter pontuações de impressão para cada entidade de modelo customizado detectada pelo serviço configurando a opção `sentiment:true` no objeto de entidades. Nenhum outro idioma suporta impressão de destino para entidades de modelo customizado.
