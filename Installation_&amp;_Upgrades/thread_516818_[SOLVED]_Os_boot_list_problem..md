---
title: "[SOLVED] Os boot list problem."
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2007-08-03
Hi all. In my boot menu when it gives the choices of OS, i have four different versions of ubuntu listed. 

These are:

Ubuntu Kernel-2.6.20-16-server
Ubuntu Kernel-2.6.20-16-server Recovery mode
Ubuntu Kernel-2.6.17-12-server
Ubuntu Kernel-2.6.17-12-server Recovery mode
Ubuntu Kernel-2.6.15-28-server
Ubuntu Kernel-2.6.15-28-server Recovery mode
Ubuntu Kernel-2.6.15-26-server
Ubuntu Kernel-2.6.15-26-server Recovery mode
Windows xp pro

I just upgraded to Feisty from dapper via edgy. I first installed ubuntu server 6.06.1 and downloaded the xubuntu desktop from that terminal. Then this upgrade. 

What is the effect of this set up in my OS boot list? 
Can i remove the options i dont want to use, safely?

Thanks in advance...

---

### Post by merlinus on 2007-08-03
You can comment out (place a hash mark) in front of the lines you do not want to appear in grub in /boot/grub/menu.lst, or you could use Synaptic to remove some of the kernels entirely.

-merlin

---

### Post by upthelum on 2007-08-03
Thanks for the info...

---

