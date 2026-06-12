---
title: "Upgrading to Gutsy"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by nimeshchandran on 2007-11-23
hello guys today i finally got the kubuntu 7.10 cd which i have ordered through Ship-it... i am currently using kubuntu 7.04... so i tried to upgrade the existing kubuntu installation to 7.10 using the command

kdesu "sh /media/cdrom0/cdromupgrade"

but  i gets the error 

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sh: Can't open /media/cdrom0/cdromupgrade

i used to have another cd drive but not anymore... and the kubuntu cd opens in the cdrom0 folder... so what should i do to upgrade or should i make a clean install again??
i didnt wanted to lose all my current configurations...

---

### Post by Pumalite on 2007-11-23
Save /home and data and do a clean install. You'll save yourself numerous headaches.

---

### Post by logos34 on 2007-11-23
you need the [alternate desktop cd for that]("https://help.ubuntu.com/community/GutsyUpgrades")...since there's no shipit alternate version, you'll either have to download it or do a fresh install with the live install cd you have.  You could save your settings by [tranferring your /home directory]("http://www.psychocats.net/ubuntu/separatehome") (containing settings and config files) to a separate partition first, then install over the 7.04 root parititon.

EDIT: or do like pumalite suggested and just backup you personal files...it is true that a fresh install is preferable to an upgrade (especially to gutsy--it's my general impression that it's been rather more error-prone than past upgrades.  I did it for the learning experience, and it was definitely that...at approximately 9 hours it was a very long learning experience, which nearly ended in failure.  Consequently I may never do one again)

---

### Post by nimeshchandran on 2007-11-23
ok i will do as u say guys... hey one more doubt... Is there any chance to save the installed things that i downloaded i mean the mp3 support for amarok, or mplayer or firefox??? or would i have to redownload them again....??i am a newbie so dont know if these installed stuff needs to be downloaded again with the new distribution...

---

### Post by Pumalite on 2007-11-23
Install those again. It's five minutes tops.

---

### Post by nimeshchandran on 2007-11-23
problem is that i got only dial up and u can guess how much it will take just to download a driver for my nvidia card.... i had setup the current system in a perfect functional state after so many pains.... i mean the cost of downloading each applications...

---

