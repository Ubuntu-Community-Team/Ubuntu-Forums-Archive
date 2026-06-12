---
title: "Unknown filesystem: Grub rescue"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by -_-' on 2010-07-19
Hello,

I've deleted a Ubuntu partition and grub doens't work anymore.

I get this message

Unknown filesystem
grub rescue >

I've searched around and for solutions but these didn't worked for me.

This is wat I've tried:

Burned Super Grub Disk and tried to boot from CD and USB.
Burned Ubuntu Live Disk and tried to boot it from CD, USB and Extended Harddisc.

But the error still appears. I look that my computer won't boot from USB or CD. Ofcourse I changed the bootthing in the bootmenu.

Can you help me to repair grub?

---

### Post by ajgreeny on 2010-07-19
Do you have ubuntu on the machine at all, as a hard disk partition?  If not you can not repair grub, as there are no grub configuration files available.

Are you sure you have changed the BIOS to boot first from a CD?  How you get into the BIOS will depend on your computer, but there is usually a screen message that says "Press DEL to enter setup" or something similar when it flashes up, but you need to be quick to see it, and hit that key.  make sure you have changed the Boot device to CD-rom, and you should be able to boot from the live CD with no problem.  If you can't there may be something wrong with either your CD or the drive.

If you can get the live CD to boot, run ```
sudo fdisk -l
``` in terminal and post the output back here, and also download the **boot_info_script** from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and follow the instructions on the site to run it and post back here the RESULTS.txt file it produces

---

### Post by -_-' on 2010-07-23
Ehm, I made a stupid mistake by burning the disks....
I reburned the Live Disks and I fixed it.

Anyway, thanks for replies.

---

