---
title: "No aparece opción instalar junto a Windows 10"
date: 2019-08-19
forum: Installation &amp; Upgrades
---

### Post by cataplov on 2019-08-19
Estoy intentando instalar Ubuntu y tanto en la instalación de Ubuntu 19 como 18 al llegar a la opción de instalar, reconoce que está instalado Windows 10, pero solamente muestra opción borrar para instalar sobre Windows.
En una ocasión apareció la posibilidad de instalarlo junto a Windows, pero ya no. 
¿Alguna idea de cómo hacer para que permita instalarlo junto a Windows 10?

---

### Post by slickymaster on 2019-08-19
> **cataplov said:**
> Estoy intentando instalar Ubuntu y tanto en la instalación de Ubuntu 19 como 18 al llegar a la opción de instalar, reconoce que está instalado Windows 10, pero solamente muestra opción borrar para instalar sobre Windows.
En una ocasión apareció la posibilidad de instalarlo junto a Windows, pero ya no. 
¿Alguna idea de cómo hacer para que permita instalarlo junto a Windows 10?
Hi cataplov, welcome to the forums. Please keep in mind that this is a English so please write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.

Here's your original post translated by Google Translate. Sorry if it isn't 100% accurate> I am trying to install Ubuntu and in both the installation of Ubuntu 19 and 18 when arriving at the option to install, it recognizes that Windows 10 is installed, but it only shows delete option to install on Windows.
On one occasion the possibility of installing it with Windows appeared, but not anymore.
Any idea how to make it possible to install it with Windows 10?

---

### Post by yancek on 2019-08-20
Boot into windows 10 and turn off fastboot and anything related to hibernation.  Then go into windows Disk Management tool and shrink the largest windows partition to create unallocated space on which to install window.  Don't create any partition in windows.  Boot the Ubuntu DVD/USB and try again and post back if you have problems.

---

