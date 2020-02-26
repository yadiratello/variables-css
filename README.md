# Variables CSS (1) (Custom Properties) 

Son propiedades que tienen:
* Herencia (sus hijos heredan esos valores).
* Cascada (se puede sobreescribir ese valor)

## Variable 
Espacio en memoria que almacena un valor. Ese valor puede ser recuperado

* Una variable en css se declara asi:
```css
etiqueta{
	--nombreVariable;
}
```
- Para asignar un valor a esa variable:
```css
--nombreVariable : valor;
```

- Para utilizar esa variable utilizamos la funcion:
```js
var(--nombreVariable)
```
- Una variable puede ser local o global
- Para que una variable sea global debo de declararlo en el elemento mas alto del DOM

* La pseudoclase :root tiene una especificidad mayor a que las estiquetas

ejm:
```css
:root{
	--color : purple;
	--link-color : green;
	--bg-color : yellow;
}
```

 **Las variables CSS son:**

- Case sensitive
- Son muy permisivas al momento de asignarle un valor

ejm:
```css
:root{
	--box-shadow : 2px 2px 5px #000;
}

h1{
	box-shadow: var(--box-shadow);
}
```
* Hacer fallback para navegadores antiguos

ejm:
```css
h1{
	background : yellow;
	background: var(--bg-color); //si el navegador no soporta variables CSS se saltará esta linea
}
```

# VARIABLES CSS (2) - SCOPE

El scope es el ambito en el que una variable existe y desde la cual puede ser recuperado su valor.

* Las variables CSS tienen scope de DOM
* Las variables css que se declaran en la pseudoclase :root se pueden acceder desde archivos externos

## DIFERENCIAS ENTRE VARIABLES SASS Y VARIABLES CSS

#### SASS:

1. se pueden declarar sin selector
2. tiene scope de bloque
3. operaciones aritmeticas directas
4. funciones para los colores
5. las variables pueden ser interpoladas
6. No se pueden redefinir
7. No existen despues de la compilacion

#### CSS :

1. necesitan un selector
2. tiene scope de DOM
3. Operaciones aritmeticas con calc
4. no tienen funciones para los colores
5. las variables NO pueden ser interpoladas
6. Se pueden redefinir
7. existen en el DOM

```css
$color : green;
$size: 3rem;

:root{
	--size:3rem;
}
```

## CSSOM

getComputedStyle(element): devuelve un objeto con todas las propiedades css que el navegador calculo 

```js
getComputedStyle($0).color
```
* Para recuperar el valor de una variable css usamos la funcion:  .getPropertyValue(nombrevariable):
```js
getComputedStyle(element).getPropertyValue(--nombre-variable)
```
*Para setear(asignar un nevo valor) una variable css usamos: setPropertyValue(--variable)
```js
element.style.setPropertyValue(--variable);
```