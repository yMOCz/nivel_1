# PDV com Descontos (Python) — Desafio Nível 1

## O que o código faz

O `pdv.py` simula o caixa de uma loja (PDV — Ponto de Venda) que aplica descontos progressivos. Para cada compra, ele pergunta o valor e a idade do cliente, calcula o valor final com as regras de desconto da loja e o mostra em reais. O atendimento se repete, compra após compra, até o operador digitar `0` no valor; então o programa exibe o resumo do dia: quantidade de compras, total bruto, total de descontos e total final.

## Como ele faz

O código lê o valor e a idade e, se algum for negativo (ou não for um número), mostra um aviso e pergunta de novo. Depois verifica se a idade é maior ou igual a 65 anos e, se for, aplica 20% de desconto; em seguida verifica se o valor **já descontado pela idade** é maior que R$ 100,00 e, se for, aplica mais 10% sobre esse valor. Por isso um valor de exatamente R$ 100,00 não ganha o desconto extra, e um cliente de 64 anos só pode receber o desconto por valor. O resultado é arredondado para centavos (com `Decimal`, que evita erros de ponto flutuante) e mostrado no formato `R$ 99.00`. Cada compra é guardada numa lista (`compras`) e, quando o usuário digita `0`, o laço termina e o programa percorre essa lista somando o total bruto (valores originais), o total final (valores com desconto) e a diferença entre os dois, que é o total de descontos concedidos.

## Como rodar

```bash
python pdv.py
```

(No Linux/macOS, use `python3 pdv.py`.) Digite o valor da compra e a idade do cliente; para encerrar, digite `0` no valor.

## Tabela de exemplos (casos de teste)

| # | Valor (R$) | Idade | Desconto idade | Desconto valor | Valor final esperado | Teste |
|---|------------|-------|----------------|----------------|----------------------|-------|
| 1 | 50.00 | 30 | 0% | 0% | R$ 50.00 | ✅ |
| 2 | 100.00 | 30 | 0% | 0% | R$ 100.00 | ✅ |
| 3 | 80.00 | 65 | 20% | 0% | R$ 64.00 | ✅ |
| 4 | 100.00 | 70 | 20% | 0% | R$ 80.00 | ✅ |
| 5 | 125.00 | 70 | 20% | 0% | R$ 100.00 | ✅ |
| 6 | 200.00 | 30 | 0% | 10% | R$ 180.00 | ✅ |
| 7 | 101.00 | 30 | 0% | 10% | R$ 90.90 | ✅ |
| 8 | 200.00 | 65 | 20% | 10% | R$ 144.00 | ✅ |
| 9 | 1000.00 | 80 | 20% | 10% | R$ 720.00 | ✅ |
| 10 | 200.00 | 64 | 0% | 10% | R$ 180.00 | ✅ |

Para conferir: rode o programa, digite o valor e a idade de cada linha e compare o "Valor final" mostrado com a coluna "Valor final esperado". Os 10 casos foram executados no `pdv.py` e todos conferem (✅).

## Exemplo de execução

```text
=== PDV com Descontos ===

Valor da compra em R$ (0 para encerrar): 200
Idade do cliente: 70
Descontos aplicados: idade (20%) + valor (10%)
Valor final: R$ 144.00

Valor da compra em R$ (0 para encerrar): 80
Idade do cliente: 70
Descontos aplicados: idade (20%)
Valor final: R$ 64.00

Valor da compra em R$ (0 para encerrar): 50
Idade do cliente: 30
Descontos aplicados: nenhum
Valor final: R$ 50.00

Valor da compra em R$ (0 para encerrar): 0

==================================
           RESUMO DO DIA
==================================
Compras registradas: 3
Total bruto:         R$ 330.00
Total de descontos:  R$ 72.00
Total final:         R$ 258.00
```
