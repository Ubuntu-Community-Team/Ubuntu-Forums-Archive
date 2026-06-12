---
title: "Major problem after failed Windows8 install, computer can't boot anything."
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by thejan2009 on 2012-07-06
I've tried to install  Windows 8 alongside my Ubuntu 12.04 installation. Yeah, I was aware of  all **** that could be inflicted, but I didn't think it'd break my  system to this extent.


  With a successful previous dualboot installation on my spare computer  I was encouraged to install Windows 8 on my main computer. I made a  backup of MBR and a LiveCD Ubuntu, just in case. When the installatin started, it looked like nothing is wrong. I  inserted product code and made a 200 GB partition (from Windows  installer). It seemed strange that it already took about 10 minutes. 

Then the computer suddenly rebooted and now it won't boot. It shows me  the Grub rescue promt. ls command shows three partitions: hd0 ;  hd0,msdos5 ; hd0,msdos1. All partitions have "unknown filesystems.


  When I boot via USB drive, it gives me kernel panic, apparently there  is not enough memory. I tried with at least 5 different LiveUSBs.


  Any help would be much appreciated.

---

### Post by darkod on 2012-07-06
I think touching it with the win8 installer might have messed it up. You are forgetting that windows doesn't understand linux partitions, so it can really do damage manipulating them.

Did you have unallocated space created and only tried to create a primary partition in it? Or you tried to resize one partition so you can create unallocated space for win8?

Testdisk might be able to bring the old partition(s) back:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can run it from live mode, using the live cd.

---

