---
title: "Installer Not Seeing SSD on Lenovo U310 IdeaPad"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by idsfa on 2012-07-07
I was having problems installing Ubuntu (12.04) on my brand new laptop, as the installer program was not offering the 32G SSD as an option for the installation.

My desired config was to have the SSD for the OS and the larger standard drive for things like my encrypted home directory, the apt package cache, etc etc

I was eventualy able to get the SSD (/dev/sda) to show up in the installer by making two changes:

1) In the BIOS, changing the drive controller from RAID to AHCI mode

2) Using gdisk(8) instead of cfdisk(8) to write a new partition table on the SSD

I must confess that I did both before trying to install again, so I do not know if one of those would be sufficient to fix the problem or both are needed.

---

### Post by MrGrieves09 on 2012-07-09
Hello,

This is quite interesting.

I'm thinking of buying the laptop but I haven't had any informations about how well it works with ubuntu.

I've posted a thread on the french ubuntu-fr forum but no real answers...

Could you tell me if everything works fine for you ? 
How long does your battery last ?

Thanks for your contribution.

---

### Post by Richbuntu on 2012-07-10
I'm also interested in buying the Lenovo U310 IdeaPad, it looks like a really nice laptop.

I was thinking of making a dual boot between Windows and Ubuntu on this laptop.
Do you think I can install Ubuntu only on the 32GB SSD Drive without messing up Windows that will run on the HDD drive?
Would Wubi would work fine on this laptop?

Thanks,
Elad.

---

### Post by idsfa on 2012-07-22
Most of the hardware works fine for me.  I added the xorg-edge PPA to get the latest 3D accelleration (introducing a known bug where Unity does not display icons on the dock).  I *had* suspend working fine, but right now it is locking up if I suspend more than 5 minutes ... may be related to the xorg-edge kernel.  I get several hours of battery life (indicator currently says I have three and a half more hours left).

If you don't need 3D accelleration, pretty much everything works out of the box.

The machine shipped to me with the SSD as drive D: for windows, so one could easily copy all of the content onto the standard drive and repurpose the SSD for linux.

---

### Post by idsfa on 2012-07-22
Just confirming that when I back out the kernel from the xorg-edger PPA and use the stock precise kernel, suspend works just fine.

I've been using it unplugged for three hours this afternoon, streaming Amazon Cloud Player over the speakers and playing Psychonauts.  Still about an hour's life left in the battery.

---

### Post by jachk on 2012-11-26
Hi all,
I'm going to buy the Lenovo Ideapad U310 with the double hdd (500Gb+32gb SSD).
I would like to know whether is possible to install Ubuntu 12.10 on the SSD hd.
I would like to have:
Ubuntu 12.10 on the SSD drive + home partition on the 500 Gb drive
Windows 7 (that come preinstalled) on the 500Gb drive.

I read that I have to disable the IRST in the BIOS (but elsewhere I read is also ok to disable it via software, in the preferences of IRST).
What should I do? Is it possible to preserve the Win 7 installation?

Thanks for the support.
Regards,

Jack

---

### Post by oldfred on 2012-11-26
I do not have Intel, but saved these threads as it seems a common issue. Since Intel, vendor of system does not matter too much.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> 
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   
You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

