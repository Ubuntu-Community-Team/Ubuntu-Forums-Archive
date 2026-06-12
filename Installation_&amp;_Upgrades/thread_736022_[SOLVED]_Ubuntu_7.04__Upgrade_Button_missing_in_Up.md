---
title: "[SOLVED] Ubuntu 7.04 : Upgrade Button missing in Update Manager"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by freak42 on 2008-03-26
Hello,

I wanted to upgrade to 7.10, did backup my home and etc folders, however afterwards the button in the update-manger to upgrade my 7.04 distribution was not there anymore. 

Using apt-get i get the following response:
> $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


My sources.lst currently contains (commented lines removed):
> 

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty main restricted
deb-src [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty universe

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty multiverse

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-security main restricted
deb-src [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-security restricted main multiverse universe 

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-security universe
deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-security multiverse
deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) feisty-updates restricted main multiverse universe


Has someone an idea how i can upgrade to 7.10?

Many thanks in advance

---

### Post by lswest on 2008-03-26
try running ```
gksudo update-manager -d
``` (i think that's the command to check for new releases) but i'm not in linux atm, so i can't check.

---

### Post by freak42 on 2008-03-26
Thank you! 
That solved my problem and I started the process of upgrading.

I wonder how the button got lost though...

Thanks again

Matthias

---

### Post by DJ_Peng on 2008-03-26
Without specifically using the -d flag the upgrade to Hardy won't be offered until it gets officially released at the end of next month. Thus no upgrade button.

---

### Post by lswest on 2008-03-26
he was upgrading from Feisty to Gutsy.

---

### Post by DJ_Peng on 2008-03-26
Ah, sorry. I missed that. Thanks for the correction.

---

### Post by lswest on 2008-03-28
Haha, no problem, i missed that the first time too ;)

---

