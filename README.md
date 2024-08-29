menu = """

[d] depósito
[s] saque
[e] extrato
[q] sair
"""

saldo = 0
limite = 500
extrato = ""
numero_saques = 1
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "d":
            valor = float(input("Informe o valor a ser depositado: "))
            if valor > 0:
                saldo += valor
                print(f"Depositado R${valor}. Seu saldo atual é {saldo}.")
                extrato += f"Depósito: R$ {valor: .2f}\n"

            else: 
                print("Valor inválido, tente novamente.")


    elif opcao == "s":
        valor = float(input(f"O seu saldo é de {saldo}. Informe o valor para saque: "))
        excedeu_limite = valor > limite
        excedeu_saldo = valor > saldo
        excedeu_saques = numero_saques > LIMITE_SAQUES
        if saldo == 0:
            print("Sem saldo.") 
        elif excedeu_limite:
            print("Excedeu limite diário, tente novamente.")
        elif excedeu_saldo:
            print("Excedeu saldo, tente novamente.")
        elif excedeu_saques:
            print(f"Excedeu limite de saques, tente novamente.")     
        elif valor > 0:
            saldo -= valor
            print(f"Foi sacado {valor}. Seu novo saldo é de {saldo}.")
            numero_saques += 1
            extrato += f"Saque: {valor:.2f}\n"
                
        else: 
            print("Valor inválido, tente novamente.")
       
    elif opcao == "e":
        if not extrato:
            print("Não houveram transações registradas.")
        else:
            print(extrato)
            print(f"Seu saldo é de R${saldo}.")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, tente novamente.")
