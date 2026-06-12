---
title: "Cross Linked Files in /boot/sys"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by markdashabout on 2008-11-07
Running 8.04. 

I had problems with the default kernel (Very slow and inconsistent to boot and believe that they may have been related to SATA disks.) Was advised to try 2.6.27-8 - which initially seemed to sort out all my problems. Fast and consistent boot. A big change, as promised. There was one odd error message but I didnt worry much about that "pcspkr already installed, aborted." Something like that, soon after reading files needed to boot. 

But when I came to upgrade my system I have no end of problems. It boiled down to whenever I run apt-get install on anything, I get thousands of messages about symbolic links in the directory heirachy , we have already visited the directory to which it points. 

Inspection reveals that there are many soft links that point higher up the heirachy. 

Here is a hand-picked example: 

/boot/sys/devices/pci000:00/0000:00:02.7/subsystem points to 
/boot/sys/bus/pci

but
/boot/sys/bus/pci/drivers/Intel ICH/module/000:00:02.7 points to 
/boot/sys/devices/pci0000:00/0000:00:027

But the structures under /boot/sys/module,bus and devices seem to be full of such instances.

I suppose I have got into this state through incorrect or interrupted installation of something. 

So what to do? I have a system that works well, but I cannot find any way to upgrade! I could eliminate the cross-links using find -L to locate them but this might be a very unsafe thing to do. Is there a (fairly) safe way to do this knowing what structures should be present or should I try a complete new install. 

Advice?

Bump.

---

