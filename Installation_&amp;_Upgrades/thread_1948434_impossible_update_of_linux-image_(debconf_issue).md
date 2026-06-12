---
title: "impossible update of linux-image (debconf issue?)"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by Eusebiusfr on 2012-03-28
Hi,

I'm on 11.10, gnome-session-fallback.

This morning, following my daily upgrade, I got an error on the package "linux-image-3.0.0-17-generic", which triggers dependency errors with about any other packets (I'm currently unable to upgrade or install anything).

This is the output of **apt-get -f install** (sorry, my locale is French and because of this issue I'm unable to switch locales properly) :

```
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Correction des dépendances... Fait
Les paquets supplémentaires suivants seront installés : 
  linux-image-3.0.0-17-generic
Paquets suggérés :
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
Les NOUVEAUX paquets suivants seront installés :
  linux-image-3.0.0-17-generic
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
3 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/37,0 Mo dans les archives.
Après cette opération, 153 Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? O
Use of uninitialized value $text in substitution (s///) at /usr/share/perl5/Debconf/Config.pm line 30.
Use of uninitialized value $text in split at /usr/share/perl5/Debconf/Config.pm line 34.
debconf: Le fichier de configuration n'indique pas l'emplacement de la base de données des réglages.
(Lecture de la base de données... 212384 fichiers et répertoires déjà installés.)
Dépaquetage de linux-image-3.0.0-17-generic (à partir de .../linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb) ...
Use of uninitialized value $text in substitution (s///) at /usr/share/perl5/Debconf/Config.pm line 30.
Use of uninitialized value $text in split at /usr/share/perl5/Debconf/Config.pm line 34.
debconf: Le fichier de configuration n'indique pas l'emplacement de la base de données des réglages.
dpkg : erreur de traitement de /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb (--unpack) :
 le sous-processus nouveau script pre-installation a retourné une erreur de sortie d'état 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```I guess the key part is:
```

Use of uninitialized value $text in substitution (s///) at /usr/share/perl5/Debconf/Config.pm line 30.
Use of uninitialized value $text in split at /usr/share/perl5/Debconf/Config.pm line 34.
debconf: Le fichier de configuration n'indique pas l'emplacement de la base de données des réglages.

```Output of **dpkg --configure -a** :
```

dpkg : des problèmes de dépendances empêchent la configuration de linux-image-generic :
 linux-image-generic dépend de linux-image-3.0.0-17-generic ; cependant :
  Le paquet linux-image-3.0.0-17-generic n'est pas installé.
dpkg : erreur de traitement de linux-image-generic (--configure) :
 problèmes de dépendances - laissé non configuré
dpkg : des problèmes de dépendances empêchent la configuration de linux-generic :
 linux-generic dépend de linux-image-generic (= 3.0.0.17.20) ; cependant :
 Le paquet linux-image-generic n'est pas encore configuré.
dpkg : erreur de traitement de linux-generic (--configure) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 linux-image-generic
 linux-generic

```Any help would be much appreciated, I'm currently lost.

---

### Post by raja.genupula on 2012-03-28
hmm i am getting problem partially , please post the things in english , i will try to give my best to help you . 

Thank you .

---

### Post by Eusebiusfr on 2012-03-28
> **raja.genupula said:**
> hmm i am getting problem partially , please post the things in english , i will try to give my best to help you . 

Thank you .
I can provide a summary, not a full translation... In the **apt-get -f install**, the issue seems to be around:
```

Use of uninitialized value $text in substitution (s///) at /usr/share/perl5/Debconf/Config.pm line 30.
Use of uninitialized value $text in split at /usr/share/perl5/Debconf/Config.pm line 34.
[translated] debconf: The configuration file does not indicate the location of the settings database.

```Afterwards, dpkg fails unpacking /var/cache/apt/archives/linux-image-3.0.0-17-generic_3.0.0-17.30_amd64.deb because the pre-installation scripts returns an exit value of 1.

**dpkg --configure -a** basically says that linux-image-3.0.0-17-generic is not installed, therefore linux-image-generic and linux-generic cannot be configured because of the dependency.

I hope it's better.

---

### Post by raja.genupula on 2012-03-28
[http://www.sendspace.com/file/hw2ulb](http://www.sendspace.com/file/hw2ulb)

my file is there in that location ,

after downloading that

do as ```
sudo nautilus
```
then go this location /usr/share/perl5/Debconf/

then delete your config.pm and place my file there and try again .

all the best .

---

### Post by Eusebiusfr on 2012-03-28
> **raja.genupula said:**
> then delete your config.pm and place my file there and try again .
Thanks, but in the meantime I've tried something else and it seemed to work:
My /etc/debconf.conf was empty, I made a copy from /usr/share/debconf/debconf.conf, afterwards apt-get was able to install the package properly.

I've rebooted on the new kernel, everything seems fine and my computer hasn't exploded. However, if someone thinks I've done something nasty (I've no idea how debconf works), please tell me...

Thanks for your help anyway.

---

### Post by raja.genupula on 2012-03-28
actually i am waiting for your reply , to delete that file from database of that site .

---

### Post by Eusebiusfr on 2012-03-28
> **raja.genupula said:**
> actually i am waiting for your reply , to delete that file from database of that site .
You can delete it, thanks.

---

