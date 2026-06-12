---
title: "Dual-booting Ubuntu 13.04 with Windows 8 on a Lenovo U410"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2013-05-09
Hi!

I have a Lenovo U410 on which I would like to dual-boot Ubuntu 13.04.

I've run it up on a live flash drive, everything works OK.

When it comes to the actual install I'm a bit nervous as although I'm fairly competent with both Linux and Windows, I've never had a machine with SSD/HDD in a "false" raid like this before, it's only two months old, and I've never had a machine where I didn't have a Windows install disk!

The installer sees the 500 GB HDD, so I assume I can create a partition and install Ubuntu on that.

Where do I put the boot loader though? It's telling me it wants to put it on the SSD.

Is this where it should go?

Are there any detailed steps listed anywhere?

I'm assuming that because the installer sees all the partitions and disks, I don't need to turn off UEFI or RAID or anything else.....

 

Thanks!

---

### Post by arnarg on 2013-05-09
[These instructions]("http://noelkurian.tk/2013/03/dual-booting-windows-7-and-archlinux-on-lenovo-ideapad-u410/") **should** work for ubuntu as well. If you decide to try it I would appreciate if you could tell me how well Ubuntu runs on it, I'm thinking about buying myself one of those.

EDIT: To install Grub on the FAT32 partition instead of MBR you should use the dropdown list on the bottom of the window where you select which partition you want to install ubuntu on. I'm 99% sure of this.

---

### Post by oldfred on 2013-05-09
You still want to install grub to the efi FAT32 partition and it should do that automatically. But unless they have fixed something grub sees the RAID which is what Intel uses for the SRT or SSD cache for Windows. And with the RAID grub will not correctly install.

        lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

    
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

