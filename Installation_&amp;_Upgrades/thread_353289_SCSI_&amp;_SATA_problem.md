---
title: "SCSI &amp; SATA problem"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2007-02-04
I installed Kubuntu to my IDE drive and my SCSI hard disk was visible in fdisk and I formated it and mounted it just fine when I first installed Kubuntu a few weeks ago.

I got a SATA drive and added it to my system and then reinstalled Kubuntu (due to ATI Radeon video issues).  I can no longer see the SCSI drive with fdisk.

Any suggestions?

Bob

---

### Post by dcstar on 2007-02-04
> **bsprowl said:**
> I installed Kubuntu to my IDE drive and my SCSI hard disk was visible in fdisk and I formated it and mounted it just fine when I first installed Kubuntu a few weeks ago.

I got a SATA drive and added it to my system and then reinstalled Kubuntu (due to ATI Radeon video issues).  I can no longer see the SCSI drive with fdisk.

Any suggestions?

Bob

In a terminal, do:
```
sudo lshw
``` and see if you can identify all of your drives.

---

### Post by bsprowl on 2007-02-06
I had many issues with Ubuntu besides this one.  

I changed video cards and reinstalled using Ubuntu 6.10 and the problem is one of those that just went away.  

I can see all of by drives including both sata and scsi drives.
 
I looked "lshw up in "man".   Very useful command; it is not in any book I have.  It will take some time to learn how to read the output. 

Thanks.

---

