---
title: "Problema Durante Actualización. Fallo con APT"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by ebulga on 2010-05-04
Hola a todos, a ver si alguien me puede ayudar...

Primero (muy contento) me puse a actualizar mi Ubuntu 9.10 por Ubuntu 10.04. Como el repositorio de Argentina estaba saturado, utilicé uno de EEUU; sin embargo éte también se cortó y tuve que intentar de nuevo: terminé usando el de Argentina.

Finalmente la instalación termina pero con errores. Desde entonces, una vez que reinicé, no puedo entrar a mi ubuntu de la forma habitual. Para entrar tengo que usar el kernel de recuperación.

Se me ocurrió intentar actualizar para que descargue nuevamente los paquetes. el gestor de actualizaciones me da el siguientes detalle de error:

```
Preconfigurando paquetes ...
Configurando apt (0.7.25.3ubuntu7) ...
dpkg: error al procesar apt (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
Se encontraron errores al procesar:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

Un paquete no se pudo instalar. Tratando de recuperarlo:
Configurando apt (0.7.25.3ubuntu7) ...
dpkg: error al procesar apt (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de apt-transport-https:
 apt-transport-https depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar apt-transport-https (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de packagekit:
 packagekit depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar packagekit (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de tasksel:
 tasksel depende de apt (>= 0.6.45ubuntu14); sin embargo:
 El paquete `apt' no está configurado todavía.
dpkg: error al procesar tasksel (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de tasksel-data:
 tasksel-data depende de tasksel; sin embargo:
 El paquete `tasksel' no está configurado todavía.
dpkg: error al procesar tasksel-data (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de packagekit-backend-apt:
 packagekit-backend-apt depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar packagekit-backend-apt (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de synaptic:
 synaptic depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar synaptic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kpackagekit:
 kpackagekit depende de packagekit (>= 0.4.7); sin embargo:
 El paquete `packagekit' no está configurado todavía.
dpkg: error al procesar kpackagekit (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de unattended-upgrades:
 unattended-upgrades depende de apt (>= 0.7); sin embargo:
 El paquete `apt' no está configurado todavía.
dpkg: error al procesar unattended-upgrades (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-codec-install:
 gnome-codec-install depende de synaptic (>= 0.57.8); sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar gnome-codec-install (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de jockey-gtk:
 jockey-gtk depende de synaptic; sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar jockey-gtk (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de aptitude:
 aptitude depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar aptitude (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-desktop:
 ubuntu-desktop depende de synaptic; sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar ubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libept0:
 libept0 depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar libept0 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libpackagekit-glib2-12:
 libpackagekit-glib2-12 depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar libpackagekit-glib2-12 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-apt:
 python-apt depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar python-apt (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de language-selector-common:
 language-selector-common depende de python-apt (>= 0.7.12.0); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar language-selector-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de apt-utils:
 apt-utils depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar apt-utils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager:
 update-manager depende de synaptic (>= 0.57.8); sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar update-manager (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-minimal:
 ubuntu-minimal depende de apt; sin embargo:
 El paquete `apt' no está configurado todavía.
 ubuntu-minimal depende de apt-utils; sin embargo:
 El paquete `apt-utils' no está configurado todavía.
 ubuntu-minimal depende de tasksel; sin embargo:
 El paquete `tasksel' no está configurado todavía.
dpkg: error al procesar ubuntu-minimal (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-notifier-common:
 update-notifier-common depende de python-apt (>= 0.6.12); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar update-notifier-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-debian:
 python-debian depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar python-debian (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libpackagekit-qt-12:
 libpackagekit-qt-12 depende de libapt-pkg-libc6.10-6-4.8; sin embargo:
  El paquete `libapt-pkg-libc6.10-6-4.8' no está instalado.
  El paquete `apt' que provee `libapt-pkg-libc6.10-6-4.8' aún no está configurado.
dpkg: error al procesar libpackagekit-qt-12 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-properties-gtk:
 software-properties-gtk depende de synaptic (>= 0.57.8); sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar software-properties-gtk (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de apturl-common:
 apturl-common depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar apturl-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-aptdaemon:
 python-aptdaemon depende de python-apt (>= 0.7.9); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar python-aptdaemon (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de apturl:
 apturl depende de apturl-common (= 0.4.1ubuntu4); sin embargo:
 El paquete `apturl-common' no está configurado todavía.
 apturl depende de software-properties-gtk; sin embargo:
 El paquete `software-properties-gtk' no está configurado todavía.
 apturl depende de synaptic; sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar apturl (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de language-selector:
 language-selector depende de language-selector-common (= 0.5.7); sin embargo:
 El paquete `language-selector-common' no está configurado todavía.
 language-selector depende de python-apt (>= 0.6.12); sin embargo:
 El paquete `python-apt' no está configurado todavía.
 language-selector depende de synaptic; sin embargo:
 El paquete `synaptic' no está configurado todavía.
dpkg: error al procesar language-selector (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de apt-xapian-index:
 apt-xapian-index depende de python-apt (>= 0.7.93.2); sin embargo:
 El paquete `python-apt' no está configurado todavía.
 apt-xapian-index depende de python-debian (>= 0.1.13); sin embargo:
 El paquete `python-debian' no está configurado todavía.
dpkg: error al procesar apt-xapian-index (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ailurus:
 ailurus depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar ailurus (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de jockey-common:
 jockey-common depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar jockey-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de computer-janitor:
 computer-janitor depende de python-apt (>= 0.7.9); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar computer-janitor (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-software-properties:
 python-software-properties depende de python-apt (>= 0.6.20ubuntu16); sin embargo:
 El paquete `python-apt' no está configurado todavía.
 python-software-properties depende de unattended-upgrades; sin embargo:
 El paquete `unattended-upgrades' no está configurado todavía.
dpkg: error al procesar python-software-properties (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-standard:
 ubuntu-standard depende de aptitude; sin embargo:
 El paquete `aptitude' no está configurado todavía.
 ubuntu-standard depende de language-selector-common; sin embargo:
 El paquete `language-selector-common' no está configurado todavía.
dpkg: error al procesar ubuntu-standard (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-apport:
 python-apport depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar python-apport (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-center:
 software-center depende de python-apt (>= 0.7.13.4ubuntu3); sin embargo:
 El paquete `python-apt' no está configurado todavía.
 software-center depende de python-aptdaemon (>= 0.11+bzr342); sin embargo:
 El paquete `python-aptdaemon' no está configurado todavía.
dpkg: error al procesar software-center (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gdebi-core:
 gdebi-core depende de python-apt (>= 0.7.0); sin embargo:
 El paquete `python-apt' no está configurado todavía.
 gdebi-core depende de python-debian; sin embargo:
 El paquete `python-debian' no está configurado todavía.
dpkg: error al procesar gdebi-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager-core:
 update-manager-core depende de python-apt (>= 0.7.13.4ubuntu3); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar update-manager-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kubuntu-debug-installer:
 kubuntu-debug-installer depende de kpackagekit; sin embargo:
 El paquete `kpackagekit' no está configurado todavía.
dpkg: error al procesar kubuntu-debug-installer (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-properties-kde:
 software-properties-kde depende de python-software-properties; sin embargo:
 El paquete `python-software-properties' no está configurado todavía.
dpkg: error al procesar software-properties-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gdebi-kde:
 gdebi-kde depende de gdebi-core (= 0.6.0ubuntu1); sin embargo:
 El paquete `gdebi-core' no está configurado todavía.
dpkg: error al procesar gdebi-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-notifier:
 update-notifier depende de update-notifier-common (= 0.99.3); sin embargo:
 El paquete `update-notifier-common' no está configurado todavía.
 update-notifier depende de update-manager; sin embargo:
 El paquete `update-manager' no está configurado todavía.
dpkg: error al procesar update-notifier (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager-kde:
 update-manager-kde depende de update-manager-core; sin embargo:
 El paquete `update-manager-core' no está configurado todavía.
dpkg: error al procesar update-manager-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de command-not-found:
 command-not-found depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar command-not-found (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gdebi:
 gdebi depende de gdebi-core (= 0.6.0ubuntu1); sin embargo:
 El paquete `gdebi-core' no está configurado todavía.
dpkg: error al procesar gdebi (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de aptdaemon:
 aptdaemon depende de python-aptdaemon (= 0.11+bzr345-0ubuntu4); sin embargo:
 El paquete `python-aptdaemon' no está configurado todavía.
dpkg: error al procesar aptdaemon (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-aptdaemon-gtk:
 python-aptdaemon-gtk depende de python-aptdaemon (= 0.11+bzr345-0ubuntu4); sin embargo:
 El paquete `python-aptdaemon' no está configurado todavía.
dpkg: error al procesar python-aptdaemon-gtk (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de network-manager:
 network-manager depende de update-notifier-common; sin embargo:
 El paquete `update-notifier-common' no está configurado todavía.
dpkg: error al procesar network-manager (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de rhythmbox-ubuntuone-music-store:
 rhythmbox-ubuntuone-music-store depende de python-aptdaemon-gtk (>= 0.11+bzr345-0ubuntu3); sin embargo:
 El paquete `python-aptdaemon-gtk' no está configurado todavía.
dpkg: error al procesar rhythmbox-ubuntuone-music-store (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-system-service:
 ubuntu-system-service depende de python-apt (>= 0.7.0); sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar ubuntu-system-service (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de landscape-common:
 landscape-common depende de python-apt; sin embargo:
 El paquete `python-apt' no está configurado todavía.
dpkg: error al procesar landscape-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: demasiados errores, parando
Se encontraron errores al procesar:
 apt
 apt-transport-https
 packagekit
 tasksel
 tasksel-data
 packagekit-backend-apt
 synaptic
 kpackagekit
 unattended-upgrades
 gnome-codec-install
 jockey-gtk
 aptitude
 ubuntu-desktop
 libept0
 libpackagekit-glib2-12
 python-apt
 language-selector-common
 apt-utils
 update-manager
 ubuntu-minimal
 update-notifier-common
 python-debian
 libpackagekit-qt-12
 software-properties-gtk
 apturl-common
 python-aptdaemon
 apturl
 language-selector
 apt-xapian-index
 ailurus
 jockey-common
 computer-janitor
 python-software-properties
 ubuntu-standard
 python-apport
 software-center
 gdebi-core
 update-manager-core
 kubuntu-debug-installer
 software-properties-kde
 gdebi-kde
 update-notifier
 update-manager-kde
 command-not-found
 gdebi
 aptdaemon
 python-aptdaemon-gtk
 network-manager
 rhythmbox-ubuntuone-music-store
 ubuntu-system-service
 landscape-common
Proceso detenido por haber demasiados errores.
```

[B]
Parece que el problema es con el paquete apt. Quiero reinstalarlo pero no me deja...[/B]

sudo aptitude update
sudo aptitude reinstall apt

El error es el mismo que antes... no se cómo arreglarlo

```
dpkg: demasiados errores, parando
Se encontraron errores al procesar:
 apt
 apt-transport-https
 packagekit
 tasksel
 tasksel-data
 packagekit-backend-apt
 synaptic
 kpackagekit
 unattended-upgrades
 gnome-codec-install
 jockey-gtk
 aptitude
 ubuntu-desktop
 libept0
 libpackagekit-glib2-12
 python-apt
 language-selector-common
 apt-utils
 update-manager
 ubuntu-minimal
 update-notifier-common
 python-debian
 libpackagekit-qt-12
 software-properties-gtk
 apturl-common
 python-aptdaemon
 apturl
 language-selector
 apt-xapian-index
 ailurus
 jockey-common
 computer-janitor
 python-software-properties
 ubuntu-standard
 python-apport
 software-center
 gdebi-core
 update-manager-core
 kubuntu-debug-installer
 software-properties-kde
 gdebi-kde
 update-notifier
 update-manager-kde
 command-not-found
 gdebi
 aptdaemon
 python-aptdaemon-gtk
 network-manager
 rhythmbox-ubuntuone-music-store
 ubuntu-system-service
 landscape-common
```

Proceso detenido por haber demasiados errores.
Alguna idea? ¿cómo puedo hacer para que se bajen nuevamente todos los paquetes y se reinstale todo?

---

