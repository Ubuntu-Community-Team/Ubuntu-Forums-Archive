---
title: "Problem with GRUB"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by g02h31l on 2007-05-07
I just added a second hard drive to a computer and would like to have Windows on one drive and Ubuntu on the second.  Windows was already installed on the first drive and had been working fine.  I added a second drive to the computer, which was connected to the second IDE port on the motherboard.  If it matters, I also added a CD-ROM drive to the same cable as the new hard drive (Windows had been installed with a network image).  I installed Ubuntu successfully.  When I restarted the computer, the screen showed Grub Error 17.  I messed around with things, changing the cables on the motherboard and the boot sequence.  The best this did was give me Grub error 25.  Can anyone help me with this problem?  What should I do?  I can no longer even access windows, even if the second hard drive is removed from the computer.

Thanks!

---

### Post by kyphi on 2007-05-07
First of all, both hard drives should be connected via one IDE cable with one drive set as master and the other as slave.  Your CD drive goes on a separate IDE cable.

Error 17 refers to GRUB not being able to mount a partition.
Error 25 refers to a disk read error.

It would appear that grub has been improperly installed.  You can rectify this by reinstalling Ubuntu to the section that installs GRUB.  Windows has to be installed first (because it does not recognise other operating systems) whereas Ubuntu will recognise Windows and incorporate it into the boot loader.  The bootloader must be installed on the Windows partition.

You can recover Windows by using the Windows install disk and opting for "repair".

Another solution would be to burn a Super Grub Disk obtainable from [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by zvacet on 2007-05-08
[http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives]("http://ubuntuforums.org/showthread.php?t=275728&highlight=two+drives")

---

