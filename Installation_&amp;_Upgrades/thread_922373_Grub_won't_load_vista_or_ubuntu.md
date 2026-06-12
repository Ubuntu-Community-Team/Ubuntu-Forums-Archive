---
title: "Grub won't load vista or ubuntu"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by badfish69 on 2008-09-17
This is my first experience with linux. I have 2 sata hard drives, 320gb a peice. The first one is running Vista, so I tried installing Ubuntu on the second. Before I did this I changed the boot order so the second hard drive boots first, allowing me access to grub. I get these 5 options in grub:

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

Any of the 3 Ubuntu that I select gives me "Error 17: Cannot mount selected partition." 

The first Vista option gives me the same. The second Vista option goes to a black screen that says "Starting up" and never goes anywhere from there. I've tried reformatting the hard drive and reinstalling Ubuntu but that didn't help.

---

### Post by thepizzaman on 2008-09-17
setting it up for the ubuntu drive to boot first may be the problem
but where is grub install? on the vista or ubuntu drive?

Error 17 indicates GRUB can't id the partition type. Check [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) for more info. Here is the relevant entry:
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

---

### Post by caljohnsmith on 2008-09-17
OK, try rebooting, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)", press "e" to edit it, change the "X" to the other drive. For instance, if X is 1, change it to 0; if it is 0, change it to 1. Don't modify whatever Y is though. Press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to temporarily boot Ubuntu, and then you can modify your /boot/grub/menu.lst to make the change permanent. Let me know how that goes and we can work from there.

---

### Post by badfish69 on 2008-09-17
> **thepizzaman said:**
> setting it up for the ubuntu drive to boot first may be the problem
but where is grub install? on the vista or ubuntu drive?

Error 17 indicates GRUB can't id the partition type. Check [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) for more info. Here is the relevant entry:
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

Grub and Ubuntu are on the same drive, which boots first. If I switch to my first hard drive, Windows boots up normally.

---

### Post by badfish69 on 2008-09-17
> **caljohnsmith said:**
> OK, try rebooting, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)", press "e" to edit it, change the "X" to the other drive. For instance, if X is 1, change it to 0; if it is 0, change it to 1. Don't modify whatever Y is though. Press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to temporarily boot Ubuntu, and then you can modify your /boot/grub/menu.lst to make the change permanent. Let me know how that goes and we can work from there.

It worked, so in terminal I typed

sudo gedit

from gedit gui i opened /boot/grub/menu.lst

reversed the drive number for all entries, both ubuntu and vista. viola. thanks for the help.

---

