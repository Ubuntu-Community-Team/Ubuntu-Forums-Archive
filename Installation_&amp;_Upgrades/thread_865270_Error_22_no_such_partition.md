---
title: "Error 22: no such partition"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by gorgerax on 2008-07-20
Got a question for ya'll...

I have 2 drives in my machine...a 250G SATA, my boot drive with XP on partition1 and a 400G ATA.  When installing Ubuntu, wanted to install on the 400G ATA.  I told it to install on the 250G, partition 2 and a swap on Partition 3.  At step 7, advanced options, I told it to install the boot loader to the 250 G SATA,,,dev/sbd.

Upon reboot, GRUB comes up. I select the first option of Ubuntu and I get the error:

Error 22: no such partition.

I get the same error no matter which option I select!

Help!  Any ideas?  Thanks!!!

---

### Post by logos34 on 2008-07-20
press 'e' to edit the the highlighted ubuntu kernel selection, 'e' again on the 'root' line and change to (hd**0**,1).  'b' to boot.

gksudo gedit /boot/grub/menu.lst

change all the ubuntu root lines to match, + 'groot' near the top.

Add this to Windows entry:

>  title        Windows 95/98/NT/2000
root        (hd**1**,0)
[B] map (hd0) (hd1)
map        (hd1) (hd0)[/B]
makeactive
chainloader    +1

---

