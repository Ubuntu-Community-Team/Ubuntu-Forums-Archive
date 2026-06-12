---
title: "need help with bootup and grub"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by forcifer on 2008-05-25
So i installed unbuntu (8.04 i think, whatever the most recent one is) on my mom's computer that i built (MSI K9N Neo-F, x1950 pro PCIe, 1gb ram, 80gb PATA hdd goodness) and everything was working fine. i installed the updates, installed thunderbird, but then i restarted for the updates to take effect and such. now is where i am having problems: 

when i rebooted, it says loading GRUB 1.5, then this command prompt style thing shows up that i presume is grub. and i dont have the slightest clue as to what to do. any help would be greatly appreciaited :) 

btw, i did the TAB for the possible commands, and if i try just normal "boot" it says kernel must load, and if i try "kernel" then there is something about file path...im not sure. this is the first time i have really used linux outside of saving others computers and all help would be very nice :)

update: if i try loading from live CD and choose boot from local disk, then it says loading grub 1.5 and, a bit later, Error 18. help please

---

### Post by Pumalite on 2008-05-25
Boot your Live CD and post:
sudo fdisk -l

---

### Post by forcifer on 2008-05-25
alright i did that and this is what shows up right underneath it

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf8e31d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

is that what is supposed to happen? ill try a reboot to see if anything works now. thanks :)

---

### Post by Pumalite on 2008-05-25
Are you sure you installed the Desktop version?

---

### Post by forcifer on 2008-05-25
i think i did. well, its working now. with the reboot, there werent any grub errors. time to see if ATI drivers work now =/

EDIT: the X1950 series isnt mentioned under the xorg information thing. should i still install, or should i just leave it as it?

---

### Post by Pumalite on 2008-05-25
ATI is a problem in Linux. Most ATI cards do better with 'vesa' as the driver than with the proprietary driver. Some people do well with Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by forcifer on 2008-05-25
thanks :) the same dumb error is back, i might try redownloading, reburning, reformatting and see if that makes it any better. thanks again though :D

---

### Post by Pumalite on 2008-05-25
You are welcome. Good luck.

---

