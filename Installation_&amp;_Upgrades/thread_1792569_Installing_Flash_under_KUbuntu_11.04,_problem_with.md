---
title: "Installing Flash under KUbuntu 11.04, problem with nspluginwrapper"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by etienoo on 2011-06-28
Hi,


I'm trying to install flash (32 bits version) on KUbuntu 11.04 64 bits on a MacBook Pro 6.02.
I followed the procedure described on the [French official Ubuntu page]("http://doc.ubuntu-fr.org/flashplayer") (in French, oops…).


In particular, I typed:

```
sudo apt-get install flashplugin-installer
```But then I got the following error:

```
sudo apt-get install flashplugin-installer

Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances        Lecture des informations d'état...
Fait Les paquets supplémentaires suivants seront installés : 
   nspluginwrapper
Paquets suggérés :
   xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
Les NOUVEAUX paquets suivants seront installés :
   flashplugin-installer nspluginwrapper
0 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/185 ko dans les archives.
Après cette opération, 770 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
Préconfiguration des paquets...
Sélection du paquet nspluginwrapper précédemment désélectionné.
(Lecture de la base de données... 160984 fichiers et répertoires déjà installés.)
Dépaquetage de nspluginwrapper (à partir de .../nspluginwrapper_1.2.2-0ubuntu9_amd64.deb) ...
Sélection du paquet flashplugin-installer précédemment désélectionné.
Dépaquetage de flashplugin-installer (à partir de .../flashplugin-installer_10.3.181.14ubuntu0.11.04.1_amd64.deb) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de nspluginwrapper (1.2.2-0ubuntu9) ...
plugin dirs: :/var/lib/flashplugin-installer/
Auto-update plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
Segmentation fault
dpkg : erreur de traitement de nspluginwrapper (--configure) : 
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 139
dpkg : des problèmes de dépendances empêchent la configuration de flashplugin-installer : 
flashplugin-installer dépend de nspluginwrapper (>= 0.9.91.4-2ubuntu1) ; cependant :  
Le paquet nspluginwrapper n'est pas encore configuré.
 dpkg : erreur de traitement de flashplugin-installer (--configure) :
  problèmes de dépendances - laissé non configuré
 Aucun rapport « apport » n'a été créé car le message d'erreur indique une erreur consécutive à un échec précédent.
                                                                                                                   Des erreurs ont été rencontrées pendant l'exécution :
  nspluginwrapper
  flashplugin-installer
 E: Sub-process /usr/bin/dpkg returned an error code (1)
```It's in French (I did not chose my terminal to be in French… just the system), but basically, the end says:

```
treatment error of nspluginwrapper (--configure) :
the subprocess post installing script returned a return state error 139
dpkg: dependencies problems prevent the configuration of flashplugin-installer
  flashplugin-installer depends from nspluginwrapper (>= 0.9.91.4-2ubuntu1) ; however :  
 the packet nspluginwrapper has not been configured yet.
dpkg : treatment error of flashplugin-installer (--configure) :
  dependencies problems - left unconfigured
No report « apport » has been create because the error message indicates an error following a previous failure.
```I tried again after purge, i.e.:
```
sudo apt-get purge nspluginwrapper
sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-installer
```But the error that follows is the same. Any suggestion…?

---

### Post by An Sanct on 2011-06-28
If you are using Firefox, try [Flash Aid]("http://www.webgapps.org/add-ons/flash-aid")&#8230;

---

### Post by etienoo on 2011-06-28
Wow, thank you :-|

Was trying to solve the problems for 3 weeks :(

---

### Post by collisionystm on 2011-06-28
Make sure to use the Adobe Labs test version with Flash AID. There are known issues with using a 32bit flash inside of a 64 bit install. I.E. You might not be able to control youtube videos

---

### Post by etienoo on 2011-06-28
I used the wizard option, and I got Adobe Flash in 64 bits.

I tried the most useful websites (youtube, dailymotion, etc.) and it looks to work fine!

Thanks.

---

### Post by lovinglinux on 2011-06-28
> **collisionystm said:**
> Make sure to use the Adobe Labs test version with Flash AID. There are known issues with using a 32bit flash inside of a 64 bit install. I.E. You might not be able to control youtube videos

Flash-Aid also applies a tweak, if necessary, to deal with the issue of not being able to use the controls in the 32bit version with the 64bit wrapper. But the 64bit works better anyway.

---

### Post by collisionystm on 2011-06-28
> **lovinglinux said:**
> Flash-Aid also applies a tweak, if necessary, to deal with the issue of not being able to use the controls in the 32bit version with the 64bit wrapper. But the 64bit works better anyway.

Nice! You created a great addon! Thanks !

---

### Post by lovinglinux on 2011-06-28
> **collisionystm said:**
> Nice! You created a great addon! Thanks !

Thanks and welcome.

---

