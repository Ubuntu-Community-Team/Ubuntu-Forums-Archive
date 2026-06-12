---
title: "Lost Ubuntu 9.10?"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by fvs on 2009-12-01
First installed Ubuntu 9.10 and then on another partion I installed Debian Lenny, When I rebooted my grub menu didn't show Ubuntu. How do I get it back on my grub menu?

---

### Post by Megafag on 2009-12-01
> **fvs said:**
> First installed Ubuntu 9.10 and then on another partion I installed Debian Lenny, When I rebooted my grub menu didn't show Ubuntu. How do I get it back on my grub menu?

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

The bit in that on grub should work?

im not sure because i never had to do it with grub2

---

### Post by darkod on 2009-12-01
It's better to reinstall grub2 to the mbr of the disk. Or you can adjust the grub from Lenny.

---

### Post by fvs on 2009-12-01
How do I reinstall grub2?

---

### Post by darkod on 2009-12-01
If you don't know which one is your ubuntu root partition run:
sudo fdisk -l (small L)

That will show you the partitions and hopefully you can figure it out without additional tries.
Once you know the partition, boot with ubuntu cd, select Try Ubuntu option, open terminal and run:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Here /dev/sda3 is example for your root partition. Change as necessary. And I assume you have only single drive, this will install grub2 on the MBR, in other words /dev/sda.

---

### Post by fvs on 2009-12-01
Thanks for your help, I went back and reinstalled it once more.
now I can't get my music on to the mp3 I have? Well keeps me busy.
Thanks one more.
fvs

---

