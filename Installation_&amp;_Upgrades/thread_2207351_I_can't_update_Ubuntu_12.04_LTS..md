---
title: "I can't update Ubuntu 12.04 LTS."
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by milena-veselinova on 2014-02-23
I have to install 34 updates, but I can't.
I open the update manager and I write my pass. The updates starts to download, but when they're finishing appears an error:

installArchives() failed: 
 Extrayendo plantillas para los paquetes: 88%% 
 Extrayendo plantillas para los paquetes: 100%% 
 Extrayendo plantillas para los paquetes: 88%% 
 Extrayendo plantillas para los paquetes: 100%% 
 Extrayendo plantillas para los paquetes: 88%% 
 Extrayendo plantillas para los paquetes: 100%% 
 Extrayendo plantillas para los paquetes: 88%% 
 Extrayendo plantillas para los paquetes: 100%% 
(Reading database ... 
(Reading database ... 5%% 
(Reading database ... 10%%
(Reading database ... 15%% 
(Reading database ... 20%% 
(Reading database ... 25%% 
(Reading database ... 30%% 
(Reading database ... 35%% 
(Reading database ... 40%% 
(Reading database ... 45%% 
(Reading database ... 50%% 
(Reading database ... 55%% 
(Reading database ... 60%%
(Reading database ... 65%% 
(Reading database ... 70%% 
(Reading database ... 75%%
(Reading database ... 80%% 
(Reading database ... 85%%
dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'firefox': Input/output error 
Error in function:  


Someone can help me? :confused: 
I'm getting nervous trying to solve it...

---

### Post by fdrake on 2014-02-23
try this (in the termianl,; close update manager)
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo dpkg --clear-avail
sudo apt-get upgrade && sudo apt-get update

```

---

### Post by milena-veselinova on 2014-02-28
Thanks for the reply, but it doesn't work. When I write that code...
[I]
milena@milena-R519-R719:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.badmv: no se puede efectuar `stat' sobre «/var/lib/dpkg/status»: No existe el archivo o el directorio
milena@milena-R519-R719:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/statusmilena@milena-R519-R719:~$ sudo dpkg --clear-avail
milena@milena-R519-R719:~$ sudo apt-get upgrade && sudo apt-get update
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se han retenido:
  linux-generic-pae linux-headers-generic-lts-raring linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-pae
Se actualizarán los siguientes paquetes:
  appmenu-gtk appmenu-gtk3 file firefox firefox-locale-en firefox-locale-es
  flashplugin-installer gnome-settings-daemon icedtea-6-jre-cacao
  icedtea-6-jre-jamvm indicator-appmenu iproute jockey-common jockey-gtk
  libdvdnav4 libgnutls26 libmagic1 libnm-glib-vpn1 libnm-glib4 libnm-util2
  linux-firmware linux-generic-lts-raring linux-libc-dev network-manager
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us thunderbird-locale-es thunderbird-locale-es-es
  usb-creator-common usb-creator-gtk xkb-data
37 actualizados, 0 se instalarán, 0 para eliminar y 5 no actualizados.
Se necesita descargar 0 B/138 MB de archivos.
Se liberarán 22,4 MB después de esta operación.
¿Desea continuar [S/n]? s
Extrayendo plantillas para los paquetes: 100%
Preconfigurando paquetes ...
(Leyendo la base de datos ... 85%dpkg: error fatal irrecuperable, abortando:
 leyendo la lista de ficheros para el paquete 'firefox': Error de entrada/salida
E: Sub-process /usr/bin/dpkg returned an error code (2)

[/I]

---

