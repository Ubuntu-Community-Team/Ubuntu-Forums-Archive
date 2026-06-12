---
title: "Dual boot menu missing"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2010-02-23
Hi, everyone I just upgraded to windows 7 and I dual boot ubuntu 9.10 64 bit, when I installed windows I lost my boot menu, can anyone tell me how to fix this with out reinstalling ubuntu? Thanks inadvance.

---

### Post by rcayea on 2010-02-23
> **wildmanne39 said:**
> Hi, everyone I just upgraded to windows 7 and I dual boot ubuntu 9.10 64 bit, when I installed windows I lost my boot menu, can anyone tell me how to fix this with out reinstalling ubuntu? Thanks inadvance.

Boot from the CD/USB flash drive from which you installed Ubuntu
Open terminal (It is there under Accessories)
type in sudo fdisk -l
then type sudo mount /dev/sdAB /mnt , where A is your drive and B is your linux partition. In my case, I typed in sudo mount /dev/sda7 /mnt

install GRUB again by typing this sudo grub-install --root-directory=/mnt /dev/sdA , where A is your drive. In my case, I typed sda

Now type sudo umount /mnt

---

