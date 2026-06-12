---
title: "I can't install anything after upgrading"
date: 2022-02-10
forum: Installation &amp; Upgrades
---

### Post by oscarinho5 on 2022-02-10
When I try to install any package I always get the same messages:


```
@:~# sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
5 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Configurando libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.29) ...
php5_invoke intl: already enabled for apache2 SAPI
php5_invoke curl: already enabled for apache2 SAPI
php5_invoke pdo_mysql: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for apache2 SAPI
dpkg: error al procesar el paquete libapache2-mod-php5 (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de php5:
 php5 depende de libapache2-mod-php5 (>= 5.5.9+dfsg-1ubuntu4.29) | libapache2-mod-php5filter (>= 5.5.9+dfsg-1ubuntu4.29) | php5-cgi (>= 5.5.9+dfsg-1ubuntu4.29) | php5-fpm (>= 5.5.9+dfsg-1ubuntu4.29); sin embargo:
 El paquete `libapache2-mod-php5' no está configurado todavía.
 El paquete `libapache2-mod-php5filter' no está instalado.
 El paquete `php5-cgi' no está instalado.
 El paquete `php5-fpm' no está instalado.


dpkg: error al procesar el paquete php5 (--configure): problemas de dependencias - se deja sin configurar
Configurando php5-cli (5.5.9+dfsg-1ubuntu4.29) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
php5_invoke intl: already enabled for cli SAPI
php5_invoke curl: already enabled for cli SAPI
php5_invoke pdo_mysql: already enabled for cli SAPI
php5_invoke pdo: already enabled for cli SAPI
php5_invoke opcache: already enabled for cli SAPI
dpkg: error al procesar el paquete php5-cli (--configure): el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de php-gettext:
php-gettext depende de php5 | php5-cli; sin embargo: El paquete `php5' no está configurado todavía.
El paquete `php5-cli' no está configurado todavía.


dpkg: error al procesar el paquete php-gettext (--configure):  problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de pkg-php-tools:  pkg-php-tools depende de php5-cli; sin embargo: El paquete `php5-cli' no está configurado todavía.


dpkg: error al procesar el paquete pkg-php-tools (--configure):  problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                                         
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                                                                                                                                  Se encontraron errores al procesar:
 libapache2-mod-php5
 php5
 php5-cli
 php-gettext
 pkg-php-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Can you help me to get out of this loop of errors that prevent me from being able to perform other actions?

---

### Post by breakdaze on 2022-02-14
What did you upgrade from, and to? It says you are missing some dependencies. 

Have you done: sudo apt update
(update package lists)

Next: sudo apt upgrade

Check /var/log/dpkg.log
for information.

Also please run: apt-get check

Please see Chapter 4 of apt guide about why apt-get -f install doesn't always work.

https://www.debian.org/doc/user-manuals#apt-guide

---

### Post by MAFoElffen on 2022-02-15
Well Dang...
```

sudo apt install -f

```
...usually will look at the broken packages and install the missing dependencies to repair them.

But where the dependency error starts a snippet of the translated output says:
```

dpkg: error processing package libapache2-mod-php5 (--configure):
 thread installed post-installation script returned error exit code 1
dpkg: dependency issues prevent php5 configuration:
 php5 depends on libapache2-mod-php5 (>= 5.5.9+dfsg-1ubuntu4.29) | libapache2-mod-php5filter (>= 5.5.9+dfsg-1ubuntu4.29) | php5-cgi (>= 5.5.9+dfsg-1ubuntu4.29) | php5-fpm (>= 5.5.9+dfsg-1ubuntu4.29); but nevertheless:
 The `libapache2-mod-php5' package is not configured yet.
 The `libapache2-mod-php5filter' package is not installed.
 The `php5-cgi' package is not installed.
 The `php5-fpm' package is not installed.

```
I know form the errors that this is a PHP package for Apache...

Note that it says php5, instead of php7.4, which is the current version of PHP in the supported Versions of Ubuntu LTS 18.04 and 20.04... 

Which begs the question of which Version and Edition of Ubuntu are you running, and which version of PHP is this for? And since this is a package for PHP on Apache, which Apache version is this?

First, your answers to that will tell us if what you are trying to do is  for a supported version. Second, it will help us find the version of  the package that might satisfy the depends problem.

---

