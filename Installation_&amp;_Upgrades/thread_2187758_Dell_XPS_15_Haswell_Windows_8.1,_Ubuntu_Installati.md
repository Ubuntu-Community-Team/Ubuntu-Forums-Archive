---
title: "Dell XPS 15 Haswell Windows 8.1, Ubuntu Installation Hangs"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by tom.j.tang on 2013-11-13
Just got my Dell XPS15 (Haswell) with Windows 8.1.  Been a Mac user for a few years now but the price point of the new Dell convinced me to switch back and try dual boot with Ubuntu. After I shrink the partition and reboot with Ubuntu 13.10 on USB - the installation procedure fails on selecting a partition/hard drive.  Booting with legacy mode.   

Anybody have insight on what to do?

Thanks,
Tom

---

### Post by oldfred on 2013-11-13
What video and is this an Ultrabook?

Some other Dell threads. Models seem similar but options make a difference.
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

These were not Dell but were Haswell, so some settings may apply.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by tom.j.tang on 2013-11-13
I've done a search on the forums and none of the issues describe what I encounter (afaik).

XPS 15 w/Haswell
4th Generation Intel(R) Core(TM) i7-4702HQ processor (6M Cache, up to 3.20 GHz)
NVIDIA GeForce GT 750M 2GB GDDR5
1TB 5400 rpm SATA Hard Drive + 32GB mSATA Solid State Drive
Intel Dual Band Wireless-AC 7260 + Bluetooth 4.0

Like my previous post, I can start the installation process and even connect to wireless.  But once I get to selecting a partition and click on "change"  the system freezes.
Tried it without connecting to wireless, same result.

Not quite sure what to try next.

---

### Post by oldfred on 2013-11-13
With the separate 32GB SSD that will be an Ultrabook which adds complications over the standard UEFI install. You usuallly have to remove the RAID meta-data from both drives to get grub to install correctly. Also you have dual video so if in nVidia mode you need nomodeset or if in Intel mode you need Intel boot paramaters to boot.

Be sure Secure boot is off. Fast boot must be off, Intel SRT must be off and meta-data removed from drive.

After turning Intel SRT off, from terminal on live installer.
       sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Review other Ultrabook installs. Some that are primarily Windows users turn Intel SRT back on. Others install Ubuntu's / (root) to SSD to make Ubuntu fast, and a few have found with larger SSDs like yours they can do both as Intel SRT does not seem to use the entire 32GB.

      
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

### Post by eric_r2 on 2013-12-13
Tom, did those directions ultimately work for you? Have you gotten all of your drivers installed? I have the same laptop as you, and am looking to make the leap to Ubuntu.

---

### Post by oldfred on 2013-12-13
Another link. This by Dell Tech Center.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

---

