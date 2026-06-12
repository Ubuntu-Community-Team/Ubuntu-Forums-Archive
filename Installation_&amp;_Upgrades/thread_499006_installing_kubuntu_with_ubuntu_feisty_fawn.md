---
title: "installing kubuntu with ubuntu feisty fawn"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by matrunner on 2007-07-12
i have installed ubuntu and using it for past few days....read few blogs and misc thought to try kubuntu along with....got the latest version of kubuntu....

          hw to install kubuntu along with ubuntu by selecting during booting....

           also give me details of un-installing either of OS 1ce i feel 1 is beeter bcas i dont have much space left to have both....hope that uninstalling doesn affect the other os...

               MAIN INFO - i have WIN XP as multi boot.........

---

### Post by gizmoarena on 2007-07-12
the installation is easy, create another ext3 partition for kubuntu, you wont need to create another swap drive as both ubuntu and kubuntu are Linuxes. install kubuntu in the new partition. the grub is smart enough to list all your OS's.

if you are not a fan of KDE, it is pointless to install kubuntu and ubuntu at the same time.
and is it totally useless if you want to dualboot ubuntu and kubuntu. you can have them both together as one OS.

if you have a good internet connection. from ubuntu terminal, use

> sudo aptitude-update
sudo aptitude install kubuntu-desktop

---

### Post by matrunner on 2007-07-12
ok...
but installing kubuntu in same os as u gave codes...and said of good internet connection...cant i do with the same live cd avaiable with me....bcas i feel not that better to have another ext3 partition for this as said earlier have winxp too in ntfs format....

---

