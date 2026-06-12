---
title: "Gutsy don't boot anymore"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by proti on 2007-09-03
Hello,
I installed a few weeks ago 2 machines with a gutsy.
The hardware is :
  AMD64 x2
  4go RAM
  2x 250Go

I  installed them with 3 partition :
   /boot in raid1 / EXT3
   swap alone on each disk
   LVM parition of the rest of the disk in RAID1
       in the LVM
       /root
       /usr
       /home
       /var

Everything was perfectly working until after one upgrade, one of the machines did not reboot anymore.

At recovery reboot, only root partition is mounted and not the others.
I have to do manualy at the prompt :
  mount -a
  /etc/init.d/rc S
and the machine finish to boot correctly.

I wonder what is wrong since both machines are installed in the same manner, and one is ok, the other not ?

---

