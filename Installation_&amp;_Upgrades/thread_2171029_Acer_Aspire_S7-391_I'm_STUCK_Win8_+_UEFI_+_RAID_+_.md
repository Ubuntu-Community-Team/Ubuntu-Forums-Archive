---
title: "Acer Aspire S7-391 I'm STUCK: Win8 + UEFI + RAID + Secure Boot + Fast startup"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by Axx83 on 2013-08-28
The beautiful new ultrabook is a Microsoft trap. Please help me have dual boot for Windows 8 and Ubuntu.

I tried installing Ubuntu with this guide [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) by resizing in Windows the partition, then going in the Bios and turning off UEFI. I tried to turn off Intel SRT in the bios but it did not seem to work, anyway I kept on installing Ubuntu and chose the "something else" option, selected just /sda as the boot partition and in the end it said I either had to erase something or not install the bootloader.

Needless to say Ubuntu or windows did not load, so I installed and tried Boot-repair, did all standard and no success.

I turned on UEFI but still windows or Ubuntu would not load, I reinstalled Ubuntu in UEFI and selected this time the UEFI partition for boot. After the install of course the system would not load, just a "no system available please reboot" or something like that.

I retried boot-repair, this time with UEFI, but after it says all is cool, the system is still not recognized and nothing can be booted.

The log is this [http://paste.ubuntu.com/6038259/](http://paste.ubuntu.com/6038259/)

What should I try ? How do I disable the raid? Do I have to cancel windows?

The ultrabook has of course no CD (it's 2013 for god's sake) and no windows 8 cd came, how do I make a USB backup or recovery if I can't boot in windows? If I don't have a recovery usb I can't erase the disc and install Ubuntu overall.

Please help

---

### Post by oldfred on 2013-08-28
Boot-Repair is still showing the "RAID" that Intel SRT uses. You need to make sure it is off and then run this to remove meta-data on drive. Examples from other brands should be similar as it is Intel SRT.

       Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

You also will have video issues. Look into bumblebee. But you may need nomodeset to boot if nVidia is default video.
See link in my signature for all the Ultrabook type issues.

Other Acer
      
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by Axx83 on 2013-08-29
> **oldfred said:**
> Boot-Repair is still showing the "RAID" that Intel SRT uses. You need to make sure it is off and then run this to remove meta-data on drive. Examples from other brands should be similar as it is Intel SRT.

       Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)



      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

Thanks for the quick answer. My problem is that the ssd is only one 128gb piece and windows recovery is occupying 20gb of it alone (how stupid is that?).

What I'd like to do is reinstall windows and have the recovery on a usb (to resell the pc) then install Ubuntu and use most of the time, but I'd like to keep the intel srt for performance on Windows (and ubuntu? does it work on that too?). For the whole I'd need UEFI on, no secure boot, no quickstart.

How do I do that? How do I install windows from a full recovery usb with intel srt then resize the drive, then install ubuntu which does not want srt, then turn it back on?


> **oldfred said:**
> You also will have video issues. Look into bumblebee. But you may need nomodeset to boot if nVidia is default video.
See link in my signature for all the Ultrabook type issues.

No problems, it's intel graphics only and seems to work very well with the live usb.

---

### Post by Axx83 on 2013-08-29
From what I read having Intel SRT if there's only one SSD drive is pointless and doesn't bring any performance improvement. Then why THE HELL did acer put it on this computer?

Am I correct? Can I just turn everything to normal AHCI ?

---

### Post by oldfred on 2013-08-29
Some users with SRT have installed Ubuntu to hard drive and turned on SRT and it worked. Some preferred Ubuntu and installed Ubuntu to the SSD and stopped using SRT. I think one user posted with a larger SSD he was able to leave the smaller space that SRT was using and still install Ubuntu's / to the SSD and still turn SRT back on. Seems tricky and you may have to experiment. Does it show unallocated on SSD? Maybe that is why they moved recovery partition there, but that seems like a terrible waste to have data you should rarely if ever use on the fastest drive.

Since they do not give repairDVDs of Windows you really need to make good backups.

       Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[URL="http://ubuntuforums.org/showthread.php?t=2129157"]http://ubuntuforums.org/showthread.php?t=2129157

[/URL]
 Dell 14z & 17r with Intel SRT
[URL="http://ubuntuforums.org/showthread.php?t=2038121"]http://ubuntuforums.org/showthread.php?t=2038121
[/URL]
 Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

[URL="http://ubuntuforums.org/showthread.php?t=2038121"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2129157"]
[/URL]

---

### Post by Axx83 on 2013-08-29
I will try to repair windows boot, then make a usb drive recovery, then eliminate all partitions and install windows without srt or raid since there is only one ssd and then ubuntu after that, Uefi should not be a problem and secure boot is always disabled.

Let's see if that works.

---

### Post by oldfred on 2013-08-29
Unless you have your own legal copy of Windows you will not be able to reinstall. The vendor recovery is just an image of the system as purchased and reinstalls exactly the same as when you bought system. Serial number in in UEFI for the vendor version.
But you should just turn off SRT in Windows and remove RAID meta-data from drive without much difficulty.

---

