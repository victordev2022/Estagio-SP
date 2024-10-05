1) Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);
Ao final do processamento, qual será o valor da variável SOMA?
 a soma sera 91




exercicio 2 

def fibonacci_sequence(n):
    # Iniciando a sequência de Fibonacci
    fib_sequence = [0, 1]
    
    # Gerando a sequência até o número informado
    while True:
        next_fib = fib_sequence[-1] + fib_sequence[-2]
        if next_fib > n:
            break
        fib_sequence.append(next_fib)
    
    return fib_sequence

def verifica_fibonacci(num):
    # Calcula a sequência de Fibonacci
    fib_sequence = fibonacci_sequence(num)
    
    # Verifica se o número está na sequência
    if num in fib_sequence:
        return f"O número {num} pertence à sequência de Fibonacci."
    else:
        return f"O número {num} não pertence à sequência de Fibonacci."

# Entrada do usuário
numero = int(input("Informe um número: "))
resultado = verifica_fibonacci(numero)
print(resultado)

exercicio 3 

import json

def calcular_faturamento(dados):
    faturamento = dados["faturamento"]

    # Ignorando os dias sem faturamento (valor 0)
    faturamento_validos = [valor for valor in faturamento if valor > 0]

    if not faturamento_validos:
        return "Não há faturamento válido para calcular."

    menor_faturamento = min(faturamento_validos)
    maior_faturamento = max(faturamento_validos)
    media_faturamento = sum(faturamento_validos) / len(faturamento_validos)

    # Contando dias em que o faturamento foi superior à média mensal
    dias_acima_media = sum(1 for valor in faturamento_validos if valor > media_faturamento)

    return {
        "menor_faturamento": menor_faturamento,
        "maior_faturamento": maior_faturamento,
        "dias_acima_media": dias_acima_media,
        "media_faturamento": media_faturamento
    }

# Lendo os dados de um arquivo JSON
def main():
    # Supondo que o arquivo JSON está no mesmo diretório
    with open('faturamento.json', 'r') as arquivo:
        dados = json.load(arquivo)

    resultado = calcular_faturamento(dados)

    # Imprimindo os resultados
    print(f"Menor faturamento: {resultado['menor_faturamento']}")
    print(f"Maior faturamento: {resultado['maior_faturamento']}")
    print(f"Dias com faturamento acima da média: {resultado['dias_acima_media']}")
    print(f"Média de faturamento: {resultado['media_faturamento']}")

if __name__ == "__main__":
    main()


exercicio 4

# Dados de faturamento por estado
faturamento = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53
}

def calcular_percentuais(faturamento):
    # Calcula o faturamento total
    total_faturamento = sum(faturamento.values())
    
    # Calcula o percentual de cada estado
    percentuais = {estado: (valor / total_faturamento) * 100 for estado, valor in faturamento.items()}
    
    return total_faturamento, percentuais

def main():
    total, percentuais = calcular_percentuais(faturamento)
    
    print(f"Faturamento total: R${total:.2f}")
    print("Percentual de representação por estado:")
    for estado, percentual in percentuais.items():
        print(f"{estado}: {percentual:.2f}%")

if __name__ == "__main__":
    main()

exercicio 5

def inverter_string(s):
    # Inicializa uma nova string vazia
    string_invertida = ""
    
    # Itera sobre a string original do final para o início
    for i in range(len(s) - 1, -1, -1):
        string_invertida += s[i]  # Concatena o caractere à nova string
    
    return string_invertida

def main():
    # Entrada do usuário
    entrada = input("Informe uma string para inverter (ou pressione Enter para usar a string padrão): ")
    
    if entrada == "":
        entrada = "Exemplo de string padrão"
    
    resultado = inverter_string(entrada)
    
    print(f"String original: {entrada}")
    print(f"String invertida: {resultado}")

if __name__ == "__main__":
    main()
