# LampDosNiveles
#### Para crear una pila LAMP en dos niveles comezaremos creando unos ficheros de aprovisionamiento
#### esta primera imagen es el fichero de apache2
![](img/Imagen1.jpg)
#### esta segunda pertenece a php
![](img/Imagen3.jpg)
#### y por ultimo tenemos la de mysql 
![](img/Imagen7.jpg)
#### estos ficheros deben tener la extension .sh y la opcion -y es para aceptar la descarga cuando nos salga la opcion *yes/no*
#### ahora editaremos el fichero vagrantfile para crear las maquinas con su aprovisionamiento, su direccion ip para tenerlas en la misma red, un puerto para su acceso y una direccion ip publica en el caso de la maquina de apache
![](img/capturavagrantfile.jpg)
#### estas dos capturas sigentes son el comando para realizar el aprovisionamientos de las maquinas 
![](img/Imagen6.jpg)

![](img/Imagen8.jpg)
#### con el comando sudo service apache2 estatus comprovaremos si el servicio apache esta activo
![](img/Imagen2.jpg)
#### para comprovar si php funciona editaremos el fichero info.php en el directorio  /var/www/html
![](img/Imagen4.jpg)
#### una vez editado provaremos si esta activo poniendo en internet la direccion ip junto con el puerto y el nombre del fichero debiendo mostrar una pagina predeterminada
![](img/Imagen5.jpg)
#### para comprobar si mysql esta funcionando debemos ir a la maquina de mysql y ejecutar la orden sudo systemctl status mysql 
![](img/Imagen9.jpg)
## ahora pasaremos a configurar la base de datos
#### lo primero es bajar el repositorio con en comando git clone como podemos ver en la imagen
![](img/Imagen10.jpg)
#### a continuacion para poder tener acceso desde la otra maquina editaremos el fichero 50-server.conf que se encuentra en /eetc/mysql/mariadb.conf.d para ponerle una ip que este en la misma red
![](img/Imagen11.jpg)

![](img/Imagen12.jpg)
#### una vez editado accederemos a la base de datos con el usuario root y crearemos otro usuario
#### para acceder como root usaremos el comando sudo mysql -u root -p
#### y usaremos el comando create user para crear el usuario nuevo
![](img/Imagen13.jpg)
#### ahora le daremos todos los permisos de la base de datos que queramos a dicho usuario con el comando all privileges
![](img/Imagen14.jpg)
#### para cargar la base de datos que se a bajado anterior mente accedederemos a dicho directorio y entraremos a la carpeta db y ejecutaremos el comando sudo mysql u root -p < database.sql
![](img/Imagen15.jpg)
#### para ver si se a bajado la base de datos accederemos a mysql y con la orden show databases; podemos comprobar que esta ahi
![](img/Imagen16.jpg)
#### ahora reiniciaremos mysql y ya estaria todo echo
![](img/Imagen17.jpg)
## configuracion de apache2
#### para empezar accederemos al directorio /var/www/html y bajaremos el repositorio anterior 
![](img/Imagen18.jpg)

![](img/Imagen19.jpg)
#### en el directorio sites-available editaremos el fichero 000-default.conf y editaremos la linea documentroot con la direccion del repositorio bajado antes en el cual se encuentra src 
![](img/Imagen20.jpg)

![](img/Imagen21.jpg)
#### para despues acceder a la base de datos atraves de internet iremos al directorio src y editaremos config.php con los sigguentes datos

![](img/Imagen23.jpg)
#### la direccion ip del servidor mysql
#### el nombre de la base de datos a la que tiene permisos 
#### el nombre del usuario con los permisos
#### y su contraseña

![](img/Imagen24.jpg)
#### ahora reiniciamos el servidor apache para que se realizen los cambios ejecutados anteriormente
![](img/Imagen25.jpg)
## comprovacion
#### para comprobar si esta esta funcionando correctamente podemos probar a a acceder desde la maquina apache a la base de datos con el usuario creado

![](img/Imagen26.jpg)
#### una vez accedidos a esta podemos añadir campos y estos podran verse accediendo desde internet
![](img/Imagen27.jpg)

![](img/Imagen28.jpg)
#### o en el caso contrario podemos añadir desde internet campos y se podran visualizar en la base de datos
![](img/Imagen29.jpg)
