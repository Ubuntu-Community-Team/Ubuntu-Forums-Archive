---
title: "Ubuntu or kubuntu which is better?"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by SBMN7 on 2011-09-13
Guys, ubuntu or kubuntu which is better? I have some package of ubuntu, ubuntu package software can install in kubuntu? Help

---

### Post by Basher101 on 2011-09-13
what you mean i think are .deb files. The only difference in Ubuntu and Kubuntu is that they use different Dekstop Environments. Ubuntu uses Gnome and Kubuntu KDE. Also they have different pre-installed programs. Otherwise they are 100% the same. As for the software center i am not sure if you can install it on Kubuntu. I did it the other way around - installed Ubuntu and after it the KDE desktop. Now i got Gnome, KDE and all the pre-installed programs from both Ubuntu and Kubuntu.

---

### Post by SBMN7 on 2011-09-13
Hello guys, i am using kubuntu on my desktop, ubuntu on my laptop. But i found problem in kubuntu. When i set its resolution 1024x768, its run perfectly. But when i trun off computer and start then its resolution auto change to 1600x....! I tried many time to set my best resolution 1024x768, but it will auto change. My monitor is CRT, 17 Inch . Please help

---

### Post by sanderj on 2011-09-13
> **SBMN7 said:**
> Guys, ubuntu or kubuntu which is better?

Both!

:P

---

### Post by nunoxic on 2011-09-13
First Open Terminal and Run 
xrandr
Hopefully, Your monitor will be listed as VGA1 (If it is listed as anything else, replace VGA1 with whatever it is listed as)
xrandr --output VGA1 --mode 1024x768
If this changes your config, consider adding this to .bashrc
This a very very crude way of doing it but it should work.

Also,
Ubuntu and Kubuntu are not very different. Neither is Ubuntu and Debian. It just depends on how you wish to look at your things. The desktop environment is the only major change (among others). It is completely your choice : KDE GNOME Unity XFCE etc.
Try them all out and decide on your own.

---

### Post by oldos2er on 2011-09-13
> **SBMN7 said:**
> Guys, ubuntu or kubuntu which is better? 

  The one that best fits your needs.

> I have some package of ubuntu, ubuntu package software can install in kubuntu? Help

Generally you can install any package in any desktop environment; at least I've never had a problem doing so.

---

