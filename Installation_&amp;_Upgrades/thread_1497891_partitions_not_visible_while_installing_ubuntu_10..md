---
title: "partitions not visible while installing ubuntu 10.04"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by brohitv on 2010-05-31
Initially i used to have only ubuntu but for later i have installed windows
over ubuntu 10.04 and i have recovered the grub using the commands given below
   1. Boot from the CD/USB flash drive from which you installed Ubuntu
   2. Open terminal (It is there under Accessories)
   3. type in sudo fdisk -l
   4. then type sudo mount /dev/sdMP /mnt , where M is your drive and P is your linux partition. For instance sudo mount /dev/sda5 /mnt
   5. install GRUB again by typing this ...
   6. sudo grub-install --root-directory=/mnt /dev/sdA , where A is your drive. So you may type sda
   7. Now type sudo umount /mnt. So as to unmount the volume.

so now after doing all this i am not able to see my partitions in ubuntu(I can see my partitions in windows xp).when i have opened the gparted i see only one unallocated space of 150gb (but i have partitions of 21,50,and 60gb).
please tell me what to do so that i can see my partitions in ubuntu.

---

