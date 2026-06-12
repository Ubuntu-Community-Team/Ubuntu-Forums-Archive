---
title: "Clean dual-boot installation of Windows 7 Professional and Ubuntu 10.4 Lucid"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by librarian on 2010-06-22
When I initially attempted a clean install of Windows 7 Professional 64 bit, then install Ubuntu 10.4 64 bit, the Ubuntu installer did not recognize the existence of the Windows installation during the GRUB setup. I went ahead and followed instructions from several places to simply let the installation do its thing, and then boot into Ubuntu, open Terminal, and run 

```
sudo update-grub
```

I encountered the same error as Beowulf.1000 at [http://ubuntuforums.org/showthread.php?p=9327075](http://ubuntuforums.org/showthread.php?p=9327075)

```
ERROR: nvidia: wrong # of devices in RAID set 
ERROR: keeping degraded mirror set
``` 

I had tried some months ago to do a dual-boot on RAID - and I never got further than screwing up my BIOS. I confirmed that all BIOS settings had RAID disabled

Finally, [http://ubuntuforums.org/showthread.php?t=1466255](http://ubuntuforums.org/showthread.php?t=1466255)

Ferrixman provided the answer. After attempting to boot the install CD with F6 options nodmraid and nomodeset - and still having the error ... and being forced to run the LiveCD
Open a terminal and do this:

```
$sudo apt-get remove dmraid
```

---

