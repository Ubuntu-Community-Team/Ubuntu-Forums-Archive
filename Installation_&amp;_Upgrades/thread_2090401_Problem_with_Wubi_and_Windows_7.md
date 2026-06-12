---
title: "Problem with Wubi and Windows 7"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by minsc1 on 2012-12-02
Hi,

I would like to install Ubuntu 12.04 on my computer from Windows using Wubi, but I have a problem with it. Firstly I mount a CD image in a virtual drive via Daemon tool. Next I start Wubi, fill all installation fields, and then I click next. Then Wubi starts to extract files, etc. After Wubi unpack system kernel new window should appear in which I will be asked to restart Windows, but that does not happen. Wubi window disappears and exit. When I check the partition on which I installed ubuntu there are some uncompressed files, but after restarting the computer, nothing happens. GRUB not showing up and Windows normally starts. I also tried to install Ubuntu 12.10, but the same thing happens. I have Windows 7 Home Premium Service Pack 1. In attachment I enclose screenshots of last window with Wubi installation and what it unpacked to disk. Partition on which I  install Ubuntu is a dynamic disk. Does this have any effect on the installation? If not, why I can not install the system?

---

### Post by Cheesemill on 2012-12-02
As far as I know you can't install Ubuntu on a system that uses Windows dynamic disks.

---

### Post by Mark Phelps on 2012-12-02
Dynamic disks generally happen when you already have the limit of 4 primary partitions on a drive and you FORCE the creation of another partition.  Linux can't use Dynamic Disks -- these are proprietary to MS.

So, what did you do to cause this? Did you force the creation of another partition and then decide to install using Wubi anyway? Wubi doesn't create a new partition; instead, it installs inside an existing Windows partition.

I would suggest you do the following:
1) Go into Win7 Disk Management and confirm that you have more than four "drives" (what MS calls partitions)
2) If one of the "drives" is empty, then remove it
3) Google for Minitool Partition Wizard Boot CD
4) Download and burn that CD
5) Boot from that CD and use the menu option to convert Dynamic Disks to Basic

If you STILL then want Ubuntu on your PC, consider using Wubi but do NOT force the creation of another partition.

---

