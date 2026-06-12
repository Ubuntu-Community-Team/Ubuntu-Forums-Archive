---
title: "New Install - GRUB - Restart"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by Just4Fun20 on 2007-07-02
I've an old machine which was formerly running Red Hat 7.3.  It's just a file server for my house.  I'm trying (using a new hard drive) to install Ubuntu Server (both 6.06 and 7.04) but I get a strange error.  The installation completes and I remove the CD.  The system reboots into GRUB, the GRUB commands run but then the system restarts and goes back into the hardware splash screens.  Left unattended it would just sit there looping like that all day.  

I have added ACPI=FORCE to the GRUB configuration but with or without it makes no difference.  

I've configured the partitions myself and I've let Ubuntu configure them, both with the same results.  

Any thoughts on how to troubleshoot this?  Any thoughts on what might be wrong?

It's an old 400Mhz AMD machine with 320MB of memory.  Memory tests run clean.  

Thanks for any help.

---

### Post by confused57 on 2007-07-02
It's a common problem installing with the server cd on older hardware:
[http://ubuntuforums.org/showthread.php?t=490282](http://ubuntuforums.org/showthread.php?t=490282)

---

