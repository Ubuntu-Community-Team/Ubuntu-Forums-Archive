---
title: "dual boot and partition resizing"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by bward1 on 2007-01-28
I have a system which is currently running just ubuntu, and I would like to dual boot it with another linux distro to try it out.  I have all of my user files in /home/ which is on a seperate drive /dev/sdb so that shouldn't be a problem as it will be /home/ in both installations.  I just need to resize my root partition on /dev/sda because I intend to keep the same swap space and boot partitions.  I know i will have to put the kernel for the new distro in the /boot partition and then edit /boot/grub/menu.lst accordingly.  I just need to trim down my / partition to make room for another distro.  Is there an easy, relatively safe way of doing this?

---

### Post by confused57 on 2007-01-28
> **bward1 said:**
> I have a system which is currently running just ubuntu, and I would like to dual boot it with another linux distro to try it out.  I have all of my user files in /home/ which is on a seperate drive /dev/sdb so that shouldn't be a problem as it will be /home/ in both installations.  I just need to resize my root partition on /dev/sda because I intend to keep the same swap space and boot partitions.  I know i will have to put the kernel for the new distro in the /boot partition and then edit /boot/grub/menu.lst accordingly.  I just need to trim down my / partition to make room for another distro.  Is there an easy, relatively safe way of doing this?

I haven't had any problems resizing partitions, using the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by bward1 on 2007-01-30
I tried the GParted liveCD but with no luck.  Without knowing the troubles it would cause, I inadvertantly bought a motherboard with a JMicron controller on it so I think that this is what is causing the problems.  I get to the point where I can choose some different options to load different kernel modules or what not, and then it kernel panics.  I guess I'm going to have to find another way around this, any suggestions?

---

