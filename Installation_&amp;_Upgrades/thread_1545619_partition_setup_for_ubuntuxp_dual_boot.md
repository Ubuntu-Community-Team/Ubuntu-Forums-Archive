---
title: "partition setup for ubuntu/xp dual boot"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by icarus035 on 2010-08-04
Hi all. I have created 5 partitions:

2 GB ext3
20 GB ext3
10 GB ext3
20 GB ntfs
400 GB ntfs

I have already installed XP on 20GB ntfs. Will dual boot work if I use the 3 ext3 partitions to install Ubuntu?

Thanks!

---

### Post by icarus035 on 2010-08-04
By the way, during installation, in the final step when I click "Advanced" it displays option for boot loader where to install it. By default it is set to /dev/sda which is my entire 500GB hard disk. Should I select only XP partition for this?

---

### Post by icarus035 on 2010-08-04
Anyone pls help...

---

### Post by Blackbird_13 on 2010-08-04
The simple answer is yes, you can install Ubuntu to the ext3 partitions. You just need to decide how you want to allocate your partitions - just do a search on Ubuntu partitioning. This is no right /wrong, just what suits you.

I found that I tried a number of different partitioning scheme before I arrived at one I was happy with - I just kept on re-installing Ubuntu until I got it right (for me). As long as your data files are on a separate partition, re-installing is quick/easy/safe.

You should take the default option of installing grub to the MBR of /dev/sda - this will install a small bit of code which will point to your /boot/grub/ directory within Ubuntu and load the grub boot menu when you boot. During the initial install grub should automatically locate your windows xp operating system and present this as a boot option in the boot menu.

---

### Post by oldfred on 2010-08-04
Whatever you do, do not install grub to the windows partition. The windows partition has essential windows boot files that both the standard windows boot loader in the MBR and grub chainload to, to allow windows to boot.

---

