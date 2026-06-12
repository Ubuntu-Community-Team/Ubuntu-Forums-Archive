---
title: "OpenBravo 3 install error"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by puneetsoni on 2012-05-27
When i am getting the following error
$ sudo dpkg --configure -a
Setting up openbravo-3 (3.0.r16286.MP-11-1oneiric1) ...
 * openbravo-postgresql already started
invoke-rc.d: initscript openbravo-postgresql, action "start" failed.
Setting up Openbravo ERP ...
dpkg: error processing openbravo-3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 openbravo-3
 
now how do i see & how to resolve this issue....
Thanksin advance

---

### Post by stylishkoala on 2013-01-22
Same problem here, I have Ubuntu 12.04 precise x64 fresh install.
Somebody can help us?

When I was installing it this message appears and did not continue the installation proccess:

```
Setting up openbravo-3 (3.0.r19110.MP-18.1-1precise1) ...
/var/lib/dpkg/info/openbravo-3.postinst: 80: [: Illegal number: 
 * Starting openbravo-postgresql                                                                                                                                   [ OK ] 
Setting up Openbravo ERP ...


```

---

### Post by rahul_bhise on 2013-03-31
+1
same error as above (stylishkoala)

---

### Post by sigo70 on 2013-07-16
/var/lib/dpkg/info/openbravo-3.postinst: 80: [: Illegal number:

# reboot

$ sudo su

# dpkg --configure -a

ctrl+c

desinstalo para empesar desde 0
PELIGRO¡ esto puede borrar configuraciones que dependan de los sigientes archivos:
uselo bajo su responsabilidad

# apt-get purge openbravo-3

# apt-get purge apache2*

# apt-get purge openjdk-\* icedtea-\* icedtea6-\*

# apt-get purge tomcat6*

# apt-get purge postgresql*

con esto instala y configura solo que necesita openbravo

# aptitude install openbravo-3

nos vuelve a dar este error

# /var/lib/dpkg/info/openbravo-3.postinst: 80: [: Illegal number:

reiniciamos de nuevo

# reboot

entramos como root

$ sudo su

nos dirigimos aqui

# cd /usr/lib/jvm

checamos

# ls

Responde, varia dependiendo que version de java tengas 

# default-java                                    java-7-openjdk-amd64     java-7-oracle
     java-1.7.0-openjdk-amd64   java-6-oracle                          java-7-openjdk-common

creamos la carpeta java-6-openjdk si no esta instalada

# mkdir java-6-openjdk

# cd java-6-openjdk

# mkdir bin

creamos este enlace yo use java-7-openjdk-amd64 por que es el que
tengo instalado

# ln -s /usr/lib/jvm/java-7-openjdk-amd64/bin/java /usr/lib/jvm/java-6-openjdk/bin/java

de nuevo

# dpkg --configure -a

:D y hoooo¡ despues de varios dias buscando en Google esto funciona :P

Name:~$ sudo su
[sudo] password for asus: 
Name:/home/asus# dpkg --configure -a
Configurando openbravo-3 (3.0.r20659.MP-24.1-1precise1) ...
/var/lib/dpkg/info/openbravo-3.postinst: 80: [: Illegal number: 
 * Starting openbravo-postgresql                                         [ OK ] 
Setting up Openbravo ERP ...
 * Reloading web server config                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
 * Stopping openbravo-postgresql                                         [ OK ] 
 * Starting openbravo-postgresql                                         [ OK ] 
 * Starting openbravo-tomcat                                             [ OK ] 

Installation is now complete! To access your Openbravo instance, please point your browser to [http://ip_address/openbravo](http://ip_address/openbravo)
Procesando disparadores para ureadahead ...
ureadahead will be reprofiled on next reboot
Configurando openjdk-7-jre-lib (7u21-2.3.9-1ubuntu1) ...
Name:/home/asus#

---

### Post by narcisgarcia on 2013-08-12
My recipe to avoid that ugly error (before having any problem):

```
sudo apt-get install app-install-data-partner
sudo cp -a /usr/share/app-install/channels/$(lsb_release -c -s)-partner.list /etc/apt/sources.list.d/
sudo add-apt-repository ppa:openbravo-isv/ppa
sudo apt-get update
# If your Ubuntu version (for example Raring) is'nt in the repository, replace "raring" by "precise" in /etc/apt/sources.list.d/openbravo-isv-ppa-raring.list
sudo apt-get update
sudo apt-get install openjdk-6-jdk
LinkDir="$(ls -1 /usr/lib/jvm/ | grep -ie 'java-6-openjdk' | grep -ive '-common$' | tail --lines=1)"
if [ ! -d /usr/lib/jvm/java-6-openjdk ] ; then sudo ln -s "/usr/lib/jvm/${LinkDir}" /usr/lib/jvm/java-6-openjdk ; fi
sudo apt-get install openbravo-3
```

Note: Requires 1,5 GiB of RAM, and may eat 2GiB of disk for the preset databases.

---

