---
title: "I can't install-reinstall-update-remove ANY packages!"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by kr0n1x on 2007-07-02
Hi, i've a BIG problem with Synaptic and APT...

When i try to upgrade my pc (Ubuntu Feisty) i've this error:
(sudo apt-get update, and this is ok, but when i try sudo apt-get upgrade...)
```
pasquale@pasquale-desktop:~$ sudo apt-get upgrade
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
I seguenti pacchetti sono stati mantenuti alla versione attuale:
  libfaad2-0 rhythmbox
I seguenti pacchetti saranno aggiornati:
  amsn compiz compiz-core compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-fusion-plugins-unsupported compiz-gnome
  compiz-kde compiz-plugins compizconfig-settings-manager
  libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 libexif-dev
  libexif12 libkadm55 libkrb5-dev libkrb53 libnautilus-burn-dev
  libnautilus-burn4 linux-restricted-modules-2.6.20-16-generic
  linux-restricted-modules-common music-applet nautilus-cd-burner
  nvidia-kernel-source python-compizconfig wine
27 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.
1 non completamente installati o rimossi.
È necessario prendere 0B/39,9MB di archivi. 
Dopo l'estrazione, verranno occupati 976kB di spazio su disco.
Continuare [S/n]? s
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  evince music-applet wine
Installare questi pacchetti senza la verifica [s/N]? s
(Lettura del database ... dpkg: errore processando /var/cache/apt/archives/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb (--unpack):
 files list file for package `libcompizconfig0' is missing final newline
Sono occorsi degli errori processando:
 /var/cache/apt/archives/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb
L'operazione è stata bloccata perché si sono verificati troppi errori.
E: Sub-process /usr/bin/dpkg returned an error code (1)
pasquale@pasquale-desktop:~$ 

```

i tried also delete files/packages in cache...with sudo apt-get clean and autoclean...and APT re-download all packages for update...but it give me forever the same error :/

a my friend sent me the packages Evince...because he haven't any problem with the same repositoty...

ONLY I've the problem :( when i try to install the .deb file...i receive:

```
pasquale@pasquale-desktop:~$ sudo dpkg -i Desktop/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb 
(Lettura del database ... dpkg: errore processando Desktop/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb (--install):
 files list file for package `libcompizconfig0' is missing final newline
Sono occorsi degli errori processando:
 Desktop/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb
L'operazione è stata bloccata perché si sono verificati troppi errori.
pasquale@pasquale-desktop:~$
```

more info at this thread (Italian): [http://forum.ubuntu-it.org/index.php?topic=99189.0](http://forum.ubuntu-it.org/index.php?topic=99189.0)

i can't update anything :(

help me please...the problem is serious...i can't update, install, reinstall, remove ANY packages!

---

### Post by kr0n1x on 2007-07-02
help me please if anyone has an idea!:(

i can't do anithing with my pc :(

---

### Post by kr0n1x on 2007-07-03
up

---

### Post by dabl on 2007-07-03
Try ```
sudo dpkg --configure -a

```
```
then sudo apt-get autoclean
```

```
then sudo apt-get autoremove
```

After that, you should be able to resume installing or removing with Adept or Synaptic (whichever you normally use.)

HTH  :)

---

### Post by kr0n1x on 2007-07-03
> **dabl said:**
> Try ```
sudo dpkg --configure -a

```
```
then sudo apt-get autoclean
```

```
then sudo apt-get autoremove
```

After that, you should be able to resume installing or removing with Adept or Synaptic (whichever you normally use.)

HTH  :)

```
pasquale@pasquale-desktop:~$ sudo dpkg --configure -a
Password:
dpkg: errore processando evince (--configure):
 Il pacchetto si trova in uno stato di inconsistenza grave - dovresti
 reinstallarlo prima di tentare la configurazione.
Sono occorsi degli errori processando:
 evince
pasquale@pasquale-desktop:~$
```

and next:
```
pasquale@pasquale-desktop:~$ sudo apt-get autoclean
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
Del libdecoration0 1:0.5.1+git20070629~3v1ubuntu2 [45,1kB]
Del compiz-plugins 1:0.5.1+git20070629~3v1ubuntu2 [279kB]
Del compiz-kde 1:0.5.1+git20070629~3v1ubuntu2 [85,2kB]
Del compiz-core 1:0.5.1+git20070629~3v1ubuntu2 [456kB]
Del compiz-gnome 1:0.5.1+git20070629~3v1ubuntu2 [165kB]
Del compiz 1:0.5.1+git20070629~3v1ubuntu2 [28,5kB]
Del compiz-fusion-plugins-main 0.0.1+git20070702~3v1ubuntu0 [193kB]
Del compiz-fusion-plugins-extra 0.0.1+git20070702~3v1ubuntu0 [158kB]
Del compiz-fusion-plugins-unsupported 0.0.1+git20070702~3v1ubuntu0 [28,5kB]
Del compizconfig-settings-manager 0.1.0+git20070702~3v1ubuntu0 [445kB]
pasquale@pasquale-desktop:~$ sudo apt-get autoremove
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
I seguenti pacchetti sono stati installati automaticamente in precedenza e ora non sono più necessari:
  libboost-regex1.33.1 libtwolame0 libattr1-dev kdelibs4-dev python2.4-dev
  kdeprint libaspell-dev libavahi-compat-libdnssd1 libmpeg3hv libswfdec0.3
  libboost-program-options1.33.1 comerr-dev libsvga1 fftw3 libpcre3-dev
  gnome-cards-data libburn2 konqueror-nsplugins liblualib50-dev klipper
  libcompizconfig-backend-gconf librte1 ksmserver ntp-simple libkrb5-dev
  libsasl2-dev libogg-dev libjasper-1.701-dev kmenuedit libguicast libpcrecpp0
  ksplash liblua50-dev lua50 libavahi-qt3-dev libacl1-dev hspell libxslt1-dev
  libssl-dev poster ntp libtiff4-dev libntlm0 khelpcenter libtiffxx0c2
  libquicktimehv libkadm55 libopenexr-dev libisofs2 kate libntfs-3g0
  kdesdk-scripts libvorbis-dev gettext-kde libidn11-dev libarts1-dev
I seguenti pacchetti saranno RIMOSSI:
  comerr-dev fftw3 gettext-kde gnome-cards-data hspell kate kdelibs4-dev
  kdeprint kdesdk-scripts khelpcenter klipper kmenuedit konqueror-nsplugins
  ksmserver ksplash libacl1-dev libarts1-dev libaspell-dev libattr1-dev
  libavahi-compat-libdnssd1 libavahi-qt3-dev libboost-program-options1.33.1
  libboost-regex1.33.1 libburn2 libcompizconfig-backend-gconf libguicast
  libidn11-dev libisofs2 libjasper-1.701-dev libkadm55 libkrb5-dev
  liblua50-dev liblualib50-dev libmpeg3hv libntfs-3g0 libntlm0 libogg-dev
  libopenexr-dev libpcre3-dev libpcrecpp0 libquicktimehv librte1 libsasl2-dev
  libssl-dev libsvga1 libswfdec0.3 libtiff4-dev libtiffxx0c2 libtwolame0
  libvorbis-dev libxslt1-dev lua50 ntp ntp-simple poster python2.4-dev
0 aggiornati, 0 installati, 56 da rimuovere e 26 non aggiornati.
1 non completamente installati o rimossi.
È necessario prendere 0B/1687kB di archivi. 
Dopo l'estrazione, verranno liberati 81,4MB di spazio su disco.
Continuare [S/n]? s
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  evince
Installare questi pacchetti senza la verifica [s/N]? s
(Lettura del database ... dpkg: errore processando /var/cache/apt/archives/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb (--unpack):
 files list file for package `libcompizconfig0' is missing final newline
Sono occorsi degli errori processando:
 /var/cache/apt/archives/evince_0.9.1-0ubuntu1~pollycoke3-really0.8.1_i386.deb
L'operazione è stata bloccata perché si sono verificati troppi errori.
E: Sub-process /usr/bin/dpkg returned an error code (1)
pasquale@pasquale-desktop:~$ 

```

---

### Post by kr0n1x on 2007-07-16
any update?

---

### Post by mykii on 2008-02-10
Hi,

I have the same problem but it seems to be a problem with some HP libs and i dont know how to fix this problem :
```

Extraction des modèles depuis les paquets : 100%
Préconfiguration des paquets...
(Lecture de la base de données... dpkg : erreur de traitement de /var/cache/apt/archives/hplip_2.7.12-0ubuntu2~gutsy1_amd64.deb (--unpack) :
 files list file for package `libidn11' is missing final newline
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/hplip_2.7.12-0ubuntu2~gutsy1_amd64.deb
L'exécution a été arrêtée car il y avait trop d'erreurs.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2008-02-10
Try what is suggested in the 3rd post of [this thread]("http://ubuntuforums.org/showthread.php?t=214805")

---

### Post by mykii on 2008-02-10
No it wont work and i think i have losted my dpkg database because now it won't remove some packages.. is there a way to rebuild existing packages ?

---

### Post by mykii on 2008-02-10
Other debugging information when i tried apt-get autoclean :
```

(Lecture de la base de données... dpkg : erreur de traitement de gjdoc (--remove) :
 files list file for package `libidn11' is missing final newline
dpkg: ../../src/packages.c:252: process_queue:  l'assertion « !queuelen » a échoué.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I had this error before.

---

### Post by kr0n1x on 2008-02-10
i "solved" formatting my OS... and reinstalling it :(
from that time, i didn't add 10491024 repositories automatically...
now i have 2-3 3rdy part repos maximum.

good luck

---

### Post by mykii on 2008-02-10
Which package has disturbed my OS. I wont reinstall it !

---

