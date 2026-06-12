---
title: "Access hard disk files from ubuntu Live CD"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by marmotapl on 2010-05-08
Hi, i'm having some problems booting ubuntu 9.10 and i just want to backup my files and install it all over again.

I want to access my old files from the ubuntu Live CD, because no kernel is working.

Is there a way?. Just in case, i don't have partitions, so i don't have a 'home' one (but i'm going to).

Thanks in advance =)

---

### Post by lemming465 on 2010-05-09
The Live CD's don't tend to automount hard disk partitions, but do tend to add them to the "Places" menu.  Just pick partitions from there till the one you want shows up.  You can also mount partitions from the command line by doing things like ```
sudo mount /dev/sda1 /mnt
```.  We can give you more specific advice if you post the output from ```
sudo fdisk -lu; sudo blkid
```.

---

