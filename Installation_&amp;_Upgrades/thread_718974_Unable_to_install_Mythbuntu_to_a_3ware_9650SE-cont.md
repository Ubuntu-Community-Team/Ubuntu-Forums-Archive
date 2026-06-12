---
title: "Unable to install Mythbuntu to a 3ware 9650SE-controlled RAID 5"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by bwish on 2008-03-08
Hi everyone. A complete Linux newbie here, in desperate need of some help...

I'm trying to set up a new server/NAS using Mythbuntu 7.10, with a RAID 5 thru a 3ware 9650SE card. I'm able to boot into Mythbuntu with the LiveCD, and then when I finish entering all of my install choices and actually begin the install, the install APPEARS to freeze during creation of the file system. I come back to it a few hours later and it says it's done, and ready for Step 15 of 15 (MythTV configuration). Upon reboot, my BIOS apparently can't find the OS, and I just get a black screen. This has happened twice.

My system details:
ASUS M2A-VM motherboard
AMD Athlon 64x2 4800+
4GB of Crucial DDR2 800
3ware 9650SE controller card
4 x Samsung HD501LJ (500GB) HDDs

After assembling all the hardware, I was able to get into the 3ware 3BM, and configure the RAID 5 successfully. I booted into the LiveCD and attempted to load the 3ware driver from [http://www.3ware.com/kb/article.aspx?id=14546](http://www.3ware.com/kb/article.aspx?id=14546), to no avail (Linux newbie, remember?). Then I read on the 3ware website that 2.6.14 kernels and newer have native support for the 9650SE, so I went ahead and tried the install, resulting in the problem described above.

After scouring the forums, it turns out that there might be an issue with the ATI SB600 southbridge on my motherboard, when using 4GB of RAM or greater, so I removed one of the DIMMs, repeated the install, and repeated the problem above.

I've sifted through the forums, but haven't had much luck on finding a way to fix my particular problem. I've also tried to go back and reread the 3ware user's manual (which is more helpful for RedHat and Fedora installations). I'm just not wise enough to know how to proceed.

I guess I'm pleading for help here, my wife is ready to hang me for all the time I've been spending trying to get this new computer working!

This is a duplication of my original posting: [http://ubuntuforums.org/showthread.php?t=718968]("http://ubuntuforums.org/showthread.php?t=718968")

---

