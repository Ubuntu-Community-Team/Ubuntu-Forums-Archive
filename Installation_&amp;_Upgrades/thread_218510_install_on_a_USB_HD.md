---
title: "install on a USB HD"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by heboth on 2006-07-18
Hello,

I've browsed various threads on how to install Ubunto 06.6 on an extenal USB HD without any luck.

My PC is a IBM R50p that can boot on a CD and a USB device. I've installed Ubuntu on the USB drive (marked as /dev/sda) and asked to install the boot loader on /boot (not the hda with my Window$ partion). However GRUB will not boot my partion. The root in GRUB is set to (hd1,0) which is correct and the kernel is /boot/wmlinuz-2.... root=/dev/sda1 ro quiet ....

all is correct. Can anybody help me out here ? :confused:

---

### Post by heboth on 2006-08-20
Solved the issue. A hint to others with this problem. Install Ubuntu on the USB HD. Install the GRUB on the external USB as well. Make sure to have the USB device as the **first** boot device - this is done in the BIOS. When booting ubunto you get the boot mnager. Select the Ubuntu partion but press 'e' to change the device. I've change mine from (HD1, 0) to (HD0,0). This is because the USB device is now actually the first device. Select 'b' in the boot manger for booting the partion and bingo... ubuntu boots !! :D :D :D 

Cheers


Henrik

---

