---
title: "Only 2 of 3 HDD visible during Installation"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by mr.Lauren on 2011-03-01
Is this situation normal that I observed during Installation?

I booted into the Ubuntu 10.04 live disk, and first checked my system with gparted.  It presented the system as expected, a 40G IDE, a 160G IDE and a 500G SATA HDD.  Then I opened the Installation application, but when I got to the Partition section, the appearance was altogether different, and it only showed 2 HDD, the 40G and the 500G, but not the 160G that I wanted to access.  The 40G has the MBR, the 500G is my active HDD.

So I booted into MEPIS, which I am also studying, and again first checked the system with KDE Partition Editor.  It also presented the system as expected.  I opened its Installation app., and when I got to the partition section, it was using the KDE Part. Ed., and all the HDD's were shown.  So I resized 2 of the 4 partitions to allow more space, added a swap partition, and then backed out of the installation.  By the way, the resizing does not appear to have been graceful - the boot sequence seemed quite "excited" when I tried to boot the re-sized SLED11.  I thought for a minute I'd destroyed my working system, but it recovered.

In case more information is needed about my system, it is an "ASUS M4A785TD-V EVO" MBd, with an AMD AM3 processor.  The 40G has Win98 & Debian5 installed.  The 160G has Libranet3, Debian4, and SUSE Linux Enterprise Desktop 11 (SLED) with root & /home partitions installed.  This SLED11 I had made too small.  The 500G has SLED11 with root & /home installed.

I would like to move away from the RPM environment.  I went there when Debian5 display function could not handle the ASUS MBd built-in video, "ATI Radeon HD 4200 GPU".  The siren song was that I could get active support help.  The downer is that when I added a couple apps not from their repository, they would no longer support it!  Another factor is that I have VMware to provide Win98 for old software that I need.  Ubuntu seems to support that, but MEPIS probably does not, unless, maybe, you're a Geek, which I am not.

Do you think what I saw is normal?  My forum search did not turn up anything quite like this so I wanted to ask.

Thanks.

---

