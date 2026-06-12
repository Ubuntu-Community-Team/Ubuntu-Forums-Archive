---
title: "Triple Boot w/ XP F11 encrypted and Ubuntu"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by jmc302005 on 2010-01-02
Hello, I have XP on sda1, Fedora 11 encrypted on sdb 1 (boot) and sdb 2 (root), I would like Ubuntu on sdc 1 (boot) sdc 2 (root). However when I tried to install from the cd the partition manager does not see my Fedora as an OS (I assume because it is encrypted). So my question is how can I achieve my triple boot without having to have my Fedora unencrypted. I want it encrypted for a reason. 

Also I cancelled the installation for Ubuntu and it reverted to a Live cd and I tried to mount my Fedora encrypted drive. Ubuntu asked for the pass and when I entered it I get an error saying it cannot be mounted because it is not a mountable file system. This is not good for me because I would like to be able to access all my hdd's from both distro's.

---

### Post by jmc302005 on 2010-01-04
Well it is a good thing I am very good with this sort of thing because I was able to figure this out on my own no thanks to anyone here. So for others wondering how to do this I will provide a solution.

Assuming you want to keep the Fedora grub boot loader in the hd0 MBR like I did you need install Ubuntu grub to your / (root) then you need to boot into Fedora and mount the Ubuntu hd. Navigate to /boot/grub and view the grub.conf. Get the location that shows where Ubuntu is installed (example: (hd1,1)) then add the following to the Fedora menu.lst in /boot/grub

```
title Ubuntu (your kernel version goes here)
      rootnoverify (hd2,0) <this depends on the location of your Ubuntu root
      chainloader +1
```by typing in terminal

```
sudo gedit /boot/grub/menu.lst
```The above will add Ubuntu to your MBR grub and when you choose Ubuntu it will the load the Ubuntu grub from your Ubuntu install. This is the easiest way to do it with out all the explaining of all the extra technical stuff.

Side note the grub.conf from Ubuntu (located in /boot/grub) adds +1 to the location of root, for instance mine was listed as (hd2,1) this is because the newer version of grub that Ubuntu uses starts the hd count from 0 but the partition count from 1. Fedora's version starts hd count from 0 and partition count from 0. This is why I had to write mine from (hd2,1) to (hd2,0).

I hope this helps others because it can be quite confusing once you start booting more than 2 OS's.

Still working on being able to view my encrypted drive from Ubuntu. This unfortunately may not be possible.

---

