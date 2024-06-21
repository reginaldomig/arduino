# Projeto de Circulação de ar

## Esse projeto é tal


```c++

// definindo as variáveis e pinos do arduino
const int trigPin = 3;      // Pino de disparo do sensor ultrassônico
const int echoPin = 2;      // Pino de eco do sensor ultrassônico
const int ledVerde = 13;    // Led verde
const int ledAmarelo = 8;   // Led amarelo
const int ledVermelho = 9;  // Led vermelho
const int motor = 12;   // Motor eletroventilador

void setup() {
  pinMode(trigPin, OUTPUT);  // Define o pino de disparo como saída
  pinMode(echoPin, INPUT);   // Define o pino de eco como entrada
  pinMode(ledVerde,OUTPUT);     // Define o pino do LED verde como saída
  pinMode(ledAmarelo,OUTPUT);     // Define o pino do LED amarelo como saída
  pinMode(ledVermelho,OUTPUT);     // Define o pino do LED vermelho como saída
  pinMode(motor,OUTPUT);    // Define o pino do motor eletroventilador como saída

}

void loop() {

  long duration, distanceCM;

  // Envia um pulso de disparo de 10 microssegundos
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Mede o tempo de duração do pulso de eco
  duration = pulseIn(echoPin, HIGH);

  // Calcula a distância em centímetros
  distanceCM = duration * 0.034 / 2;

  
  if (distanceCM < 100) {
    ligaLedVerde();
  } else if (distanceCM < 200){
    ligaLedAmarelo();
  } else if (distanceCM < 300){
    ligaLedVermelho();
  } else {
    desligaLeds();
  }
  
  delay(1000);  // Atraso de 1000 ms antes da próxima leitura
}


void ligaLedVerde(){
  digitalWrite(motor, HIGH);  // Aciona o motor
  digitalWrite(ledVerde, HIGH);  // Liga o LED verde
  digitalWrite(ledAmarelo, LOW);  //desliga o led amarelo
  digitalWrite(ledVermelho, LOW);  //desliga o led vermelho
  
}


void ligaLedAmarelo(){
  digitalWrite(motor, HIGH);  // Aciona o motor
  digitalWrite(ledVerde, LOW);  // Liga o LED verde
  digitalWrite(ledAmarelo, HIGH);  //desliga o led amarelo
  digitalWrite(ledVermelho, LOW);  //desliga o led vermelho
}


void ligaLedVermelho(){
  digitalWrite(motor, HIGH);  // Aciona o motor
  digitalWrite(ledVerde, LOW);  // Liga o LED verde
  digitalWrite(ledAmarelo, LOW);  //desliga o led amarelo
  digitalWrite(ledVermelho, HIGH);  //desliga o led vermelho

}

void desligaLeds(){
  digitalWrite(motor, LOW);  // Aciona o motor
  delay(500);
  digitalWrite(ledVerde, LOW);  // Liga o LED verde
  delay(500);
  digitalWrite(ledAmarelo, LOW);  //desliga o led amarelo
  delay(500);
  digitalWrite(ledVermelho, LOW);  //desliga o led vermelho

}






```
