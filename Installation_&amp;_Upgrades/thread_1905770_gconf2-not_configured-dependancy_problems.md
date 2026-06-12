---
title: "gconf2-not configured-dependancy problems"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by gabx666 on 2012-01-07
Hello,

I have lots of depency problems and can't install some new app because I always get an error message complaining about gconf2 not yet configured.

> gabx@magnolia:~/Bureau$ apt-cache policy gconf2
gconf2:
  Installé*: 3.2.3-0ubuntu0.1
  Candidat*: 3.2.3-0ubuntu0.1
 Table de version*:
 *** 3.2.3-0ubuntu0.1 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) oneiric-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.2.0-0ubuntu1 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages

> gabx@magnolia:~/Bureau$ sudo dpkg-reconfigure gconf2
[sudo] password for gabx: 
/usr/sbin/dpkg-reconfigure: gconf2 est cassé ou partiellement installé

Above last line means gconf2 is broken or partially installed
This problem is quite new, and came after either an upgrade or an install.

I tried to reinstall, but didn't change. I already tried a ** $ apt-get purge remove && install**, but it didn't change.

How can I get rid of this issue? Can I simply remove gconf2 ? If i do, it will remove many other programs too!

TY for any help

---

### Post by zvacet on 2012-01-07
```
sudo apt-get -f install
```

or

```
sudo dpkg --configure -a
```

---

### Post by gabx666 on 2012-01-07
both commands list lots of error, then[b]dpkg: too many errors, stopping
[/b]    
 > gabx@magnolia:~/Bureau$ sudo dpkg --configure -a
Paramétrage de gconf2 (3.2.3-0ubuntu0.1) ...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: gconf_schema_set_gettext_domain
dpkg*: erreur de traitement de gconf2 (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 127

Then a whole list of apps not configured because of dependance problems.

Tried this too :

Loged out X, then CTRL+ALT+F1,then login 

> sudo apt-get --reinstall install gconf2 libgconf2-4 gconf2-common

dpkg stopped with too many errors

---

### Post by gabx666 on 2012-01-07
> **zvacet said:**
> ```
sudo apt-get -f install
```

or

```
sudo dpkg --configure -a
```

1- Removed manually one by one many unwanted app
2- > $ sudo apt-get autoremove to remove obsolete packets

Now :

> gabx@magnolia:~/Bureau$ sudo dpkg --configure -a
gabx@magnolia:~/Bureau$ sudo apt-get -f install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 7 non mis à jour.
gabx@magnolia:~/Bureau$



Removed gconf2 and gconf-editor.

Built and installed gconf2 from source, but when installed gconf-editor, got an error with gconf2 again:

> Traitement des actions différées («*triggers*») pour «*gconf2*»...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: gconf_schema_set_gettext_domain
dpkg*: erreur de traitement de gconf2 (--unpack)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 127

When installing another package, got again an error :

> gabx@magnolia:/usr/lib/jvm$ sudo apt-get install update-java
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet suivant a été installé automatiquement et n'est plus nécessaire*:
  python-wnck
Veuillez utiliser «*apt-get autoremove*» pour les supprimer.
Les paquets supplémentaires suivants seront installés*: 
  gksu libgksu2-0
Les NOUVEAUX paquets suivants seront installés*:
  gksu libgksu2-0 update-java
0 mis à jour, 3 nouvellement installés, 0 à enlever et 8 non mis à jour.
Il est nécessaire de prendre 79.2 ko dans les archives.
Après cette opération, 492 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? o
Réception de*: 1 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) oneiric/main libgksu2-0 amd64 2.0.13~pre1-4ubuntu2 [47.7 kB]
Réception de*: 2 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) oneiric/main update-java all 0.5-2~webupd8 [3'960 B]
Réception de*: 3 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) oneiric/main gksu amd64 2.0.2-5ubuntu2 [27.6 kB]
79.2 ko réceptionnés en 0s (341 ko/s)
Sélection du paquet libgksu2-0 précédemment désélectionné.
(Lecture de la base de données... 310608 fichiers et répertoires déjà installés.)
Dépaquetage de libgksu2-0 (à partir de .../libgksu2-0_2.0.13~pre1-4ubuntu2_amd64.deb) ...
Sélection du paquet gksu précédemment désélectionné.
Dépaquetage de gksu (à partir de .../gksu_2.0.2-5ubuntu2_amd64.deb) ...
Sélection du paquet update-java précédemment désélectionné.
Dépaquetage de update-java (à partir de .../update-java_0.5-2~webupd8_all.deb) ...
Traitement des actions différées («*triggers*») pour «*gconf2*»...
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: gconf_schema_set_gettext_domain
dpkg*: erreur de traitement de gconf2 (--unpack)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 127
Traitement des actions différées («*triggers*») pour «*man-db*»...
Traitement des actions différées («*triggers*») pour «*menu*»...
Traitement des actions différées («*triggers*») pour «*bamfdaemon*»...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées («*triggers*») pour «*desktop-file-utils*»...
Traitement des actions différées («*triggers*») pour «*gnome-menus*»...
Des erreurs ont été rencontrées pendant l'exécution*:
 gconf2
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I get rid of this issue? Can I remove gconf2??

**EDIT**
It seems my problem comes from I am running XFce, not Gnome. So, each time I need install a gnome app, gconf complains.

---

