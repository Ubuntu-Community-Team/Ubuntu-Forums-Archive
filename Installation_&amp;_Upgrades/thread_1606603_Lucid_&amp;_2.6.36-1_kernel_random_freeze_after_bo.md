---
title: "Lucid &amp; 2.6.36-1 kernel: random freeze after boot"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Aranmanoth80 on 2010-10-26
Hello all,

I am using Ubuntu Lucid Lynx 10.04 (64 bits) in my Asus U30JC laptop (Core i3 M350, intel 4500MHD + nvidia 310M with nvidia Optimus, 4GB RAM).

I am content with Lucid and I don't want to upgrade to 10.10 for now. However I read that the new 2.6.36 kernel has some good improvements, such as improving system interactivity while intensive I/O (such as copying large files), and improved energy management for i3/i5 processors (which I hope translates into more battery time, which is a problem of Ubuntu vs Win7 in my laptop).

I discovered I had 2 options: compile the kernel myself, or use the [Ubuntu Kernel PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa") (maintained by the Ubuntu Kernel Team). I decided to use the PPA, so I added it to my software sources and installed the **generic**"linux-lts-backport-natty" kernel (2.6.36-1).

Package installation went fine, and after reboot, I could log in to the desktop no problem. Everything seemed fine, but after a few minutes, the system freezes completely: mouse did not move, none of the indicators moved, even Ctrl + Alt + F1 did not work.

And here are the questions, to be answered at your choice :P
Anyone has had a similar experience?
Should I try to compile the kernel instead?
Where is the log file where there might be a message related to the freeze?
Do you think that the kernel developers would try to fix a bug that probably only affects people running the 2.6.36-1 kernel on a distribution that was not built around it?

Thanks for reading :)

Cheers, David

---

### Post by KernelSpace on 2010-10-28
Welcome to the kernel/xorg freeze club
 
See here for more details. for a 1000+ posts or so
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
 
Most importantly this seems to be affecting quite a few distros if you search the net

---

