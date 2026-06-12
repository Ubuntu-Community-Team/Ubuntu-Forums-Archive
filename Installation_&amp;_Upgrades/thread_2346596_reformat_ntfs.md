---
title: "reformat ntfs"
date: 2016-12-16
forum: Installation &amp; Upgrades
---

### Post by pete1977x on 2016-12-16
I want to install  Windows 10 over Ubu. Later I will install Ubu alongside later. I booted from USB with Ubu on it and selected Try Ubuntu. Then I used GParted to reformat to NTFS which is a requirement. I have Windows USB  thumb ready to go. I unmounted the bigger partition and tried to reformat to NTFS..the screen froze and fractiled. Then I shutdown and rebooted and Ubu came on as usual. What did I do wrong?

---

### Post by sudodus on 2016-12-16
If you intend to use the whole drive, you need not format anything. Windows can do it automatically (it overwrites the drive with its own partitions and file systems). This is the easiest option. It works well to shrink the Windows partition from Windows (and leave unallocated disk space).

After that you can boot rom an Ubuntu install disk and running live 'Try Ubuntu'. Gparted is there for you to create partitions for Ubuntu.

-o-

If you want to prepare now for a dual boot and what to prepare for it, you should know what Windows needs and provide it. You can do that when the computer is booted from an Ubuntu install disk and running live 'Try Ubuntu'. Gparted is there for you. But is is more difficult, and we are Ubuntu people and not the best experts on Windows ;-)

---

### Post by Mark Phelps on 2016-12-17
The BEST way to install a recent Windows version is, when you get to the screen that lists the drive partitions, choose the one you want to use and have the Windows installer reformat it -- even if you already formatted it yourself.  This insures the proper formatting for the partition.

---

