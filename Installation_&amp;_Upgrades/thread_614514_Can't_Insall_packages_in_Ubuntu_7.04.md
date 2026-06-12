---
title: "Can't Insall packages in Ubuntu 7.04"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by AneeshAN on 2007-11-16
I  tried to install some packages( banshee,audacity) on ubuntu 7.04  which are downloaded from ubuntu's website  ( in *.tar.gz and  *.deb versions) ,while installing .tar.gz file in Terminal  ( as root) I got some error messages that FILE  PERMISSIONS ARE NOT  OK  and  i got ERROR  " DEPENDENCIES  ARE NOT  SATISFACTORY "  while installing  the .deb files   

!!!!!!!!! HELP   ME  !!!!!!!!   to install these files  ( I didn't have a Internet connection )

---

### Post by K.Mandla on 2007-11-16
> **AneeshAN said:**
> I  tried to install some packages( banshee,audacity) on ubuntu 7.04  which are downloaded from ubuntu's website  ( in *.tar.gz and  *.deb versions) ,while installing .tar.gz file in Terminal  ( as root) I got some error messages that FILE  PERMISSIONS ARE NOT  OK  and  i got ERROR  " DEPENDENCIES  ARE NOT  SATISFACTORY "  while installing  the .deb files   

!!!!!!!!! HELP   ME  !!!!!!!!   to install these files  ( I didn't have a Internet connection )
Ah, if you don't have an Internet connection, this is going to be a real trick. The debs are failing because there are dependencies that have to be satisfied before the package can be installed. 

Is there any way you can connect that machine to the Internet, even for a short time?

---

