---
title: "problem using apt-get"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by Gillo_ on 2012-04-14
Hi,
so I bought a new laptop last week because my old one broke down. Now I'm trying to get Ubuntu up
and running again. But I'm having this weird issue with apt. Whenever I try to install something (Dosbox,
for example) using apt-get in the terminal, my system tries to download *adobe-flashplugin_11.2.202.228.orig.tar.gz*. To do so it is trying to connect with archive.canonical.com.
Below is te output I get when I try to install Dosbox. Part of it is in dutch (I'm from Belgium) so I hope it
isn't complete jibberish.

```
Pakketlijsten worden ingelezen... Klaar
Boom van afhankelijkheden wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar  
De volgende extra pakketten zullen geïnstalleerd worden:
  libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  dosbox libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
0 pakketten opgewaardeerd, 5 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
2 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 1268 kB aan archieven opgehaald worden.
Door deze operatie zal er 3686 kB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Ophalen:1 http://be.archive.ubuntu.com/ubuntu/ oneiric/universe libsdl-net1.2 amd64 1.2.7-2 [12,1 kB]
Ophalen:2 http://be.archive.ubuntu.com/ubuntu/ oneiric/universe libmikmod2 amd64 3.1.11-a-6.4 [145 kB]
Ophalen:3 http://be.archive.ubuntu.com/ubuntu/ oneiric/universe libsmpeg0 amd64 0.4.5+cvs20030824-2.2ubuntu1 [94,4 kB]
Ophalen:4 http://be.archive.ubuntu.com/ubuntu/ oneiric/universe libsdl-sound1.2 amd64 1.0.3-3.1 [95,7 kB]
Ophalen:5 http://be.archive.ubuntu.com/ubuntu/ oneiric/universe dosbox amd64 0.74-2 [921 kB]
1268 kB opgehaald in 2s (439 kB/s)
Selecteren van voorheen niet geselecteerd pakket libsdl-net1.2.
(Database inlezen ... 181984 files and directories currently installed.)
Uitpakken van libsdl-net1.2 (uit .../libsdl-net1.2_1.2.7-2_amd64.deb) ...
Selecteren van voorheen niet geselecteerd pakket libmikmod2.
Uitpakken van libmikmod2 (uit .../libmikmod2_3.1.11-a-6.4_amd64.deb) ...
Selecteren van voorheen niet geselecteerd pakket libsmpeg0.
Uitpakken van libsmpeg0 (uit .../libsmpeg0_0.4.5+cvs20030824-2.2ubuntu1_amd64.deb) ...
Selecteren van voorheen niet geselecteerd pakket libsdl-sound1.2.
Uitpakken van libsdl-sound1.2 (uit .../libsdl-sound1.2_1.0.3-3.1_amd64.deb) ...
Selecteren van voorheen niet geselecteerd pakket dosbox.
Uitpakken van dosbox (uit .../dosbox_0.74-2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Instellen van flashplugin-installer (11.2.202.228ubuntu0.11.10.1) ...
Downloading...
--2012-04-14 17:16:23--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228.orig.tar.gz
Herleiden van archive.canonical.com... 1.0.0.0
Verbinding maken met archive.canonical.com|1.0.0.0|:80... mislukt: Verbinding is verlopen.
Nieuwe poging.

--2012-04-14 17:19:33--  (poging  2)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228.orig.tar.gz
Verbinding maken met archive.canonical.com|1.0.0.0|:80... mislukt: Verbinding is verlopen.
Pogingen worden gestaakt.

download failed
The Flash plugin is NOT installed.
dpkg: fout bij afhandelen van flashplugin-installer (--configure):
 subproces installed post-installation script gaf een foutwaarde 1 terug
Instellen van nautilus-dropbox (0.6.8-1) ...

Dropbox is the easiest way to share and store your files online. Want to learn more? Head to http://www.dropbox.com/


Error: Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable.
dpkg: fout bij afhandelen van nautilus-dropbox (--configure):
 subproces installed post-installation script gaf een foutwaarde 255 terug
Instellen van libsdl-net1.2 (1.2.7-2) ...
Instellen van libmikmod2 (3.1.11-a-6.4) ...
Instellen van libsmpeg0 (0.4.5+cvs20030824-2.2ubuntu1) ...
Instellen van libsdl-sound1.2 (1.0.3-3.1) ...
Instellen van dosbox (0.74-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Fouten gevonden tijdens behandelen van:
 flashplugin-installer
 nautilus-dropbox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```There seems to be a problem with the flashplugin-installer and nautilus-dropbox. I have been messing
around with adobe flash player, because I couldn't get it to work. Now I can watch online videos, but
this issue still remain. I also can't get Dropbox to work. It always tells me to download the proprietary daemon, but I have no
idea how I should do that.

EDIT: Dropbox now works, I tried installing it using the commands provided bij [https://www.dropbox.com/install](https://www.dropbox.com/install) and it worked!
And apparently Dosbox works just fine as well, even though I got the errors mentioned above...
EDIT2: So dropbox actually *doesn't* work. I closed the terminal where I entered the commands and the program stopped, and
the folders stopped syncing...

---

### Post by dino99 on 2012-04-14
[http://www.google.fr/#hl=fr&sclient=psy-ab&q=oneiric%2Bflash%2Bamd64&oq=oneiric%2Bflash%2Bamd64&aq=f&aqi=&aql=&gs_l=hp.3...2366l12206l0l12479l19l18l0l1l1l0l147l1020l17j1l19l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=dda3ba5ee4953ba5&biw=1387&bih=886](http://www.google.fr/#hl=fr&sclient=psy-ab&q=oneiric%2Bflash%2Bamd64&oq=oneiric%2Bflash%2Bamd64&aq=f&aqi=&aql=&gs_l=hp.3...2366l12206l0l12479l19l18l0l1l1l0l147l1020l17j1l19l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=dda3ba5ee4953ba5&biw=1387&bih=886)

---

### Post by Gillo_ on 2012-04-14
dino99, what exactly do you mean with this link?

---

### Post by Gillo_ on 2012-04-14
The errors have disappeared when I want to install new programs. After I rebooted, I was somehow able to connect to archive.canonical.com, and the flash-plugin was installed correctly when I entered *sudo apt-get* update in the terminal. The nautilus-dropbox error disappeared after I manually intalled the daemon using [http://dnasmith.com/?p=42](http://dnasmith.com/?p=42). I also downloaded some dropbox configuration files using [http://www.linuxquestions.org/questions/linux-software-2/installing-dropbox-ubuntu-9-10-a-772655/](http://www.linuxquestions.org/questions/linux-software-2/installing-dropbox-ubuntu-9-10-a-772655/). After another *sudo apt-get update*, both errors disappeared.
I hope the problem doesn't return, and that someone else ill find this thread useful :)

---

