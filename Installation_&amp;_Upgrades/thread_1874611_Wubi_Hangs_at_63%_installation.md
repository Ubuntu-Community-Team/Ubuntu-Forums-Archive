---
title: "Wubi Hangs at 63% installation"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by sai_chaitanya on 2011-11-03
Hi,
I am trying to install Ubuntu via wubi on my old PC. I have no issues on my new PC. But when i do it on my old one the installation always hangs at exactly 63% of "Copying files.." during installation everytime. I tried using different versions(Kubuntu,Lubuntu,Xubuntu etc),changing the disk image used for installation,doing chkdsk,increasing RAM to 768MB, using acpi=off, using all available modes - verbose mode,safe graphics etc. . Nothing works. The live CD and boot from USB works perfectly with no issues even the graphic card is OK. I can do a full installation but worried now that what if it gets stuck in middle of partioning or something important. So i am going to use wubi only.So is there a workaround like creating a loopback device ourselves and getting it recognized as a HDD in installation from live CD? I am right now defragmenting the drives.Not sure if that helps but i'll let you know the results. Meanwhile any help would b appriciated.
The Specs of old PC:-
2.8 Ghz P4, 256MB RAM(also tried it by upgrading to 512MB and 768MB),80 GB HDD
Tried installation with 5GB to 13GB disk space sizes for Ubuntu.

---

### Post by sai_chaitanya on 2011-11-03
Also the reason it hangs as seen in the command line is beacouse of hung tasks. The tasks hung everytime are :- install.py, Loop0, Loop1, flush-7, and few others which keep changing from time to time.

---

