---
title: "Problem with WinXP&amp;Ubuntu dual-booting"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Akula on 2006-07-04
Hello,

To this moment I have been using Ubuntu installed all alone on small hard drive, which I am using without my Windows XP hard drive plugged (and when I want to use Windows, I unplug the Ubuntu hard drive and plug in Windows hard drive... you get the point?). 

Now I would like to install Ubuntu on empty hard drive (PATA, 80GB, slave) to be used at same time with Windows (XP) hard drive (SATA, 120GB, master) with boot menu, where I could choose which one of Operating Systems would be started. 

I have tried following:
As my computer automatically boots to Windows, I used Ubuntu 6.06 Desktop CD to boot to Ubuntu desktop, and from there I did choose to make install. I installed Ubuntu on 80GB hard drive, where I had made following partitions: 
*ext3 (17GB): for Ubuntu install, 
*swap (2GB): I have 1GB of RAM, 
*fat32 (57GB): for files used by Ubuntu and Windows, like music/movie files. 

After installation seems to be succesful, I booted my computer and it booted directly back to Windows! 

**My problem is:** How can I have a list of operating systems, to choose from, when I start my computer?

PS. And if you have any better ideas for shared partition (Fat32 now), please tell me. After all, I am quite new to Ubuntu and Linux.

---

### Post by kpkeerthi on 2006-07-04
When you installed ubuntu, did you unplug the drive where XP was installed?

---

### Post by Akula on 2006-07-04
No, it has been connected all the time.

PS: As I last time installed ubuntu with option "manually edit partition table", at the end I was given list of my hard drive partitions and their mount points. 

swap mount point: swap, 
ext3 mount point: /, 
fat32 mount point: /share (this mount point I made myself)

Partitions on windows hd had also mount points at default, I have tried installing with removing mount points of windows partitions and letting them be default.

---

