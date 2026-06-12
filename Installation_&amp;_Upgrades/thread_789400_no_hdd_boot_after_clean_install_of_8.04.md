---
title: "no hdd boot after clean install of 8.04"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by brijam on 2008-05-10
Twice through the GNOME 8.04 live CD install today, both times letting it configure everything on its own, including partitioning.

"Operating System not found".

Both times, the hdd won't boot.  It appears GRUB isn't being installed at all.  /dev/sda is flagged as boot when I look at it from the live CD's gparted.

Also, Ubuntu is the only Linux I've installed that always finds my Hitachi laptop drive as being SCSI instead of IDE.

Is there a guide somewhere to getting an auto-configured GRUB going?

---

### Post by Pumalite on 2008-05-10
Are you running Vista?

---

### Post by brijam on 2008-05-10
Good lord, no.

100% clean hdd to start.

---

### Post by Pumalite on 2008-05-10
Boot your Live CD and post:
sudo fdisk -l

---

### Post by brijam on 2008-05-10
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-05-10
How did you partition?

---

### Post by brijam on 2008-05-10
Guided - entire disk.

I was never offered any options for anything at all, partitioning, packages, or otherwise.

Also:

ubuntu@ubuntu:/boot$ ls
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-16-generic
ubuntu@ubuntu:/boot$ 

Unless I'm mistaken, grub wasn't installed at all.  Shouldn't there be a /grub directory there?

---

### Post by brijam on 2008-05-10
Anyone?

---

### Post by Pumalite on 2008-05-10
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by brijam on 2008-05-10
No effect.

From what I can tell, there's nothing to get from /boot/grub/stage1 -- /boot/grub doesn't exist, and that's what find returns.

Screw it, I'll just go back to Gutsy and upgrade.

---

### Post by Pumalite on 2008-05-10
Good luck.

---

### Post by brijam on 2008-05-10
Thanks.  Sorry if that sounded directed at you -- it certainly wasn't.  Thanks for your help.

---

### Post by Pumalite on 2008-05-10
No offense taken. You are welcome.

---

