# Clase: Condicionales

1. Crear un nuevo programa:

[Crear un programa en Khan Academy](https://es.khanacademy.org/computer-programming/new/pjs)

2. Copia el siguiente código, vamos a mover un objeto en el plano:

```javascript
var x = 20;
var velocidad = 3;

draw = function() {
  background(202, 255, 97);

  fill(66, 66, 66);
  ellipse(x, 200, 50, 50);

  // mover la pelota
  x = x + velocidad;
};
```

La pelota rebota cuando llega al borde derecho?

4. condicional: IF

```javascript
var hizo_la_tarea = true

if (hizo_la_tarea) {
  println("jugar con amigos");
}
```

3. condicionales con operadores:

```javascript
var ultimo_num_placa = 3;

if (ultimo_num_placa == 7) {
  println("ir a cine en carro");
}
```

Ejercicio: crear varios condicionales con cada uno de los operadores `==`, `!=`, `>`, `<`, `>=` o `<=`

4. Cómo podemos hacer rebotar la pelota en el lado derecho:

```javascript
var x = 20;
var velocidad = 3;

draw = function() {
   background(202, 255, 97);

   fill(66, 66, 66);
   ellipse(x, 200, 50, 50);
    x = x + velocidad;

   if (x > 400) {
      velocidad = -3;
   }
};
```

Ejercicio: Hacer rebotar la pelota en el lado izquierdo.

5. Condicionales anidades.

```javascript
var num_placa = 3;
var hizo_la_tarea = false;

if (num_placa == 7 || num_placa == 9) {
  println("ir a cine en carro");
}

if (hizo_la_tarea && tendio_la_cama) {
  println("comprar helado");
}
```

Ejercicio: cambiar los valores de las variables para probar la tabla de verdad

6. Else

```javascript
var lado_moneda = "sello";

if (lado_moneda == "cara") {
  println("escoges la cancha");
} else {
  println("la escogemos nosotros");
}
```

7. Juego de rebotar la pelota

```javascript
noStroke();
background(0,0,0);

var bolaX = random(0, 400);
var bolaY = 0;
var bolaDireccionX = 4;
var bolaDireccionY = 4;

var fin = false;

var calcularDireccion = function(x, direccionActual) {
  if((direccionActual > 0 && x >= 400) || (direccionActual < 0 && x <= 0)) {
    return -direccionActual;
  }

  return direccionActual;
};

var calcularDireccionBolaX = function(x, y, direccionActual) {
  if(y >= 385 && y <= 390 && x > mouseX && x < mouseX + 40) {
    if(x < mouseX + 10) {
        return -4;
    }
    if(x < mouseX + 20) {
        return -2;
    }
    if(x < mouseX + 30) {
        return 2;
    }
    return 4;
  }

  if((direccionActual > 0 && x >= 400) || (direccionActual < 0 && x <= 0)) {
    return -direccionActual;
  }

  return direccionActual;
};

var calcularDireccionBolaY = function(x, y, direccionActual) {
  if(direccionActual > 0) {
    if(y >= 385 && y <= 390 && x > mouseX && x < mouseX + 40) {
      return -4;
    }
  }

  if(direccionActual < 0 && y <= 0) {
    return 4;
  }

  return direccionActual;
};

draw = function() {
  // Es el fin del juego?
  if(fin){
    fill(255, 255, 255);
    textSize(30);
    text("Perdiste!", 140, 200);
    return;
  }

  background(0,0,0);

  // Dibujar barra de abajo
  rect(mouseX, 390, 40, 5);
  fill(255, 255, 255);
  // Dibujar bola
  ellipse(bolaX, bolaY, 10, 10);

  bolaDireccionX = calcularDireccionBolaX(bolaX, bolaY, bolaDireccionX);
  bolaDireccionY = calcularDireccionBolaY(bolaX, bolaY, bolaDireccionY);

  bolaX += bolaDireccionX;
  bolaY += bolaDireccionY;

  if(bolaY > 400) {
    fin = true;
  }
};
```
