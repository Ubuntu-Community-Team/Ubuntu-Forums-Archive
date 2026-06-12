---
title: "sudo grub-install --root-directory ?"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2010-11-01
Dear all,

If I boot on a live-CD, then enter in a terminal the following commands:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt

..does it install Grub-pc in /dev/sda1 ? even if Grub was already installed in /dev/sda1 ?


Furthermore, are the 3 above commands equivalent to the below ones ?

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc
sudo chroot /mnt
sudo grub-install /dev/sda
exit
sudo umount /mnt/dev /mnt/proc /mnt/sys
sudo umount /mnt

Thanks in advance for your answers.

---

### Post by Quackers on 2010-11-01
The first set would re-install grub to the MBR of /dev/sda. It would be used if the MBR had been damaged but the normal grub boot files were ok.
The second set would seem to me to do the same thing. 
Neither method would touch grub-pc as I understand it.
See drs305's guide here for fuller details.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YannBuntu on 2010-11-01
Thank you !
So if GRUB files were already present in sda1, the chroot method I wrote will not modify them ?

---

### Post by Quackers on 2010-11-01
> **YannBuntu said:**
> Thank you !
So if GRUB files were already present in sda1, the chroot method I wrote will not modify them ?

Please note that on re-reading your post I have amended my first post.
In answer to your present question, I'm not absolutely sure!

---

### Post by oldfred on 2010-11-01
When you install grub, grub2, or a windows boot loader to the MBR, it is just a tiny amount of code that the computer uses to continue booting from files installed elsewhere.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

The MBR standard is that BIOS uses the MBR in the primary master (older IDE), now with SATA BIOS is a little smarter and will let you choose which hard drive's MBR to use.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

