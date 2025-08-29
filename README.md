# Criando-um-Sistema-Banc-rio-com-Python
Sistema Bancário

menu = """

========== CAIXA ELETRÔNICO ==========

[1] Depositar
[2] Sacarr
[3] Extrato
[4] Sair

=> """

Saldo = 0
Limite = 500
Extrato = ""
Numero_Saques = 0
LIMITE_SAQUES = 3 

while True:

    opcao = input(menu)
    
    if opcao == "1":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            Saldo += valor
            Extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "2":
        valor = float(input("Informe o valor do saque: "))     

        excedeu_saldo = valor > Saldo

        excedeu_limite = valor > Limite
        
        excedeu_saques = Numero_Saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.") 

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            Saldo -= valor
            Extrato += f"Saque: R$ {valor:.2f}\n"    
            Numero_Saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")   

    elif opcao == "3":
        print("\n========== EXTRATO ==========")
        print("Não foram realizados movimentações. " if not Extrato else Extrato)
        print(f"\nSaldo: R$ {Saldo:.2f}")
        print("===============================")
        
    elif opcao == "4":
        break

    else:
        print("Operação inválida, por favor selecionar novamente a operação desejada.")
        

