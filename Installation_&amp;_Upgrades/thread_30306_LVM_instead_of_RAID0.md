---
title: "LVM instead of RAID0"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by tariqf on 2005-04-28
Hi I have been trying to install Ubuntu onto a s/w raid 0 but grub/lilo always fails to install so I decided to just do LVM.

I have 2* 80GB hard disks on seperate IDE controllers and use LVM to have 100G /video volume and 50G system area. The remaining 10G is for /boot and /swap. 

This works fine but can anyone tell me if I am getting the same performance I would from a raid0 config? i.e. is LVM striping my 2 disks and getting almost double the throughput for reads and writes as you would with raid0?

---

### Post by tonym on 2005-04-28
You can request striping by use of --stripes and --stripesize on lvcreate.  Don't know what the performance comparison is.

---

### Post by tariqf on 2005-04-28
does anyone know if lvcreate uses striping by default in the installer? 

The reason I ask is because I created the logical volumes through the partition management in the installer.

---

### Post by tonym on 2005-04-29
You could try running lvdisplay -v .  Don't know if it gives striping info.

---

