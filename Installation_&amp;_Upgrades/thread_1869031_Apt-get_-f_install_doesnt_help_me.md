---
title: "Apt-get -f install doesnt help me"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by skyline2412 on 2011-10-25
I was trying to install openjdk-7-jre offline installing with dpkg -i the package and dependencies but i screwed up.

Errors while installing:
```
me@me:~/Escritorio/openjdk-7-jre$ sudo dpkg -i *.deb
(Leyendo la base de datos ... 184523 ficheros o directorios instalados actualmente.)
Preparando para reemplazar libaccess-bridge-java-jni 1.26.2-6 (usando libaccess-bridge-java-jni_1.26.2-6_amd64.deb) ...
Desempaquetando el reemplazo de libaccess-bridge-java-jni ...
Preparando para reemplazar libasound2 1.0.24.1-0ubuntu10 (usando libasound2_1.0.24.1-0ubuntu10_amd64.deb) ...
Desempaquetando el reemplazo de libasound2 ...
Preparando para reemplazar libc6 2.13-20ubuntu5 (usando libc6_2.13-20ubuntu5_amd64.deb) ...
Desempaquetando el reemplazo de libc6 ...
Preparando para reemplazar libcups2 1.5.0-8 (usando libcups2_1.5.0-8_amd64.deb) ...
Desempaquetando el reemplazo de libcups2 ...
Preparando para reemplazar libfontconfig1 2.8.0-3ubuntu2 (usando libfontconfig1_2.8.0-3ubuntu2_amd64.deb) ...
Desempaquetando el reemplazo de libfontconfig1 ...
Preparando para reemplazar libgdk-pixbuf2.0-0 2.24.0-1ubuntu1 (usando libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de libgdk-pixbuf2.0-0 ...
Preparando para reemplazar libgif4 4.1.6-9 (usando libgif4_4.1.6-9_amd64.deb) ...
Desempaquetando el reemplazo de libgif4 ...
Preparando para reemplazar libglib2.0-0 2.30.0-0ubuntu4 (usando libglib2.0-0_2.30.0-0ubuntu4_amd64.deb) ...
Desempaquetando el reemplazo de libglib2.0-0 ...
Preparando para reemplazar libgtk2.0-0 2.24.6-0ubuntu5 (usando libgtk2.0-0_2.24.6-0ubuntu5_amd64.deb) ...
Desempaquetando el reemplazo de libgtk2.0-0 ...
Preparando para reemplazar libjpeg62 6b1-1ubuntu2 (usando libjpeg62_6b1-1ubuntu2_amd64.deb) ...
Desempaquetando el reemplazo de libjpeg62 ...
Preparando para reemplazar libpango1.0-0 1.29.3+git20110916-0ubuntu1 (usando libpango1.0-0_1.29.3+git20110916-0ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de libpango1.0-0 ...
Preparando para reemplazar libpng12-0 1.2.46-3ubuntu1 (usando libpng12-0_1.2.46-3ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de libpng12-0 ...
Preparando para reemplazar libpulse0 1:1.0-0ubuntu3 (usando libpulse0_1.0-0ubuntu3_amd64.deb) ...
Desempaquetando el reemplazo de libpulse0 ...
Preparando para reemplazar libx11-6 2:1.4.4-2ubuntu1 (usando libx11-6_1.4.4-2ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de libx11-6 ...
Preparando para reemplazar libxext6 2:1.3.0-3 (usando libxext6_1.3.0-3_amd64.deb) ...
Desempaquetando el reemplazo de libxext6 ...
Preparando para reemplazar libxi6 2:1.4.3-3ubuntu1 (usando libxi6_1.4.3-3ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de libxi6 ...
Preparando para reemplazar libxrender1 1:0.9.6-2 (usando libxrender1_0.9.6-2_amd64.deb) ...
Desempaquetando el reemplazo de libxrender1 ...
Preparando para reemplazar libxtst6 2:1.2.0-3 (usando libxtst6_1.2.0-3_amd64.deb) ...
Desempaquetando el reemplazo de libxtst6 ...
Preparando para reemplazar openjdk-7-jre 7~b147-2.0~pre6-1ubuntu1 (usando openjdk-7-jre_7~b147-2.0~pre6-1ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de openjdk-7-jre ...
Preparando para reemplazar openjdk-7-jre-headless 7~b147-2.0~pre6-1ubuntu1 (usando openjdk-7-jre-headless_7~b147-2.0~pre6-1ubuntu1_amd64.deb) ...
Desempaquetando el reemplazo de openjdk-7-jre-headless ...
Configurando libc6 (2.13-20ubuntu5) ...
dpkg: error al procesar libcups2 (--install):
 libcups2:amd64 1.5.0-8 no puede configurarse porque libcups2:i386 es una versión diferente (1.5.0-8ubuntu3)
Configurando libfontconfig1 (2.8.0-3ubuntu2) ...
Configurando libgif4 (4.1.6-9) ...
Configurando libglib2.0-0 (2.30.0-0ubuntu4) ...
dpkg: problemas de dependencias impiden la configuración de libgtk2.0-0:
 libgtk2.0-0 depende de libcups2 (>= 1.4.0); sin embargo:
 El paquete `libcups2' no está configurado todavía.
dpkg: error al procesar libgtk2.0-0 (--install):
 problemas de dependencias - se deja sin configurar
Configurando libjpeg62 (6b1-1ubuntu2) ...
Configurando libpng12-0 (1.2.46-3ubuntu1) ...
Configurando libpulse0 (1:1.0-0ubuntu3) ...
Configurando libx11-6 (2:1.4.4-2ubuntu1) ...
Configurando libxext6 (2:1.3.0-3) ...
Configurando libxi6 (2:1.4.3-3ubuntu1) ...
Configurando libxrender1 (1:0.9.6-2) ...
Configurando libxtst6 (2:1.2.0-3) ...
dpkg: problemas de dependencias impiden la configuración de openjdk-7-jre:
 openjdk-7-jre depende de libcups2 (>= 1.4.0); sin embargo:
 El paquete `libcups2' no está configurado todavía.
 openjdk-7-jre depende de libgtk2.0-0 (>= 2.8.0); sin embargo:
 El paquete `libgtk2.0-0' no está configurado todavía.
dpkg: error al procesar openjdk-7-jre (--install):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de openjdk-7-jre-headless:
 openjdk-7-jre-headless depende de openjdk-7-jre-lib (>= 7~b147-2.0~pre6-1ubuntu1); sin embargo:
 El paquete `openjdk-7-jre-lib' no está configurado todavía.
 openjdk-7-jre-headless depende de libcups2 (>= 1.4.0); sin embargo:
 El paquete `libcups2' no está configurado todavía.
dpkg: error al procesar openjdk-7-jre-headless (--install):
 problemas de dependencias - se deja sin configurar
Configurando libasound2 (1.0.24.1-0ubuntu10) ...
Procesando disparadores para doc-base ...
Procesando 1 archivo doc-base cambiado...
Registrando documentos con scrollkeeper...
Procesando disparadores para libglib2.0-0:i386 ...
Configurando libpango1.0-0 (1.29.3+git20110916-0ubuntu1) ...
Configurando libaccess-bridge-java-jni (1.26.2-6) ...
Configurando libgdk-pixbuf2.0-0 (2.24.0-1ubuntu1) ...
Procesando disparadores para desktop-file-utils ...
Procesando disparadores para gnome-menus ...
Procesando disparadores para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Procesando disparadores para hicolor-icon-theme ...
Procesando disparadores para menu ...
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 libcups2
 libgtk2.0-0
 openjdk-7-jre
 openjdk-7-jre-headless
```


Files I tried to install
```
me@me:~/Escritorio/openjdk-7-jre$ ls
libaccess-bridge-java-jni_1.26.2-6_amd64.deb
libasound2_1.0.24.1-0ubuntu10_amd64.deb
libc6_2.13-20ubuntu5_amd64.deb
libcups2_1.5.0-8_amd64.deb
libfontconfig1_2.8.0-3ubuntu2_amd64.deb
libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_amd64.deb
libgif4_4.1.6-9_amd64.deb
libglib2.0-0_2.30.0-0ubuntu4_amd64.deb
libgtk2.0-0_2.24.6-0ubuntu5_amd64.deb
libjpeg62_6b1-1ubuntu2_amd64.deb
libpango1.0-0_1.29.3+git20110916-0ubuntu1_amd64.deb
libpng12-0_1.2.46-3ubuntu1_amd64.deb
libpulse0_1.0-0ubuntu3_amd64.deb
libx11-6_1.4.4-2ubuntu1_amd64.deb
libxext6_1.3.0-3_amd64.deb
libxi6_1.4.3-3ubuntu1_amd64.deb
libxrender1_0.9.6-2_amd64.deb
libxtst6_1.2.0-3_amd64.deb
openjdk-7-jre_7~b147-2.0~pre6-1ubuntu1_amd64.deb
openjdk-7-jre-headless_7~b147-2.0~pre6-1ubuntu1_amd64.deb
```


```
me@me:~$ sudo apt-get upgrade
[sudo] password for me: 
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 libcups2 : Rompe: libcups2:i386 (!= 1.5.0-8) pero 1.5.0-8ubuntu3 está instalado
 libcups2:i386 : Rompe: libcups2 (!= 1.5.0-8ubuntu3) pero 1.5.0-8 está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
me@me:~$
```

Apt-get -f install doesnt help me.
```
me@me:~/Escritorio/openjdk-7-jre$ sudo apt-get -f install
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
  libcups2
Se actualizarán los siguientes paquetes:
  libcups2
1 actualizados, 0 se instalarán, 0 para eliminar y 8 no actualizados.
6 no instalados del todo o eliminados.
Se necesita descargar 0 B/173 kB de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ... 184523 ficheros o directorios instalados actualmente.)
Preparando para reemplazar libcups2 1.5.0-8 (usando .../libcups2_1.5.0-8ubuntu3_amd64.deb) ...
Desempaquetando el reemplazo de libcups2 ...
dpkg: error al procesar /var/cache/apt/archives/libcups2_1.5.0-8ubuntu3_amd64.deb (--unpack):
 «./usr/share/doc/libcups2/changelog.Debian.gz» es diferente del mismo archivo en el sistema
dpkg-deb: error: el subproceso copiado se mató con la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/libcups2_1.5.0-8ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas/help, apart from reinstall distrib?

thx

---

### Post by dino99 on 2011-10-25
open synaptic and look at broken package(s)
your post indicate a PARTIAL upgrade, which means you need some patience and wait to get the missing packages (still not ready into archives)

this issue can also be due to, either:
- borked sources.list (mixing distro sources)
- some third party repo(s) (ppa)

so start by cleaning the system first.

---

### Post by skyline2412 on 2011-10-25
Thanks for answer, I updated the thread with all information i have, i supoosed it could help

Sorry I dont jave synaptic installed on oneiric and cant install because of these errors.

but as you say problematic dependency could be libcup2 isnt it?

thx

---

### Post by dino99 on 2011-10-25
as i've previously said:
- clean the system first (clean/autoclean/autoremove),
- then comment out all third party entries into /etc/apt/sources.list
- when done, update again
- install synaptic

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by skyline2412 on 2011-10-25
· autoclean & autoremove:
```
me@me:~$ sudo apt-get autoclean && sudo apt-get autoremove
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 libcups2 : Rompe: libcups2:i386 (!= 1.5.0-8) pero 1.5.0-8ubuntu3 está instalado
 libcups2:i386 : Rompe: libcups2 (!= 1.5.0-8ubuntu3) pero 1.5.0-8 está instalado
E: Dependencias incumplidas. Pruebe de nuevo usando -f.
```

· I deselected third party repositories from software sources GUI of ubuntu. (Only some PPAs launchpad) and commented with gedit the third party entries of sources.list

· update:
```
me@me:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease                                 
Obj http://extras.ubuntu.com oneiric Release.gpg                              
Ign http://archive.ubuntu.com oneiric InRelease       
Ign http://archive.ubuntu.com oneiric-updates InRelease
Ign http://archive.ubuntu.com oneiric-backports InRelease
Obj http://extras.ubuntu.com oneiric Release           
Ign http://archive.ubuntu.com oneiric-security InRelease
Obj http://archive.ubuntu.com oneiric Release.gpg
Obj http://extras.ubuntu.com oneiric/main Sources      
Obj http://archive.ubuntu.com oneiric-updates Release.gpg
Obj http://archive.ubuntu.com oneiric-backports Release.gpg
Obj http://archive.ubuntu.com oneiric-security Release.gpg
Obj http://archive.ubuntu.com oneiric Release          
Obj http://archive.ubuntu.com oneiric-updates Release                         
Obj http://archive.ubuntu.com oneiric-backports Release                       
Obj http://archive.ubuntu.com oneiric-security Release                        
Obj http://archive.ubuntu.com oneiric/main Sources                            
Obj http://archive.ubuntu.com oneiric/restricted Sources
Obj http://archive.ubuntu.com oneiric/universe Sources 
Obj http://archive.ubuntu.com oneiric/multiverse Sources
Obj http://archive.ubuntu.com oneiric/main amd64 Packages
Obj http://archive.ubuntu.com oneiric/restricted amd64 Packages
Obj http://archive.ubuntu.com oneiric/universe amd64 Packages
Obj http://archive.ubuntu.com oneiric/multiverse amd64 Packages
Obj http://archive.ubuntu.com oneiric/main i386 Packages
Obj http://archive.ubuntu.com oneiric/restricted i386 Packages
Obj http://archive.ubuntu.com oneiric/universe i386 Packages
Obj http://archive.ubuntu.com oneiric/multiverse i386 Packages
Obj http://archive.ubuntu.com oneiric/main TranslationIndex
Obj http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Obj http://archive.ubuntu.com oneiric/restricted TranslationIndex
Obj http://archive.ubuntu.com oneiric/universe TranslationIndex
Obj http://archive.ubuntu.com oneiric-updates/main Sources
Obj http://archive.ubuntu.com oneiric-updates/restricted Sources
Obj http://archive.ubuntu.com oneiric-updates/universe Sources
Obj http://archive.ubuntu.com oneiric-updates/multiverse Sources
Obj http://archive.ubuntu.com oneiric-updates/main amd64 Packages
Obj http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Obj http://archive.ubuntu.com oneiric-updates/universe amd64 Packages
Obj http://extras.ubuntu.com oneiric/main amd64 Packages
Obj http://extras.ubuntu.com oneiric/main i386 Packages
Obj http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Obj http://archive.ubuntu.com oneiric-updates/main i386 Packages
Obj http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Obj http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Obj http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Obj http://archive.ubuntu.com oneiric-updates/main TranslationIndex
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Obj http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Obj http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Obj http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Obj http://archive.ubuntu.com oneiric-backports/main Sources
Obj http://archive.ubuntu.com oneiric-backports/restricted Sources
Obj http://archive.ubuntu.com oneiric-backports/universe Sources
Obj http://archive.ubuntu.com oneiric-backports/multiverse Sources
Obj http://archive.ubuntu.com oneiric-backports/main amd64 Packages
Obj http://archive.ubuntu.com oneiric-backports/restricted amd64 Packages
Obj http://archive.ubuntu.com oneiric-backports/universe amd64 Packages
Obj http://archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Obj http://archive.ubuntu.com oneiric-backports/main i386 Packages
Obj http://archive.ubuntu.com oneiric-backports/restricted i386 Packages
Obj http://archive.ubuntu.com oneiric-backports/universe i386 Packages
Obj http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Obj http://archive.ubuntu.com oneiric-backports/main TranslationIndex
Obj http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Obj http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Obj http://archive.ubuntu.com oneiric-backports/universe TranslationIndex
Obj http://archive.ubuntu.com oneiric-security/main Sources
Obj http://archive.ubuntu.com oneiric-security/restricted Sources
Obj http://archive.ubuntu.com oneiric-security/universe Sources
Obj http://archive.ubuntu.com oneiric-security/multiverse Sources
Obj http://archive.ubuntu.com oneiric-security/main amd64 Packages
Obj http://archive.ubuntu.com oneiric-security/restricted amd64 Packages
Obj http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Obj http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Obj http://archive.ubuntu.com oneiric-security/main i386 Packages
Obj http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Obj http://archive.ubuntu.com oneiric-security/universe i386 Packages
Obj http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Obj http://archive.ubuntu.com oneiric-security/main TranslationIndex
Obj http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Obj http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Obj http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Obj http://archive.ubuntu.com oneiric/main Translation-es
Obj http://archive.ubuntu.com oneiric/main Translation-en
Obj http://archive.ubuntu.com oneiric/multiverse Translation-es
Obj http://archive.ubuntu.com oneiric/multiverse Translation-en
Obj http://archive.ubuntu.com oneiric/restricted Translation-es
Obj http://archive.ubuntu.com oneiric/restricted Translation-en
Obj http://archive.ubuntu.com oneiric/universe Translation-es
Obj http://archive.ubuntu.com oneiric/universe Translation-en
Obj http://archive.ubuntu.com oneiric-updates/main Translation-en
Obj http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Obj http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Obj http://archive.ubuntu.com oneiric-updates/universe Translation-en
Obj http://archive.ubuntu.com oneiric-backports/main Translation-en
Obj http://archive.ubuntu.com oneiric-backports/multiverse Translation-en
Obj http://archive.ubuntu.com oneiric-backports/restricted Translation-en
Obj http://archive.ubuntu.com oneiric-backports/universe Translation-en
Obj http://archive.ubuntu.com oneiric-security/main Translation-en
Obj http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Obj http://archive.ubuntu.com oneiric-security/restricted Translation-en
Obj http://archive.ubuntu.com oneiric-security/universe Translation-en
Leyendo listas de paquetes... Hecho

```

cant install synpatic yet

```
me@me:~$ sudo apt-get install synaptic 
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
 libcups2 : Rompe: libcups2:i386 (!= 1.5.0-8) pero 1.5.0-8ubuntu3 va a ser instalado
 libcups2:i386 : Rompe: libcups2 (!= 1.5.0-8ubuntu3) pero 1.5.0-8 va a ser instalado
 synaptic : Depende de: libept1 pero no va a instalarse
E: Dependencias incumplidas. Intente «apt-get -f install» sin paquetes (o especifique una solución).
```

---

### Post by raja.genupula on 2011-10-25
Have you tried with 

```
sudo apt-get install -f
```


then do this ```
sudo apt-get update
```

all the best.

---

### Post by skyline2412 on 2011-10-25
Yes, but it doesnt solved nothing, it happened the same error.

I gave up and reinstall. thx all

---

### Post by raja.genupula on 2011-10-25
> **skyline2412 said:**
> Yes, but it doesnt solved nothing, it happened the same error.

I gave up and reinstall. thx all

Hi man 
come on no need to go for new install .Actually partial upgrades take your system unstable.
 By looking at the dino post i got that you did partial .So please wait for a while to get a good upgrade and i am sure that gonna solve the issue.so please be patient for a while.

---

