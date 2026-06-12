---
title: "Ubuntu and Windows 8 OS Install fail"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by johnandsonsauto on 2014-06-11
Hello,

I have a work computer that I wanted to put Ubuntu on (which was currently running windows 8). So I went to install Ubuntu via usb image. I accidentally completely installed ubuntu over win8. For some reason it wouldn't allow me to partition it separate. Either way it wasn't a big deal because I don't save many files locally. I managed to install Ubuntu but I still needed to get Win8 back on the dell pc because we run specific software. I had Dell send me a backup/reinstall disc. It came and I inserted in and it wouldn't allow me to install win8 because it said the drive was not formatted uefi. 

So I decided to (within that same menu) use the option to clear the drive completely and do a fresh install of win8. Well it still gave me the same uefi error so I decided to reboot to Ubuntu 14.04. Well because I had cleared the drive, it was no longer there. No biggy, I got my fearless USB stick with the image back out to install ubuntu yet again. However, it gets all the way through installation and then just stops. So I went from win8 only to ubuntu only to neither. I am somewhat tech savvy but not excessively and any help is HUGELY appreciated .

Thanks a million!

---

### Post by oldfred on 2014-06-11
How did you originally install Ubuntu?
Ubuntu will install in either UEFI or BIOS boot mode from its installer. And how you boot installer is how it installs.
But you have to have drive in correct partitioning.
Both Windows & Ubuntu need gpt partitioning to install in UEFI boot mode.
Both Windows on Ubuntu only boot from MBR(msdos) partitioned in BIOS mode.
Ubuntu will boot from gpt with either UEFI or BIOS if correct supporting partitions are on drive.

So if you want Windows & Ubuntu in UEFI boot mode you need drive with gpt partitioning. And if you are using a vendor recovery disk which is just an image of drive it may expect to see gpt and Windows only partitions to restore into.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by ubfan1 on 2014-06-11
Sounds like you got your disk reformatted with the legacy MSDOS partition table, and Windows wont install to that anymore.  Windows should install first, since it tends to take over the whole disk (Ubuntu at least allows you to avoid that by the "something else" choice).  Try repartitioning the disk, wipe out the existing partition table, make a new gpt table, then see if Windows will install.  The expected installation will have a small (300-500 MB FAT32 partition for the EFI bootloaders, and the rest a Windows partition (maybe a small backup partition, don't know what Windows does).  Get Windows back, then read
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

The  normal procedure is to shrink the Windows partition from within Windows, chkdsk it a few times from within Windows, turn off fast boot in the Windows power options, then try to intall Ubuntu.  It should boot from USB and start the install -- pick "something else", and make the root "/" and swap partitions in the free space.  If you run into problems, like usb won't boot (not your problem I know, but for anyone else reading), then start doing things like   turning off secure boot.  Good Luck

---

