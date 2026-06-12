---
title: "multiple kernels problem"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by topquarck on 2006-08-18
[SIZE="3"]hi all;
my ubuntu has upgraded itself to a newer kernel version (2-6-15-26), its previous version was (2-6-15-23) and askd me To restart my machine .....
when i booted again, the bootloader showd me 2 choices, either boot using the new kernel or the old kernel... <and the windows entry in the bootloader disappeared>...
the Question is , **why do i need dual kernels on my machine?** **How to get rid of one of them and use only one kernel version without affecting my system** <i am afraid to erase one of them by Synaptic package manager then i find my entire system down ](*,)
PLS i need urgent help ;
thanx alot 
[/SIZE]

---

### Post by waldschm on 2006-08-18
When you install a new kernel, your old kernel is not uninstalled and GRUB retains the option to boot Ubuntu with that kernel. This is not a problem, it can just clutter your menu. It's a good idea to keep the old kernel around for a while, that way in case the new kernel is causing a problem you can boot into the older kernel you know to be stable. That said, if you want to, you can remove the old kernel with synaptic or just remove it from the GRUB menu by editing /boot/grub/menu.lst

---

### Post by topquarck on 2006-08-18
[SIZE="3"][B]is it really safe to remove the new kernel?

I mean when i tried to do so, sysnaptic told me it will remove other packages <i suspect they are used by other packages> I am afraid to do something i cant fix[/B][/SIZE]

---

### Post by waldschm on 2006-08-18
I haven't tried removing old kernels myself so I don't want to make a blanket statement on the safety of it, but if you want to read more for yourself check out this thread:

[http://www.ubuntuforums.org/showthread.php?p=1318190](http://www.ubuntuforums.org/showthread.php?p=1318190)

---

