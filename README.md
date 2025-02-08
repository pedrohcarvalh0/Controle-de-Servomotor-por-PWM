# Controle de Servomotor com PWM no Raspberry Pi Pico W

Este projeto demonstra como controlar um servomotor utilizando PWM no Raspberry Pi Pico W. O código configura a GPIO 22 para gerar um sinal PWM com frequência de 50Hz (período de 20ms) e posiciona o servo em ângulos específicos utilizando diferentes larguras de pulso.

## Funcionalidades

- **Configuração do PWM:**  
  A GPIO 22 é configurada para operar em modo PWM com um clock ajustado para gerar uma frequência de 50Hz. Isso é feito ajustando o divisor de clock e o valor de wrap do contador PWM.

- **Posicionamento do Servomotor:**  
  O servo é posicionado em três ângulos fixos:
  - **180°:** Pulso de 2400µs, com espera de 5 segundos.
  - **90°:** Pulso de 1470µs, com espera de 5 segundos.
  - **0°:** Pulso de 500µs, com espera de 5 segundos.

- **Movimentação Suave:**  
  Após os posicionamentos fixos, o código realiza uma varredura suave do servo entre 0° e 180°. Essa transição é feita aumentando e diminuindo gradualmente a largura do pulso em incrementos de 5µs, com um atraso de 10ms entre cada ajuste, garantindo uma movimentação fluida.

## Estrutura do Código

- **setup_pwm(uint gpio):**  
  Configura a GPIO selecionada para funcionar com PWM. Define o divisor de clock para 64, o que, a partir de uma frequência base de 125MHz, resulta em aproximadamente 1.953125MHz. Em seguida, calcula o valor de wrap (39062) para obter o período de 20ms.

- **set_servo_pulse(uint gpio, uint16_t pulse_width_us):**  
  Recebe a largura do pulso desejada em microssegundos e a converte para um valor proporcional ao contador PWM (baseado no wrap de 39062). Essa função é utilizada para ajustar a posição do servo.

- **main():**  
  Inicializa o sistema e o PWM, posiciona o servomotor em 180°, 90° e 0° graus (cada posição com uma espera de 5 segundos) e, em seguida, realiza uma movimentação suave entre os ângulos de 0° e 180°.

## 🚀 Compilação e Upload

```plaintext
1. Clone o repositório do código:
   git clone <URL_DO_REPOSITORIO>

2. Compile o programa usando CMake:
   mkdir build
   cd build
   cmake ..
   make

   Também é possível compilar diretamente na  extensão do Raspberry Pi Pico Project no VS Code clicando em "Compile Project"

3. Envie o arquivo `.uf2` gerado para o Raspberry Pi Pico:
   - Mantenha o botão `BOOTSEL` pressionado enquanto conecta o Pico ao computador.
   - Através da extensão do Raspberry Pi Pico Project no VS Code, é possível enviar o código para a placa clicando em "Run Project (USB)".
   - Caso não consiga enviar diretamente, copie o arquivo `.uf2` gerado para a unidade montada.

4. Caso não tenha a placa, é possível simular o sistema:
   - Compile o código.
   - Clique no arquivo `diagram.json` e inicie a simulação.
```

## 🎥 Explicação e Demonstração

```plaintext
https://youtu.be/YhFtb5burWQ
```

---
