Este repositorio sirve para alojar el documento de entrega del trabajo del taller de servidores Linux, y los archivos/directorios del ambiente donde se hizo este trabajo.

Tenemos tres playbooks, que se deberian ejecutar en el siguiente orden:

1. obligatorio.yml
2. tomcat2.yml
3. reverse_proxy2.yml

obligatorio.yml hace las siguientes tareas:
* Actualizacion de los dos servidores Linux (Ubuntu y Rocky) y reiniciar los servers en caso los servidores se hayan actualizado
* Instalacion OpenJDK 17 en el servidor Rocky

tomcat2.yml instala la aplicacion Tomcat 8.5.72, pero hace tareas previas y posteriores:
* Instala tar y unzip en el server Rocky para descomprimir el archivo que contiene el Tomcat 8.5.72
* Crea el usuario y grupo tomcat en el server Rocky
* Crea el directorio /opt/tomcat en el server Rocky para alojar la aplicacion
* Descarga y extrae Tomcat 8.5.72
* Mueve los archivos de Tomcat al directorio creado anteriormente
* Crea un archivo de unidad systemd para Tomcat
* Recarga systemd para registrar como servicio a Tomcat e iniciarlo
* Por ultimo, abre el puerto 8080 en el firewall para poder acceder a la aplicacion por la interfase web

reverse_proxy2.yml hace las siguientes tareas:
* Instala el servidor Apache
* Inicia y registra como servicio Apache
* Copia un archivo de configuracion a la configuracion de Apache para el reverse proxy
* Habilitar los módulos de Apache requeridos para la familia Debian
* Instala el firewall UFW
* Registra el firewall UFW como servicio
* Abre el puerto 80 para el apache web server en el firewall
* Permitir el acceso SSH

Una vez ejecutados los 3 playbooks, las consignas del trabajo estan cumplidas a cabalidad
