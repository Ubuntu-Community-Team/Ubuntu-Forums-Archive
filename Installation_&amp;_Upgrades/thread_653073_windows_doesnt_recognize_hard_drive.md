---
title: "windows doesnt recognize hard drive"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by adamb23 on 2007-12-29
i need to go back to windows, dont really want to, but ive been having so many problems with my graphics card and also some vital programs i need windows for wont work on wine. However, i formatted my main hard drive to put ubuntu on and now when i try to reinstall windows it cant format my hard drive, says it has to be in nfts format. I dont want to run ubuntu and windows, just windows if possible.

---

### Post by Pumalite on 2007-12-29
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Delete everything in your hard drive. Make a new large partition of your whole hard drive, formatted ntfs. Install Windows.

---

### Post by pietjanjaap on 2007-12-29
Start pc from xp cd, then go to recovery console(repair i think), this is like dos screen.
There you should delete everything and do fixmbr or mbrfix, and then make a new patition.
If you leave some space open then you can try ubuntu together with xp.


Or:
If you don't have xp install cd. then go to [www.bootdisk.com](www.bootdisk.com),
download win 98 bootcd, do fdisk /mbr , and delete all partitions. Then install xp again.

---

### Post by adamb23 on 2007-12-29
ok pumalite, i burned the iso on a cd, which option do i select in the main menu?

---

### Post by Pumalite on 2007-12-29
When you first boot Gparted you have a 'boot' prompt; usually 'Enter' gets you in in most computers. Unless there is a new version that I have not used. I'm still using 0.3.4-0.iso. If you have a newer version, post your menu.

---

### Post by adamb23 on 2007-12-29
the version im using is 3.4-11. i selected the first option i came to and it went fine for a while then it said analog input not able to display video mode

---

### Post by Pumalite on 2007-12-29
Hit all options in your menu until you hit the jackpot or else try to get the version I have and hit 'Enter' at boot. Mine is easier I've found.

---

