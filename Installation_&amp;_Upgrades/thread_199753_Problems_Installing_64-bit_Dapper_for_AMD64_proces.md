---
title: "Problems Installing 64-bit Dapper for AMD64 processor"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by cgeddie on 2006-06-19
Hi Folks,

I downloaded and burned the AMD64 version of Dapper Drake, 6.06, and tried to use it to install onto an empty partition on my boot drive. My boot drive, however, is a mirrored SATA RAID, and installation was not straightforward.

First I used the package manager on the live CD to install dmraid, then tried to use the installer GUI on the live CD to install Dapper onto the empty partition on my boot drive.  This didn't work, although (quite unhelpfully) I cannot remember the exact way in which this failed.

I eventually found this web page ([http://ubuntu-in.org/wiki/SATA_RAID_Howto](http://ubuntu-in.org/wiki/SATA_RAID_Howto)) and followed the instructions there.  The only thing I did differently from the instructions on this web page was that I installed the **linux-amd64-generic** package instead of the linux-386 package with apt-get.

I have GRUB configured now, and can use it to boot into the WinXP-SP2 partition on the saim RAID array, but I cannot boot into Ubuntu.  When I choose to boot Ubuntu 6.06, it immediately restarts my machine, going through all the standard power-up sequence and landing me back at the GRUB menu.  Same if I choose the recovery mode item in the GRUB menu.  The memtest menu item works fine.

**MAIN QUESTION: How can I get Ubuntu 6.06 running in 64-bit mode on my machine?**

Secondary question:  By specifying _only_ the kernel package as 64-bit when I followed the install instructions at [http://ubuntu-in.org/wiki/SATA_RAID_Howto](http://ubuntu-in.org/wiki/SATA_RAID_Howto), have I ended up with a system half in 32-bits and half in 64-bits, or is there some other reason for my failure to boot Ubuntu on my machine?

If you need other info, please feel free to email me.

Thanks in advance for your help! :)

---

