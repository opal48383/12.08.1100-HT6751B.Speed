# 12.08.1100-HT6751B.Speed
int a = -1;
boolean SW = true; 
void setup() {
Serial.begin(9600);
pinMode(2,OUTPUT);//IN3
pinMode(5,OUTPUT);//IN1
pinMode(6,OUTPUT);//IN2
pinMode(4,INPUT);//button
pinMode(8,OUTPUT);//6
pinMode(9,OUTPUT);//5
pinMode(10,OUTPUT);//4
pinMode(11,OUTPUT);//3
pinMode(12,OUTPUT);//2
pinMode(13,OUTPUT);//1
pinMode(3,INPUT);//SW
}

void loop() {
  if (digitalRead(3) == 0)
  {
  Serial.print("Button: ");
  Serial.println(digitalRead(3));
   while(digitalRead(3) == 0);
    if (SW == true)
    {
      SW = false;
      a=-1;
      digitalWrite(13,HIGH);
      digitalWrite(12,HIGH);
      digitalWrite(11,HIGH);
      digitalWrite(10,HIGH);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    }
    else
    {
     SW = true ; 
     a = 0; 
    }
    Serial.print("SW: ");
    Serial.println(SW);
    delay(250);
  }
   if (digitalRead(4) == 0)
  { while(digitalRead(4) == 0); 
  if( SW == true ){ a = (a+1)%6; 
    delay(250);
    Serial.print("Speed: ");
    Serial.println(a);}
  }
  switch(a){
    case 0:
      Speed(110);
      digitalWrite(13,LOW);
      digitalWrite(12,HIGH);
      digitalWrite(11,HIGH);
      digitalWrite(10,HIGH);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    break;
    case 1:
      Speed(139);
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,HIGH);
      digitalWrite(10,HIGH);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    break;
    case 2:
      Speed(168);
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,HIGH);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    break;
    case 3:
      Speed(197);
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,LOW);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    break;
    case 4:
      Speed(226);
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,LOW);
      digitalWrite(9,LOW);
      digitalWrite(8,HIGH);
    break;
    case 5:
      Speed(255);
      digitalWrite(13,LOW);
      digitalWrite(12,LOW);
      digitalWrite(11,LOW);
      digitalWrite(10,LOW);
      digitalWrite(9,LOW);
      digitalWrite(8,LOW);
    break;
        case -1:
      Speed(0);
      digitalWrite(13,HIGH);
      digitalWrite(12,HIGH);
      digitalWrite(11,HIGH);
      digitalWrite(10,HIGH);
      digitalWrite(9,HIGH);
      digitalWrite(8,HIGH);
    break;
  }
  
}

void Speed(int S) {
    analogWrite (5,S);
    analogWrite (6,0);
  }
