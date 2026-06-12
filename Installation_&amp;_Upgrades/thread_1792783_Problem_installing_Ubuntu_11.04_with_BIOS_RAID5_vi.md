---
title: "Problem installing Ubuntu 11.04 with BIOS RAID5 via Asus Crosshair III motherboard"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by fireknigh on 2011-06-28
Hi everyone, this is my first time installing Ubuntu in a RAID system. And from what I have learned some of these motherboard based / BIOS raid systems are not true RAID setups.
 
I have 4 WD 640GB hdds (/dev/sda-sdd) setup in a RAID5 and an external 1.5TB hdd (/dev/sdf).
 
I have Windows 7 running on the RAID5 partition with no problems. I scaled the partition size down by 200 GB to reserve it for the Ubuntu installation. Unfortunatly, Ubuntu does not appear to be recognizing the RAID5 configuration but it does show all 5 drives with a single ntfs partition on my external drive.
 
I have tried installing using both Wubi and a regular installation (USB memory stick).
 
WUBI:
Looks like it installs correctly in Windows 7 and when I reboot I get the bootloader with Windows 7 and Ubuntu as boot options. When I choose Ubuntu it starts loading but then stops with an error that can not locate the Installation.ISO and halts.
 
Standard installation with USB memory stick:
The installation program loads up just fine but when I get to the step where I setup the file system it lists the 5 hard drives but the only partition it finds is the 1.5GB ntfs partition on my external drive. It doesn't recognize anything on the RAID5 setup.
As a side note, before installation the built in RAID controller/BIOS/whatever properly detects the RAID5 setup. So that should be up and running.
 
Anyway....does anyone have any suggestions on either approach? Being able to access the data on the RAID5 partition is not very important to me so I am very tempted to just install Ubuntu on another USB drive and just plug it in when I need to do development work. But that doesn't get me to using Ubuntu as my primary desktop.
 
Any thoughts?
 
 
Thanks,
Chris

---

### Post by fireknigh on 2011-06-29
Well, I'm not going to mark it solved. But I am up and running with Ubuntu 11.04 installed on an external USB drive. Not exactly an optimal solution since my BIOS is now functioning as my boot loader by changing the boot order. :)
 
Chris

---

### Post by psusi on 2011-06-29
Raid5 is not currently supported on Fakeraids.

---

### Post by dabl on 2011-06-29
> **fireknigh said:**
> 
 
Any thoughts?
 


Couple of 'em:

(1) If RAID is truly important for your installation, then the best solution is to install a Linux-supported RAID controller, such as these:  [http://www.3ware.com/products/serial_ata.asp](http://www.3ware.com/products/serial_ata.asp)

(2) The BTRFS filesystem is still considered in "experimental" status by Debian, although it is supported in both Debian and Ubuntu.  And they have not finished and released a filesystem checking/fixing utility for it yet. Since you have a handful of matched drives, you might consider looking into a multi-drive btrfs filesystem.  In default configuration on a multi-drive installation, btrfs stripes your data, but mirrors the metadata.  It's not the same as RAID5, exactly (but it will do a RAID 10), but it's a pretty interesting new filesystem, IMHO.  I personally have had a pair of WD1002FAEX (6Gb/s) drives in a btrfs filesystem since December on a Debian system, with no ill effects.  Here's the wiki pages you should review, if interested:

[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

[https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

[https://btrfs.wiki.kernel.org/index.php/Gotchas](https://btrfs.wiki.kernel.org/index.php/Gotchas)

---

### Post by psusi on 2011-06-29
> **dabl said:**
> 
(2) The BTRFS filesystem is still considered in "experimental" status by Debian, although it is supported in both Debian and Ubuntu.  And they have not finished and released a filesystem checking/fixing utility for it yet. Since you have a handful of matched drives, you might consider looking into a multi-drive btrfs filesystem.  In default configuration on a multi-drive installation, btrfs stripes your data, but mirrors the metadata.  It's not the same as RAID5, exactly (but it will do a RAID 10), but it's a pretty interesting new filesystem, IMHO.  I personally have had a pair of WD1002FAEX (6Gb/s) drives in a btrfs filesystem since December on a Debian system, with no ill effects.  Here's the wiki pages you should review, if interested:


If you are going to do that, you might as well just use mdadm software raid with a stable filesystem, but it sounds like he wants to maintain compatibility with Windows, so neither is an option.

---

### Post by fireknigh on 2011-06-30
Thank you for the suggestions!
 
Performance/redundancy isn't too high on my priority list since my goal is setting up a test development environment that is easier to work with compared to the hosting service I currently subscribe to. 
 
Because all of the data I care about is being backed up on a different external drive, I can still access all of that in Ubuntu. The only real complaint I have now is having to modify my BIOS settings to pick an OS. On the plus side, I can now unplug my Ubuntu hdd and plug into into my laptop while on the road. 
 
Although no one suggested it, the easy solution would be to make my Ubuntu hdd internal, but I maxed out the SATA connections on my motherboard, oh well.
 
When it is time to upgrade in a year or so, I'll buy a real raid controller and do it right. For now, the cost/benefit isn't worth it to me. For anyone curious, I ran some disk analysis on the BIOS raid when it was setup as a 2 disk RAID 0 and as a 4 disk RAID 5 and the performance scaled exactly as expected (133MB/s and 200MB/s write speed respectively).  I don't have any single drive baseline figures to compare those against but I have seen ~63MB/s posted on techreport.com. No numbers on CPU usage during transfer.
 
Chris

---

### Post by YesWeCan on 2011-06-30
You should be able to chain load your Ubuntu disk from your Windows boot loader. Using EasyBCD for example.

---

