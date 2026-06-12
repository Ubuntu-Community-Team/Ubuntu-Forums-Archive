---
title: "Installing DVD player packages - Restart - Boot Hangs in GRUB"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by Cayitano on 2008-03-18
These two lines were at the end of a list of similar lines with the [  29...] opener.


[   29.182519]  [<c0105627>] kernal_thread_helper+0x7/0x10
[   29.182570]  ==========================

Manual off/on switch forced shutdown.

As boot up progresses in GRUB a message calls for pressing the ESC key to go to a menu of choices.

First three choices:
Ubuntu 7.10. kernal 2.6.22-14-rt
Ubuntu 7.10. kernal 2.6.22-14-rt (recovery mode)
Ubuntu 7.10 kernal 2.6.22-14-generic

All the generic choices work. The first two fall down dead with the notation listed at the top.

On shutdown the machine reads out a blue Kubuntu. Generic boot up reads Ubuntu as it progresses into the log-in window.

This happened shortly after using Synaptic to install Mplayer, Xine, Video Lan Client, and Ogle and continues to occur. A restart was required and that is when I noticed the Kubuntu boot down identifier.

I uninstalled Ubuntu Studio, Kubuntu, Edubuntu in sequence and rebooted each time with no solution.

I booted again generic and did a Synaptic search for Ubuntu to reload it and found a reference to an i386 meta package of some kind, aha! Linux kernel image for version 2.6.22 on i386.

Installed it and now the baby boots up fine without needing to hit the escape key to choose generic. The tail end extesnion reads as i386 after the kernal ID instead of "rt". 

Now I will go back and try to figure out how to watch a DVD rental on my laptop screen. Linux OS has really sharp colors compared to Windows on the same laptop.

Cayitano

---

