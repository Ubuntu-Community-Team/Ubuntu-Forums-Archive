---
title: "windows boot problems"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by joshua.rh on 2010-05-01
Hello everyone,
    I just got the new ubuntu install (great btw) annnnd my windows  boot loader is messed up.  I installed grub on /dev/sda4 and chameleon  in the front again and I'm getting this error: [http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391)  .   My hard drive is set up like this:

/dev/sda
    EFI             /dev/sda1
    Windows    /dev/sda2
    OSX           /dev/sda3
    Ubuntu       /dev/sda4
    data            /dev/sda6

When I try to boot either of these discs: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)  I get this error message: [http://support.microsoft.com/kb/925762](http://support.microsoft.com/kb/925762)  

The problem is also described here: [http://www.insanelymac.com/forum/index.php?showtopic=165878](http://www.insanelymac.com/forum/index.php?showtopic=165878)   Though because I can't do anything with the repair discs I can't  complete the process.  I've also tried various things with the boot  flags on the EFI/Windows partitions, to no avail.

I realize this isn't really an Ubuntu problem, but there aren't really and good windows forums that I could find... so here it is.  Let me know if you can help, thanks,

Josh

---

