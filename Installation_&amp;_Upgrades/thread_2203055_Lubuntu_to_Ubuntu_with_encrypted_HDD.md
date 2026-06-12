---
title: "Lubuntu to Ubuntu with encrypted HDD"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by David_Sediqui on 2014-02-01
I am running latest lubuntu but it gives me so much problems with sound and video I would like to go back to Ubuntu. I have tried with running from USB and it worked good as before. 
On lubuntu I have encrypted my HDD with the standard functionality.
I would like to change or replace lubuntu by ubuntu AND be able to use the data (all music and stuff).
Since I am travelling and not in the possesion of an external big HDD I cannot temporarily backup my stuff.
Do you have some help on which approach to follow?\
Regards and thanks a lot!
David

---

### Post by sudodus on 2014-02-03
I improve the audio management with pulseaudio and pavucontrol. That way it is not necessary to migrate to a completely new desktop.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pulseaudio
sudo apt-get install pavucontrol

```
But if you want to migrate anyway, the easy way is to install the desktop either by

```
sudo apt-get install unity
```

or (to get the whole meta-package with all packages that belong to Ubuntu)

```
sudo apt-get install ubuntu-desktop
```

A disadvantage is that there with be doublets of software for example for editing, word processing, finding software ... but if there is plenty of free space on the HDD, it is no problem.

You select desktop environment 'session' at the login screen, and you can revert back to Lubuntu if you wish, but now with better audio control (I think and hope so).

---

