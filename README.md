# opencart-testing
Pruebas Funcionales Unitarias del Sistema OpenCart usando PHPUnit para el Curso de Técnicas de Pruebas de Software.


## Estructura del Repositorio

* El directorio `dev` contiene el proyecto de OpenCart en su versión en desarrollo, dentro de este directorio se mantiene el codigo fuente que esta en desarrollo y tambien esta contenida la suite de pruebas funcionales unitarias usando PHPUnit.

* El directorio `prod` contiene el proyecto de OpenCart en su versión en producción, dentro de este directorio se mantiene el codigo fuente que pasa las pruebas funcionales unitarias usando PHPUnit.


## Instalar Dependenias
Antes de ejecutar el proyecto se deben instalar las dependencias usando la herramienta composer:

```sh
$ composer intall
```

## Configurar Variables de Entorno para OpenCart

Se debe copiar el archivo `.env.sample` que se encuentra en el directorio `dev` y guardarlo en el mismo directorio `dev` con el nombre de archivo `.env`.

Modificar las variables de entorno que usa OpenCart según sea necesario:

### OpenCart Database connection values
OC_DB_HOSTNAME=localhost
OC_DB_USERNAME=opencart
OC_DB_PASSWORD=opencart
OC_DB_DATABASE=opencart
OC_DB_DRIVER=mysqli

### OpenCart Administration user
OC_USERNAME=admin
OC_PASSWORD=admin
OC_EMAIL=you@example.com

### Server Specification
SERVER_PORT=8000
SERVER_URL=http://localhost


## Ejecutar Pruebas
Las pruebas funcionales unitarias se ejecutan desde el directorio `dev` con los siguientes pasos:

```sh
$ bin/robo opencart:setup (Paso 1. Configura el entorno de OpenCart)
$ bin/robo project:deploy (Paso 2. Realiza un Deploy de OpenCart)
$ bin/phpunit --testsuite catalog-tests (Paso 3. Ejecuta las pruebas del catalogo 'catalog-test' definidas en la suite phpunit.xml)
$ opencart:run (Paso 4. Ejecuta servidor de OpenCart)
```

El paso número 4. es opcional, para ejecutar solo las pruebas solo es necesario ejecutar los paso 1. - 3.

### Suite de Pruebas
La suite de pruebas se configura en el archivo `dev/phpunit.xml` se pueden crear bloques que componen la suite siguiendo el patrón:

```xml
<testsuites>
    <testsuite name="catalog-tests">
        <file>./tests/HelloWorldTest.php</file>
    </testsuite>
    <testsuite name="admin-tests">
        <file>./tests/HelloWorldAdminTest.php</file>
    </testsuite>
</testsuites>
```

Todos los archivos de pruebas que sean creados se deben guardar sobre el directorio `dev/tests` los cuales hacen parte de la suite de pruebas.
