---
title: "How to use syslinux to boot a full install of ubuntu/linux mint"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by benbrockn on 2014-08-03
Hi,

So I have a problem booting Ubuntu and Linux Mint from one specific laptop I have (HP Pavilion dv6z laptop). What happens is a plain black screen with blinking cursor. If you want to read more about that click here: [http://ubuntuforums.org/showthread.php?t=2237349&p=13088125#post13088125](http://ubuntuforums.org/showthread.php?t=2237349&p=13088125#post13088125)


But anyway, I know that my HP laptop works fine with Live USBs that use syslinux. Since my linux OS won't boot, what I want to try is to make a small fat32 partition on my USB stick right in front of my ROOT partition and set the flag to boot. This small partition will house the basic syslinux structure and when the laptop reads from the stick, it will boot syslinux which boot my Linux OS. As for the original grub loader found in the root partition, I was  thinking to just leave that alone and let syslinux bypass it to load the  Linux OS.

So.... How do I do this? How can I install syslinux on a newly made fat32 partition and let it chainload the fully installed OS?


My current partitions are like so:

> 16GB USB flash drive

Root 7500 MiB (7.86 GB)  [1.22 GB unused]
Home 7766 MiB (8.14 GB) [5.41 GB unused]

Thanks!

---

### Post by oldfred on 2014-08-03
I do not think your issue is solved by the choice of boot loader. It is the configuration of the system and or boot options that you can add.

The live installer is configured for the lowest common denominator to boot just about anything. But once installed "better" configuration is installed but then you may need boot options or additional drivers.

It also can be related to BIOS settings.

I do not know AMD as I have nVidia, but I always have to use nomodeset boot option until I install proprietary drivers. 

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)



I did the opposite with my Windows 7 repair flash drive. Syslinux is a Windows type boot loader that uses boot flag and has boot code in Partition boot sector. With my Windows repair flash drive I just installed grub to it and chainloaded a standard Windows boot stanza to the partition boot sector. The only issue I had to be careful of was Windows already had a /Boot partition can grub wants to create a /boot partition. In Linux those would be different, but in Windows you cannot have both as it is not case sensitive. So grub & BCD coexist in same boot folder.

---

### Post by sudodus on 2014-08-03
Some HP computers have problems booting from USB with grub, except the grub version that came with Ubuntu 13.04, 'Raring'. I made a chainloader for that purpose, see these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by benbrockn on 2014-08-03
> **oldfred said:**
> I do not think your issue is solved by the choice of boot loader. It is the configuration of the system and or boot options that you can add.

The live installer is configured for the lowest common denominator to boot just about anything. But once installed "better" configuration is installed but then you may need boot options or additional drivers.

It also can be related to BIOS settings.

I do not know AMD as I have nVidia, but I always have to use nomodeset boot option until I install proprietary drivers. 

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)



I did the opposite with my Windows 7 repair flash drive. Syslinux is a Windows type boot loader that uses boot flag and has boot code in Partition boot sector. With my Windows repair flash drive I just installed grub to it and chainloaded a standard Windows boot stanza to the partition boot sector. The only issue I had to be careful of was Windows already had a /Boot partition can grub wants to create a /boot partition. In Linux those would be different, but in Windows you cannot have both as it is not case sensitive. So grub & BCD coexist in same boot folder.


Hey thanks for the reply, unfortunately grub doesn't even load. The only way I get it to work is through virtualbox (i'm sure my really old xp laptop will work too, but I can't test it atm). But using virtualbox I can get into the grub file and change parameters. I already tried nomodeset, I'm unsure of other parameters I can use though. I don't have time tonight, but I'll look into those links, thanks.

---

### Post by benbrockn on 2014-08-03
> **sudodus said:**
> Some HP computers have problems booting from USB with grub, except the grub version that came with Ubuntu 13.04, 'Raring'. I made a chainloader for that purpose, see these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")


Thanks for the links as well, I'll be able to check them later.

---

