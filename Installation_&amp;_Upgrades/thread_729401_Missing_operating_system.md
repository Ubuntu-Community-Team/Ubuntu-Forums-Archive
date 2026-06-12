---
title: "Missing operating system"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by phreakboy on 2008-03-19
I finally got 7.10 to install after a few issues and then when it came to the reboot, now it just says missing operating system. I have tried a couple solutions that I found but with no luck. I am really hoping that someone here can help as I really want to get this setup. The laptop I am on has been running opensuse for quite some time and now I would really like to check out ubuntu 7.10 on my other laptop.

---

### Post by Pumalite on 2008-03-19
Boot up Ubuntu Live CD in the offending laptop and from the Terminal, post:
sudo fdisk -lu

---

### Post by phreakboy on 2008-03-19
/dev/hda1                  63    36339039    18169483+   83   Linux
/dev/hda2      75153070    778140159   1494045        5   Extended
/dev/hda3      36339030    75152069    19406520     83   Linux
/dev/hda5      76646178    78140159        746991     82   Linux swap / solaris
/dev/hda6      75152196    76646114        746959+   82   Linux swap / solaris

Partition table entries are not in disk order

---

### Post by Pumalite on 2008-03-19
Mount your partition:
sudo mkdir /media/hda1
sudo mount -t ext3 /devhda1 /media/hda1
Now get menu.lst:
cat /media/hda1/boot/grub/menu.lst
Post the output here.

---

### Post by phreakboy on 2008-03-19
after I type the sudo mount command, I get 
mount: special device /devhda1 does not exist.

---

