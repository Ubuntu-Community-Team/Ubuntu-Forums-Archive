---
title: "Problems after upgrating from 16.10 to 17.04"
date: 2017-06-16
forum: Installation &amp; Upgrades
---

### Post by alejandrofig on 2017-06-16
Hello , today i Upgrated to 17.04 and the error Broken count >0 appeared. I can't also install upgrades with the terminal or update the software with the software update manager (I don't know if it is called like that, I am translating from italian). The update manager tells me that some packages are broken and to try to run sudo apt-get install -f from terminal. I have tried that with no result, I also tried sudo apt-get install --fix-broken, but nothing. what i got was:
alejandro@alejandro-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get install --fix-broken
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  account-plugin-tools account-plugin-ubuntuone cgmanager checkbox-gui
  dns-root-data dnsmasq-base espeak-data fonts-stix hwdata imagemagick-common
  libbluray1 libboost-date-time1.61.0 libboost-iostreams1.61.0
  libboost-locale1.61.0 libboost-log1.61.0 libboost-program-options1.61.0
  libboost-regex1.61.0 libboost-serialization1.62.0 libboost-thread1.61.0
  libbsd0:i386 libchromaprint0 libcolamd2 libespeak1 libglew1.13
  libjson-c3:i386 libjsoncpp1 libkf5gpgmepp5 liblircclient0 liblivemedia52
  libllvm3.8 libllvm3.8:i386 liblouis10 libmimic0 libmircommon6
  libmirplatform13 libmirserver41 libopencv-contrib2.4v5 libopencv-legacy2.4v5
  libopencv-ml2.4v5 libopenjpeg5 liborcus-0.11-0 libpam-cgfs libpay2
  libperl5.22 libpoppler61 libraw15 libschroedinger-1.0-0
  libsuitesparseconfig4 libubuntu-app-launch3 libubuntuoneauth-2.0-0 libvpx3
  libx265-79 libxapian22v5 libxcb-composite0 linux-headers-4.8.0-53
  linux-headers-4.8.0-53-generic linux-image-4.8.0-53-generic
  linux-image-extra-4.8.0-53-generic linux-signed-image-4.8.0-53-generic
  lp-solve mir-platform-graphics-mesa-kms10 mir-platform-graphics-mesa-x10
  mir-platform-input-evdev5 pay-service pay-ui perl-modules-5.22 pm-utils
  pyotherside qml-module-ubuntuone qtdeclarative5-ubuntu-web-plugin
  signon-plugin-password system-config-printer-gnome ubuntu-push-client
  ubuntuone-client-data ubuntuone-credentials-common unity-scope-click vbetool
  vlc-nox
Usare "sudo apt autoremove" per rimuoverli.
The following additional packages will be installed:
  click-apparmor ubuntu-app-launch url-dispatcher
I seguenti pacchetti saranno aggiornati:
  click-apparmor ubuntu-app-launch url-dispatcher
3 aggiornati, 0 installati, 0 da rimuovere e 2 non aggiornati.
30 non completamente installati o rimossi.
È necessario scaricare 0 B/71,9 kB di archivi.
Dopo quest'operazione, verranno liberati 80,9 kB di spazio su disco.
Continuare? [S/n] s
(Lettura del database... 260017 file e directory attualmente installati.)
Preparativi per estrarre .../ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: attenzione: il sottoprocesso vecchio script di pre-removal ha restituito lo stato di errore 1
dpkg: viene provato lo script dal nuovo pacchetto...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb (--unpack):
 non c'è alcuno script nella nuova versione del pacchetto - saltato
Preparativi per estrarre .../url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: attenzione: il sottoprocesso vecchio script di pre-removal ha restituito lo stato di errore 1
dpkg: viene provato lo script dal nuovo pacchetto...
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb (--unpack):
 non c'è alcuno script nella nuova versione del pacchetto - saltato
Preparativi per estrarre .../click-apparmor_0.3.18_amd64.deb...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: attenzione: il sottoprocesso vecchio script di pre-removal ha restituito lo stato di errore 1
dpkg: viene provato lo script dal nuovo pacchetto...
Cannot start click due to a conflict with a different locally-installed Python 'click' package.  Remove it using Python packaging tools and try again.
dpkg: errore nell'elaborare l'archivio /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb (--unpack):
 il sottoprocesso nuovo script pre-removal ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/ubuntu-app-launch_0.12+17.04.20170404.2-0ubuntu2_amd64.deb
 /var/cache/apt/archives/url-dispatcher_0.1+17.04.20170328-0ubuntu2_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone got any idea?
Thanks

---

### Post by alejandrofig on 2017-06-16
I have also tried disabling third party software with no luck

---

### Post by alejandrofig on 2017-06-16
Ok, after further investigation I followed this tutorial and the problem seems to be fixed [https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04](https://askubuntu.com/questions/904952/the-package-system-is-broken-after-upgraded-to-ubuntu-17-04)

---

### Post by alejandrofig on 2017-06-16
The problem wasn't fixed, but now I know that the problem is the package click-apparmor, I tried to fixed it with synaptic, and to remove it or to update it, I also tried downloading manually the new version and install it, but i can't. Any ideas?

---

### Post by alejandrofig on 2017-06-16
Me again, Now it seems that I have installed the new version of click-apparmor, but it was correctly install, so I tried to reinstall it with synaptic and the following error came up : E: Internal Error, No file name for click-apparmor:amd64. Also when I run the comand sudo apt-get upgrade I get: 
alejandro@alejandro-HP-Pavilion-15-Notebook-PC:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
1 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Continuare? [S/n] s
Configurazione di click-apparmor (0.3.18)...
Traceback (most recent call last):
  File "/usr/bin/click", line 32, in <module>
    gi.require_version('Click', '0.4')
  File "/usr/lib/python3/dist-packages/gi/__init__.py", line 118, in require_version
    raise ValueError('Namespace %s not available' % namespace)
ValueError: Namespace Click not available
dpkg: errore nell'elaborare il pacchetto click-apparmor (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
Si sono verificati degli errori nell'elaborazione:
 click-apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)


I hope some of you will have any idea of what to do. Thanks

---

### Post by alejandrofig on 2017-06-17
I have solve everything following this :
[https://ubuntuforums.org/showthread.php?t=2358899](https://ubuntuforums.org/showthread.php?t=2358899)

---

