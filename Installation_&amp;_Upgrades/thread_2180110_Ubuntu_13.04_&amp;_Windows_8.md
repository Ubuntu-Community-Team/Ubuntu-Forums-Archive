---
title: "Ubuntu 13.04 &amp; Windows 8"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by ninjashby on 2013-10-11
Hi all, 

I am having the same trouble as a lot of others trying to get ubuntu 13.04, windows 8 and UEFI to play nicely. 
I am on a dell inspiron 14z which has windows 8 pre-installed. It has two disk drives, one 500GB and one 32GB SSD. Windows 8 is installed on the 500GB drive. I disabled secure boot, windows fast boot and tried to boot from an ubuntu live USB. 

This failed, with a black screen after the 'Try ubuntu before installing' option, so i enabled legacy bios support. Then I could successfully boot from USB. 

I proceeded to install ubuntu onto a partition on the 32GB SSD, with the home drive on a new partition on the 500GB drive. 

This worked, but it wasn't great. I could boot into ubuntu as long as I had the legacy BIOS support enabled. This prevented me from booting into windows. If I reenabled UEFI, I could boot into windows but I didn't get grub and couldn't boot into ubuntu. 

I followed the instructions at [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode) to use boot-repair to convert my ubuntu install to work with UEFI, this didn't work, now I just get 'internal hard disk drive not found' 

Here are the results of boot-repair : [http://paste.ubuntu.com/6223285/](http://paste.ubuntu.com/6223285/)

I am at a loss for what to try next. Googling the problem just comes up with the same things I have tried.

---

### Post by oldfred on 2013-10-11
It looks like Boot-Repair converted you to UEFI boot.

 LIne 1186 and 0006 is ubuntu
BootOrder: 0006,0000,0001,0002,0003,0007,0005,0004,000A


   Boot0006* ubuntu	HD(1,800,fa000,b416810b-294d-4d48-b53e-f948f36c0d6a)File(EFIubuntugrubx64.efi)

You did have grub installed to MBR which is the BIOS boot mode and as you found you could only dual boot from UEFI by turning on/off CSM/BIOS/Legacy boot mode.

Some have installed / (root) to sdb like you did with Intel SRT still enabled. Those with larger SSD like yours seem to have space to do that. But I do not see the partition for SRT so that may be interfering with Windows. You usually have to turn off the SRT, remove meta-data from drives and then install as grub sees Intel SRT as RAID (somehow) and does not correctly install.

Some other Dells. Most versions seem similar, just whether they have SSD with Intel or not.

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

Those with very new Haswell systems seem to find the beta 13.10 works better. But it still is beta until later this month.

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
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

