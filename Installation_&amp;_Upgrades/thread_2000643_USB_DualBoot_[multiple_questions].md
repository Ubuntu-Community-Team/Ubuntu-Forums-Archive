---
title: "USB DualBoot [multiple questions]"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by LucienMidnight on 2012-06-09
I am planning on using a 32G USB to dual boot linux. My previous setup on the PC was Windows // Ubuntu // Debian // swap. On my new laptop (for various reasons) I want to dual boot linux from USB and still include a space for files. Based on what I have read (including a similar thread here) I am planning on partitioning for Storage // Ubuntu // Debian with full installs rather than live/persistent version.
 
How will treating both Ubuntu and Debian as 'normal' installs (including seting up Grub) fail with regard to default directories/files?
 
Best way to manage files shared from Ubuntu & Debian (casper-rw?)? FAT32 or a seperate partition?
 

Any suggestions for swap? On Storage, or using random HDD Drives (could be dangerous)?
 
I am assuming better speed with a full install over persistent, any idea on wear and tear on flash memory, and what best to use to backup/move to a new drive when neccessary? (USB will have lifetime guarantee anyway)
 
I am planning on using VirtualBox, I think I should be able to run in Windows or boot directly into the OS with this setup (there is a tweak for running from USB). Can anyone confirm this? I currently see no reason why not, although most articles I have read use Live distros.
 
 
This is a project to see whether I can put this together and to make linux available so I can start making use of it (either directly or through VirtualBox). I'd like to see whether my concept is possible - I see no reason why not as USB is simply an external drive, but mainly I'm trying to find what pitfalls and hazards I may come across.
 
Thanks,
Lucien M

---

### Post by oldfred on 2012-06-09
Is this a USB flash drive? USB is slower than SATA port and Flash is slower than hard drive particularly writes. I have a full install of Ubuntu in 8GB on my 16GB flash with the rest for data. No swap at all with 4GB but I try not to load too many apps at once. It is more for testing with laptop and emergency boot.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Install to USB flash is not different than any install to a second drive, but with flash you want to change some settings to reduce writes for speed & life. Settings for flash are similar as settings for SSD, but flash does not support all the features (nor speed) of a SSD.

---

### Post by LucienMidnight on 2012-06-10
Thanks,
 
I'll start reading through these while I wait for a larger USB stick to arrive from eBay. Sounds like I'll do the same install I did last time with a few tweaks for USB.
 
I'm not too worried about speed but obviously I would like it to be reasonable for using something so small. :) I'll have to look at what setting need changing for limiting write so I guess I'll start googling SSD setups.
 
Many thanks again.

---

### Post by C.S.Cameron on 2012-06-10
Reports of flash drives failing due to running Ubuntu are extremely rare. The only time I have heard was from a person running his server on a cheap, give away flash drive.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by LucienMidnight on 2012-06-11
That's good to know. :)
 
I'll mark it as solved for now, thanks.

---

