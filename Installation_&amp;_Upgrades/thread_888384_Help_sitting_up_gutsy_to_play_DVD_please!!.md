---
title: "Help sitting up gutsy to play DVD please!!"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by KEE on 2008-08-13
i did a new ubuntu install and i cant get restricted content to get DVD to work =/ 
hers what i remember 

$sudo apt-get install restricted-extras

$[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)



$sudo dpkg --configure -a

dosent work any more? has some thing changed?

---

### Post by mc4man on 2008-08-13
Totem's not a very good player for dvds anyway -  do this
go here and run the line for gutsy, then run the GPG Key line. If the key line errors don't worry, just type y whenever prompted.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then run ```
sudo aptitude install libdvdcss2 vlc
```
After that go System -> preferences -> removable drives and media -> multimedia  and change the line in Video Dvd disks to 
```
vlc %m
```
Then try a dvd

---

### Post by ibutho on 2008-08-13
The pacage you should install it ubuntu-restricted-extras. More information is available [here]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by pietjanjaap on 2008-08-13
After a fresh install you need to install codecs etc.
See the list of site's ther is a manual how to do this.



Search forums, ubuntu howto sites etc.


[http://computertip.googlepages.com/ubuntulinux](http://computertip.googlepages.com/ubuntulinux)
[http://onlyubuntu.blogspot.com/](http://onlyubuntu.blogspot.com/)
[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.debuntu.org/how-to-instal...lvm-filesystem](http://www.debuntu.org/how-to-instal...lvm-filesystem)




[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

the best:
[http://damen.dommel.be/Ubuntu.html](http://damen.dommel.be/Ubuntu.html)

the gimp        - very good photoshop
gfslicer        - splitter joiner
Q7z+7z          - archiver
hellanzb        - downloaden nzb van usenet
kget            - download program
Inkscape Vector Graphics Editor
Klibido         - to look in usenet groups and nzb download
dvdfab in wine  - the only thing i can't find in linux.
quickpar in wine
k3b writing/burning dvd's
gmount iso       - to mount iso file
KNetLoad Network Monitor - you network activity in a grafic

---

### Post by KEE on 2008-08-13
big thanks =D

---

