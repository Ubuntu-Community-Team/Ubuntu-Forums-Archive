---
title: "Start-up and Partitioning before Ubuntu installation"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Jason_K_M on 2010-03-16
Hi
 
I have recently formatted my hard disk and logically enough, upon start-up, the computer reports that no operating system is present. However, I would like to start-up the computer, examine and partition the hard disk in advance of re-installing Ubuntu. Could anybody suggest what I could use to start the computer, such that I am able to start a shell and run basic commands such as 'df' and 'parted'.
 
Thanks in advance for your help.
 
Jason

---

### Post by dstew on 2010-03-16
You can run an Ubuntu Live CD, and use Synaptic to install gparted. (Yes, you can install and run programs on a running Live CD system ... they will disappear when you shut down though, because the Live CD file system is present in RAM instead of on a hard disk.) Parted and df may already be on the Live CD.

You can also download and burn a [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). I have found this very useful for partitioning ahead of installation.

---

