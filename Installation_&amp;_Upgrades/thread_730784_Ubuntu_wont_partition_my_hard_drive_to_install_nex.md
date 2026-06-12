---
title: "Ubuntu wont partition my hard drive to install next to XP"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by mattrobinson999 on 2008-03-21
Ok,
I needed to reinstall xp on my old computer because of driver problems.
So I installed Ubuntu to wipe the hard drive and found that I actually quite liked it.
I continued to reinstall xp and wiped Ubuntu from my hard drive deciding that I would reinstall Ubuntu after xp in the long term.
Now ive reinstalled xp, and that works fine.
Ive used the Ubuntu live disk to try and install Ubuntu but it wont.
It says that I dont have any unpartitioned space on my hard drive. (200Gb)
I dont want to reinstall xp because I dont want the hastle.
Does any one have any advice?

---

### Post by Pumalite on 2008-03-21
Get Gparte3d Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Right click on XP, choose 'resize' from the menu, format ext3 the new space. Then boot Ubuntu and install in new partition. Let Grub install to MBR (by default) and you'll have dual boot.

---

### Post by mattrobinson999 on 2008-03-21
Thank you soooo much who ever you are

---

### Post by Pumalite on 2008-03-21
I am who I am. You are welcome.

---

### Post by mattrobinson999 on 2008-03-21
The Gparte3d Live CD that you suggested wont work on my comp. 
The monitor says "out of frequency"

do u have any other suggestions?

---

### Post by Pumalite on 2008-03-21
Gparted Live CD has several options. Try them all.

---

### Post by mattrobinson999 on 2008-03-21
Ive tried all of the options now and non of them work.
Any other programs or suggestions?

---

### Post by Pumalite on 2008-03-21
Get version 0.3.4-0 and try with that.

---

### Post by mattrobinson999 on 2008-03-21
Ok,
but do you know of any other FREE software that will work?

---

### Post by Pumalite on 2008-03-21
You could try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
I know it has a partitioner too.

---

### Post by Kevbert on 2008-03-21
With Windows XP you may have a paging file towards the end of the drive. Run the Windows Defragmentation Program and defrag the drive. If this block of data has not been moved you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. Now click on Set, OK, OK, OK and close Control Panel.
Reboot the machine into Windows and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up.

---

