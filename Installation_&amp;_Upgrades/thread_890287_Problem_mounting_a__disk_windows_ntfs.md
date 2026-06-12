---
title: "Problem mounting a  disk windows ntfs"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by fcubas on 2008-08-14
Hi all, i just get in a new problem, I have a windows xp system, this system cannot be booteable and i need to recover some files. I start the ubuntu live 5.10 and I already mount the disk in the /media/hd2a. The problem is when I try to copy this to another location this is imposible. The system said that I dont have enough permissions. I already try to change the permission with the regular user and the root user and also the system dont let me do it.

Regards

---

### Post by ezsit on 2008-08-15
Most WinXP installs were done with NTFS as the filesystem. Ubuntu 5.10 did not have the NTFS drivers available I believe. The first version of Ubuntu that I successfully used to read and write to NTFS partitions was version 8.04 (the most current).

If you do not have the time or bandwidth to download the latest version of ubuntu, I have found SLAX to be fully capable of automounting NTFS partitions from live boot. SLAX can be found at [www.slax.org](www.slax.org). It is only a 200 mb download and boots very quickly. Just hit enter at the boot menu and you should be good to go. SLAX uses KDE, so if that is not a problem, I'd give it a shot. I always carry a SLAX cd around when I do computer repair/data recovery. Great tool.

---

### Post by fcubas on 2008-08-15
ezsit, thanks for your help, I just download the ubuntu 8.04.04 and this work perfectly, I already bakcup the information and reinstall de machine... thanks in advanced

---

