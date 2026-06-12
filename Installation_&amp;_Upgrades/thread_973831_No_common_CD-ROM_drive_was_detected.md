---
title: "No common CD-ROM drive was detected"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by duffrecords on 2008-11-07
I would like to install Ubuntu Studio 7.10 because the real time kernels found in Hardy and Intrepid are said to have worse latency or are more resource-hungry than the earlier kernels.  However, I can't get far in the installation process because it can't detect my DVD drive, which is a SATA device.  This is the error it creates:

No common CD-ROM drive was detected.

There is no CD-ROM and even if there were, the Ubuntu Studio installer only fits on a DVD.  I've read several forum posts which advise going into the BIOS and changing the SATA operation mode to RAID instead of IDE or AHCI.  I've tried all three options but the installer still fails to detect the drive.  The other solutions I can think of are to use an external USB enclosure for the drive (which I don't have) or to boot over the network (although the same people who posted on these forums reported the older kernel did not recognize their network card).  The installer does give me the opportunity to supply a driver via floppy disk but I don't know which driver that is or where to get it.  My DVD drive is a Samsung SH-S223Q and in Hardy Heron it is identified with no problem as /dev/scd0 and mounted as /media/cdrom0.

---

### Post by duffrecords on 2008-11-07
I also read a post that said to```
modprobe ide-scsi
``` and try to detect the drive again but I received this response:

FATAL: Module ide_scsi not found.

---

### Post by cpradio on 2008-11-24
I had this issue too, I solved it by hitting ALT + F2, Enter to activate the console, and typed the following:
modprobe ide-scsi
modprobe ide_generic

Then I went back to the first terminal, ALT + F1, and had it detect the hardware again.

---

### Post by cpradio on 2008-11-25
Just an FYI, I discovered the above only worked with Hardy Heron.  I couldn't get it to work with Intrepid Ibex

---

### Post by duffrecords on 2009-06-14
This seems to be fixed in releases such as Ubuntu 9.04 and Debian 5.0, the latter of which I'm using now.

---

### Post by RainKap on 2009-07-07
Ah, that's interesting - I had the same problem with both the 8.10 and 9.04 alternate CDs, but the 8.04 alternate CD installer detected the DVD-ROM drive with no problem (and all 3 CDs booted from that drive). I've started an install of 8.04, but I'll try aborting it and see whether your method works with 9.04.

More later...

Ian

---

### Post by RainKap on 2009-07-07
No, it didn't work on my system with either 8.10 or 9.04 :( Back to 8.04...

Ian

---

### Post by RainKap on 2009-07-08
But having installed 8.04 I was able to use the 9.04 install CD to upgrade - could have been worse...

Ian

---

### Post by yotam on 2009-09-24
> **cpradio said:**
> I had this issue too, I solved it by hitting ALT + F2, Enter to activate the console, and typed the following:
modprobe ide-scsi
modprobe ide_generic

Then I went back to the first terminal, ALT + F1, and had it detect the hardware again.

With Xubuntu karmic-alternate-i386 (alpha-6), I get this problem.
Both of the suggested *modprobe* commands failed.

---

### Post by yotam on 2009-09-26
See my solution :) in 

[http://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614/comments/8]("http://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614/comments/8")

In short:
```
 # insmod pata_opti.ko
```

---

