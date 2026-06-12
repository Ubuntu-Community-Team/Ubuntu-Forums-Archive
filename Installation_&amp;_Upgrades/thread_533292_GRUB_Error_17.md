---
title: "GRUB Error 17"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by aho on 2007-08-23
Hey. I dicided to dual boot my windows xp with ubuntu. So as uauall i put in the CD and set it all up but now when i turn on my computer i get this error:
```
Booting from local disk...
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17
```

I have set up ubuntu before many times and i have never had this error. I dont understand and im not sure how to fix it.

Can anyone please help? I am not that experienced with Ubuntu yet so you may need to give me some simple steps. Sorry.

Thanks 
- AHO

---

### Post by merlinus on 2007-08-23
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

-merlin

---

### Post by Pumalite on 2007-08-23
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Post cat /boot/grub/menu.lst

---

### Post by mrfelker on 2007-08-23
The links are to the general manual for GRUB which is quite esoteric.   What error 17 means (quite common) is that you haven't pointed Ubuntu to the  right partition so it can't recognize the FS.
The way I do it is to setup a small (100MB will do) partition for the /boot (which actually contains GRUB and the boot menu in /boot/grub.  Then install Ubuntu root ( /) in whatever size partition you want.
Then tell Ubuntu to make the /boot partition bootable.  As always - you just can't do this the GUI install of Ubuntu.  Use the Alternate install CDROM (easy to download the image and burn it - say on Windows using the FREE Windows program Imgburn)   The text install is not really that hard.  Be sure to make the /boot partition bootable (toggle option).  You should not get a problem.  Once you get Ubuntu up use Gparted to see (and modify if you wish) your setup.

A sample might be:

/dev/hda1 /windows (mount point) ntfs (next column you can start with defaults 0 0.
/dev/hda2 /boot   ext2  <I use this instead of ext3 since the boot files are completely static - so why journal them? defaults 0 1
/dev/hda3   swap <I forget the options since with 8GB of RAM I don't use a physical swap drive>
/dev/hda4   /   ext3  defaults 0 1.

DONT edit the Ubuntu /etc/fstab if you want preserve sanity.

---

### Post by MQMike on 2007-08-23
You need to follow the links given by   merlinus and Pumalite.
Pay attention to re-installing GRUB and editing the menu.lst.

You didn’t tell us where Windows is and where you put Ubuntu on the hard drive.
Also, during the installation of Ubuntu, we hope that GRUB was installed to the MBR of the drive, but if not, that’s the partr about re-installing GRUB.

First follow what Pumalite asked for – the menu.lst.

---

