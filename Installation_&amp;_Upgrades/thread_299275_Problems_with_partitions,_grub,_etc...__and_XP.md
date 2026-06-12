---
title: "Problems with partitions, grub, etc...  and XP"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by AG28 on 2006-11-13
Look for some help on a dual boot I tried to accomplish.  I've run Debian for about a year now and love it.  Only problem is that I have a dedicated system set up as a server.  I wanted a good, practical desktop version of linux so I went with Ubuntu.  I won't bore you with all the set-up details, but I do have a unique problem.  I usually use grub as my bootloader.  I've had no problems using it to dual boot linux/windows OS's.  Until now.  I have a SATA drive that holds my XP install.  I have two IDE drives that are "storage" drives.  I repartitioned the SATA drive and was able to install Ubuntu.  When I placed grub into \dev\sda\, it killed ntldr.  Not only that, it wouldn't boot into Ubuntu.  (version 6.10).  I could do the manual edit thing, and was able to get into Ubuntu, but I had to have my XP box back.  I loaded the XP  
setup disk and fixboot and fixmbr, and my XP box is back and happy.  
After all this typing, my question is, what bootloader/grub/ntldr
trick can I use to dual boot.  I have to fully installed systems but no way to get to one without messing the other.  Thanks for any help!

---

### Post by rjean on 2006-11-13
I dual boot with XP. However I have Partition Magic 8 for Windows - which includes "Boot Magic". I set up a separate boot partition in Ubuntu, in which I installed grub. Then Boot Magic allows me to select which OS to boot. I also have Gentoo installed in the same manner. I also found that Boot Magic would not install in an NTFS partition so I had to put it on it's own Fat32 space on my second hard drive, which is also where Ubuntu is installed.

---

### Post by AG28 on 2006-11-13
Hmmm, that's interesting.  I read some other posts where a 3rd party product was used to dual boot.  Is this something with just the Ubuntu distro?  I had no problems dual booting with Debian and an installed version of Knoppix and XP.  Used grub on both.

---

