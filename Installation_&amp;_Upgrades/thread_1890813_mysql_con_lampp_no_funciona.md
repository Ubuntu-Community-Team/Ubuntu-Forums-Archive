---
title: "mysql con lampp no funciona"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by Cabeza_de_Arbol on 2011-12-04
Hola, mi problema es el siguiente:
Instalé lampp, la última versión, pero con antes haber instalado el paquete mysql aparte. Ahora al escribir en consola "/opt/lampp/lampp start" me dice:

Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

..o sea, que hay otro mysql que no es el de lampp arrancado pero no sé cómo detenerlo ni como desinstalarlo.
Saqué además el ejecutable mysql de "/etc/init.d" con lo cual no tengo idea de cómo arranca sólo, alguna idea de qué puedo hacer?

---

### Post by darkod on 2011-12-04
Y si haces:
sudo service mysql start

Depende si se llama mysql en /etc/init.d/ o no.

---

### Post by yodiegogutierrez on 2011-12-04
Hola, a mi me pasa lo mismo. 

Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
Warning: World-writable config file '/opt/lampp/etc/my.cnf' is ignored
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

He intentado: 
sudo service mysql stop

y me arroja lo siguiente:
unrecognized service

y cuando intento detener mysql en:
/etc/init.d/mysql stop

me dice:

root@ubuntu:/etc/init.d# mysql stop
El programa «mysql» puede encontrarse en los siguientes paquetes:
 * mysql-client-core-5.1
 * mysql-cluster-client-5.1
Intente: apt-get install <paquete seleccionado>

Alguna ayuda? el XAMPP anda bien, me muestra la pantalla XAMPP de inicio. El problema es MySQL que no incia:

- Could't Start MySQL!

Y en el PhpMyAdmin, al abrir dice lo siguiente:

Error
MySQL ha dicho: 

#2002 - El servidor no está respondiendo (o el socket del servidor MySQL local no está configurado correctamente) 
La conexión para controluser, como está definida en su configuración, fracasó.


Gracias si alguien me puede ayudar xD

---

### Post by Cabeza_de_Arbol on 2011-12-09
darkod me ayudó tu respuesta, lo que hice fue:

sudo service mysql stop

y luego..

sudo /opt/lampp/lampp start

con eso arrancó el mysql de lampp, igualmente sigo sin desinstalar el otro mysql instalado. Sigo esperando ayuda para encontrar ese.

GRACIAS

---

