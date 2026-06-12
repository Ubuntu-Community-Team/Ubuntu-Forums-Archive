---
title: "Can I install Ubuntu on HDD+SSD RAID storage?"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by rkashby on 2012-10-09
As described in a separate thread here...

[http://ubuntuforums.org/showthread.php?p=12286714#post12286714](http://ubuntuforums.org/showthread.php?p=12286714#post12286714)

...I just bought a Lenovo ultrabook  (with pre-installed Windows 7) and have been unable to set up dual boot during Ubuntu 12.04 installation. The Ubuntu install does NOT recognize the presence of Windows 7 on the machine (at which point I aborted the install). Apparently the problem (or a big part of the problem) is that the machine has a RAID storage mode and has an HDD + SSD combination, as opposed to just HDD.

Don't really understand the storage issues, but I am wondering if this storage configuration will allow me to install Ubuntu 12.04 IN PLACE of Windows 7. After which I could install VIrtualBox and run Windows 7 virtually. (I need Windows for MS Office.)

Prior to running into the problem with the dual boot installation, I would never even have thought to ask this question. But I DO NOT want to wipe out Windows 7 by installing Ubuntu, and then discover my Ubuntu install doesn't work because of the storage configuration.

---

### Post by oldfred on 2012-10-10
While Dell examples the process should be the same:

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

You remove the RAID and install Ubuntu either to SSD or change partitions around to open one primary to convert it to the extended partition. Ubuntu works from logical partitions in the extended without issue. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

While for HP, the issues are the same. Some vendors may handle Vendor recovery somewhat differently, you need to check you manual or Vendor Web site.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by ruehara on 2012-10-10
FWIW I configured the BIOS on my Dell XPS 430 to look for an external SATA drive as the first stop in the boot chain, then the internal drive.

I have Ubuntu installed as the only O/S on the internal drive and Windows 7 on the eSATA drive.

If I turn on the eSATA drive before starting up the computer, it behaves just like a dedicated Windows 7 device, but if I boot up without the eSATA drive powered, then it boots up Ubuntu. 

It's a very painless and non-damaging dual boot system

---

