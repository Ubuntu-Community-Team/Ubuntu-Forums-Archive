---
title: "help with partioning drive"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by DataSpy on 2010-11-21
Hello,
I'm partitioning my hd to install ubuntu 10.04 minimal with gparted and I was wondering if there's a way to assign mount points, like / and /home ?

Any help greatly appreciated, thanks in advance!

---

### Post by dino99 on 2010-11-21
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by DataSpy on 2010-11-21
That's actually what I did, I'm using Gparted and created 3 partions, one for root, one for swap, and one for home but I can assign mount points.  So when I try to install the OS it says there's no root partions, do you know how to assign mount points in gparted, I've looked through every options?!

thanks,
Jim

---

### Post by dino99 on 2010-11-21
pay attention when formatting /  set it bootable and validate

---

### Post by coffeecat on 2010-11-21
> **DataSpy said:**
> So when I try to install the OS it says there's no root partions, do you know how to assign mount points in gparted, I've looked through every options?!

When installing, you don't assign mount points with Gparted - you do it in the installer. From the live CD, start the installer and when you get to the partitioning stage, choose 'manual (advanced)'. You can point the installer to the partitions you have already created and it will sort out the mounting for you. It's all reasonably clear, but post back if you need.

---

