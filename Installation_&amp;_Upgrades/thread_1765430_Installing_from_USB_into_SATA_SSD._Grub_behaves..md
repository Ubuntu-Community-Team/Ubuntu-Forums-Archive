---
title: "Installing from USB into SATA SSD. Grub behaves."
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by pygy on 2011-05-23
Hello,

I'm trying to install Natty from a USB thumb drive on a SATA SSD. 

My main system is OS X. The method to create an instal USB disk on the download page didn't yield a bootable disk (the partition was readble, with the right files, but GRUB never started). 

The [quick method from the clemsonlinux wiki](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive#The_Quick_Method) gave me a minimal bootable drive, though.

From there, I tried to install Natty on my SSD.

Once again, the partitioning process appears to work fine, the files are copied, no problem, but the GRUB install fails silently.

I think that the problem comes from the fact that, when I boot from the USB drive (even if the SSD is set as the first boot device), the SSD ends up at /dev/sdb, whereas it would be at /dev/sda  if the machine could be booted from the SSD.

I chose the automatic partitioning method and ends up with sda1 (/), sda2 (ext) and sda5 (swap).

If I launch the installer in recovery mode and ask to mount /dev/sdb1 as root, mount reports that sda1 is / (sda1 doesn't even exist), but blkid reports the SSD as /dev/sdb.

The output of the boot_inf_script is clearly pathological, but I didn't manage to get it out of the machine with what I have (gmail is broken in lynx).


I've also tried to install LILO instead of GRUB. LILO boots, but doesn't find /dev/sdb (which is now /dev/sda) and gives me a busybox prompt.

I've tried to install GRUB from there, but, once again, I get a black screen at boot time.

Advices would be welcome (to fix either GRUB or LILO, as long as the system boots, I'll be happy).

---

### Post by pygy on 2011-05-23
Alright :-)

I got it to work.

I had to replace all instances of /dev/sdb1 by /dev/sda1 (in /etc/fstab, /boot/map, /etc/lilo.conf), I rebooted then chrooted again into /dev/sda1 and ran **lilo -r /**.

Now, I get to the command line prompt. There's another problem, but it is unrelated, so I'll leave for another thread.

---

