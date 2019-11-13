
## Instalación,configuración y despliegue en heroku

  * [Creación Procfile](#procfile)
  * [Alta en Heroku y despliegue](#altaHeroku)
  * [Despliegue atomático Github](#des_github)


<a name="procfile"></a>
### Creación Procfile
Para el despliegue en heroku, tenemos que crear un archivo llamado **Procfile** en la raíz
de nuestro respositorio. En este archivo incluimos los comandos para iniciar nuestra aplicación,en este caso le pasamos:
> web: make start-heroku.

Significa que vamos a desplegar una aplicación web con la herramienta de construcción Makefile en la que hemos definido el target **start-heroku**.

 En el makefile,start-heroku se sitúa en la carpeta contenedora de nuestra aplicación y ejecuta el comando siguiente para iniciarla:
> cd src; gunicorn main:app -b 0000:$(PORT)


<a name="altaHeroku"></a>

### Alta en Heroku y despliegue
**1. Para empezar tenemos que creamos una cuenta en Heroku [Alta Heroku](https://signup.heroku.com/login)**

**2. Instalamos [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install)**

  > sudo snap install heroku --classic

**3. Login en heroku**

  > heroku login

**4. Creamos la aplicación.**

 Se le ha asignado el nombre y el buildpack de python.
 
> heroku create gest-energy --buildpack heroku/python

**5. Despliegue.**

> git push heroku master

**5. Comprobamos que se ha desplegado correctamente en la siguiente URL.**

> https://gest-energy.herokuapp.com/


<a name="des_github"></a>
### Despliegue atomático Github
Podemos habilitar la opción para que nuestra aplicación se despliegue automáticamente cada vez que hacemos push. Para ello tenemos que dirigirnos a la web de [heroku](https://dashboard.heroku.com/apps) dentro de nuestra aplicación y en la sección de deploy habilitamos automatic deploys. Además de marcar **Wait for CI to pass before deploy**
para que se despliegue una vez pasados los test de nuestro CI.
