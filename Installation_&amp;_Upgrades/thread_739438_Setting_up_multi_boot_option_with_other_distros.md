---
title: "Setting up multi boot option with other distros"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by uzee007 on 2008-03-29
Hi,
I have bought a new computer for testing different distros. Its a single hd system 60GB, AMD cpu with CD Rom and 512B Ram.
What I would like to do is install multiple distros on separate partitions on the drive and then be able to boot into anyone at boot time.
The distros I would like to install are:
Ubuntu
Edubuntu
PCLinuxOS
SimplyMepis

Firs of all, I'm hoping multi-booting is possible..? (otherwise I will have to try 2 at a time)

Based on the search I have done so far, I read that dual booting linux with linux may pose problems as the 2nd distro's boot loader over-writes the first one, don't know how multi-boot is handled....
What is my best route? 
Also, since there is currently no OS installed on the PC, I think I will need to atleast partition the drive (with Gparted, etc.) after the first installation so that each distro has its own separate partition..? am I thinking right?
Thanks very much.
uzee

---

### Post by Pumalite on 2008-03-29
This might help:
[http://ph.ubuntuforums.com/showthread.php?p=4518862](http://ph.ubuntuforums.com/showthread.php?p=4518862)

---

### Post by kellemes on 2008-03-30
The distributions you list are making use of Grub..
You need to make a decision about the distribution you want to manage Grub from.. assuming this is Ubuntu.. simply install Ubuntu and have it install Grub.
Now you install Mepis, let it install Grub, it will overwrite the MBR.. not your Grub /bot/grub/menu.lst from the Ubuntu install.
Now you can use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to resetup Grub based on the Ubunt /boot/grub/menu.lst.
Now you have your old/first Grub bootmenu back, but without the entry to Mepis, how to fix it..
Add an entry to your /boot/grub/menu.lst (the Ubuntu one) like so..
```
# Mepis
title Mepis
configfile   (hd2,8)/grub/menu.lst
```
The configfile entry should point to the location of /boot/grub/menu.lst of your Mepis-install.
This way you get a nested bootmenu, works great.

You can have as many distro's installed as you wish.

When you want to install a distro that makes use of LILO instead of Grub (like Zenwalk), you simply install LILO in the root-partition of Zenwalk (so not the MBR!) and chainload like so..
```

# Zenwalk
title Zenwalk
root (hd*,*)
chainloader +1
```

---

