---
title: "VirtualBox 2.02 &amp; 8.04LTS (Kernel 2.6.24-21-gen i686"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by lkraemer on 2008-10-18
I am running Ubuntu 8.04 LTS, and have VirtualBox v2.02 installed on Kernel 2.6.24-19-generic on i686.  I just upgraded 8.04 LTS, and the latest Kernel is now 2.6.24-21-generic in i686.  VirtualBox starts like always but when I click on WinXP it says Spawning process, and never starts XP.  I can boot, select the previous Kernel version with grub, and WinXP comes right up.  I have DELETED the WinXP Virtual Machine, and rebuilt it for the new Kernel.  The same VDI file was used on both Kernel Versions.  Is anyone else having this problem with the updated Kernel?

Suggestions?

Compaq V5201US with AMD Sempron 3300+, 2 Gig Ram, 160 Gig Drive.
WinXP Virtual Machine base memory is 796Meg, remaining is for Ubuntu.

Thanks.

LKraemer

---

### Post by lkraemer on 2008-10-18
SOLVED!

sudo /etc/init.d/vboxdrv setup

lkraemer

---

