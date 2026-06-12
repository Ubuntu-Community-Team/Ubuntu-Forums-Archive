---
title: "Ubuntu 10.04"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Kezin on 2010-05-13
I am trying to install Ubuntu 10.04 on a SUMO external HDD, USB 2.0 as my internal HDD is fried and removed. It seems to install fine but when I reboot at end of installation It says Grub Error and wont allow me to do anything.  Any advice or tips appreciated. The only form of OS I have now is running this Ubunto CD as a test system.
Thanks
Kezin

---

### Post by dino99 on 2010-05-13
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Zimmer on 2010-05-13
I have installed Lucid to an external USB drive which already has Mepis and the legacy GRUB .
I added this to the Mepis GRUB menu.lst in order to boot it.

> ##altered  manual entry forLucid to hd0
title Ubuntu  Lucid 10.04, kernel 2.6.32-22-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.32-22-generic root=/dev/sdb2 ro quiet splash
initrd /boot/initrd.img-2.6.32-22-generic

When my BIOS sees the USB drive as first boot option it appears to allocate it as hd0 (not hd1 as you would expect).

So, you may need to find out how and where to change that in your GRUB2 files. It is NOT menu.lst anymore, but there is a guide to this on the documentation wiki...

Oh, and the commands above will not be right for GRUB2, except for the changing of the hd1 to hd0

UPDATE.. see the GRUB2 guide linked above , create a custom entry

---

