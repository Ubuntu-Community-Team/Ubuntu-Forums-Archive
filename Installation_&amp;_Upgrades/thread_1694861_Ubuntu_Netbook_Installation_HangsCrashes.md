---
title: "Ubuntu Netbook Installation Hangs/Crashes"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Zythyr on 2011-02-25
I am trying to install on Ubuntu Netbook on my MSI Wind U123. 

I downloaded the latest version of Ubuntu Netbook and followed the proper directions to create an installation USB. 

During installation, I got up to the step where it tells me to have: atleast 2.5GB available, make sure power cord is plugged in, and that I am connected to the internet. When I click on, "Forward" to continue the installation, it just hang/freezes. 

I have similar problem when trying to install JoliCloud. When installing JoliCloud, I get up to step 3, where it asks about the keyboard. When I click "Forward", it doesn't do anything, it just hangs.

*I tired using multiple different USB drive, and also downloaded ISO file again to ensure the file wasn't corrupted.*

---

### Post by Zythyr on 2011-02-27
Help please?

---

### Post by Zythyr on 2011-02-28
I fixed this issue, I managed to successfully install both Ubuntu and JoliCloud.  The issue was that I previously had installed Mac on my netbook, formatted with GUID partition scheme. When I wiped out the hard drive by installing Windows 7, there was some corruption between GPT and MBR. This cuased GParted to keep crashing in Ubuntu and other dirsto during installation. 

I fixed the issue using GDisk based on this post: [http://georgia.ubuntuforums.org/showpost.php?p=9866163&postcount=8](http://georgia.ubuntuforums.org/showpost.php?p=9866163&postcount=8)


I am still having one issue, can someone please help me how to resolve it? 

After installation of Windows, Ubuntu, and JoliCloud. I have three partitions now with the following installations. 
Partition 1: Windows 7
Partition 2: Ubuntu 
Partition 3: JoliCloud 

JoliCloud installed GRUB as the bootloader. Every time I try to boot into JoliCloud, I get the following error: 

> Alert! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist.  Dropping to a shell!

I can boot into Ubuntu with no issue. 

When I try to boot into Windows 7, I get an error. I am sure I can fix that error by inserting Windows 7's install USB and using the repair tool.

---

