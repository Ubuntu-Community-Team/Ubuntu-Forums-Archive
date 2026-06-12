---
title: "Grub bootloader goes fail to boot in dual boot system after installing Ubuntu 12.10"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by ketan985 on 2012-10-20
I had 12.04 with my dual boot system. Yesterday I downloaded  Ubuntu 12.10 make bootable USB and choose Upgrade option in Installer.  After installation Grub failed to boot my machine. I tried following  to  fix grub bootloder . Same problem I fixed with Ubuntu 12.04 using live  USB but this solution not work for Ubuntu 12.10. Now coming at exactly  where this solution goes fail. 
  I followed  this steps after booting Live USB and opening terminal.
  1)  sudo fdisk -l to see where Linux is installed
  2)  sudo mount /dev/sda9 /mnt where sda9 is my linux partition
  3) sudo mount /dev/sda9 /mnt/boot 
  4) sudo mount --bind /dev /mnt/dev
  5) sudo chroot /mnt  (No problems with this steps done perfectly)
  6) grub-install /dev/sda when I type I got error that
  source_dir doesn't exist Please specify --target or --directory
  How can I solve this ?

---

### Post by p-dh on 2012-10-20
Have you tried using [boot-repair]("https://help.ubuntu.com/community/Boot-Repair")? I have used it on several computers and it has done the trick. If it doesn't fix your problem, please post and I'll help you through this. I have found that grub2 is pretty easy to fix.

Peace,
Paul :cool:

---

### Post by darkod on 2012-10-20
You can't mount /dev/sda9 as both / and /boot. Do you have a separate /boot partition or not?

If you don't have, you don't need to mount anything at /mnt/boot, that is only for separate /boot partitions.

If you do have separate /boot, it has to be another partition, /dev/sda9 can't be both.

PS. I don't know where you found those command, but usually you don't need the chroot. You can do it without it and it's much simpler, you only pass as argument the mounted root partition. So, if your /dev/sda9 is root and you have no separate /boot partition, you only need to do:
```
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
That should work.

---

### Post by ketan985 on 2013-01-01
Thanks a lot Friend !!!!!!!!!!!!!

---

