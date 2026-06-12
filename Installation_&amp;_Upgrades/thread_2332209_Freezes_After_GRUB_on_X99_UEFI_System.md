---
title: "Freezes After GRUB on X99 UEFI System"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by qkslvr221 on 2016-07-29
Hi all, I'm trying to get any build of Ubuntu working on this system but am having a pretty hard time. I've tried 15.04, 16.04 and 16.10 liveUSB, but seem to get stuck after GRUB every time. 

I've added nomodeset, nouveau.modeset=0/1, pci=nomsi, xforcevesa, enabling CSM and verbose mode, but get the same black screen with colored dots at the top. nomodeset seems to make it completely black instead of static corruption, but I still don't get further. The system does respond to ctrl+alt+del at times, but I can't get any sort of console or error readout.

System specs:
X99 ASRock
i7 5820k
Nvidia/MSI GTX 980
32GB DDR4
Full UEFI

I've switched across multiple monitors and ports between 1280x1024 and 3840x2160 res, and they seem to change the corruption a bit. I even used this USB media to complete an install on my HTPC, and transferred the SSD over to this machine only to get exact same results. Any help would really be appreciated! I can't be the only one who's stuck on this. :-?

---

### Post by oldfred on 2016-07-29
While nomodeset should work with nVidia, some have just used Intel to install and then installed nVidia driver before reconnecting to nVidia card. 
But some versions with Skylake even needed boot parameters for the Intel video.

Asrock as asmedia ports. If you use one of those system will have issue. 
One user reported even connecting the DVD player to asmedia port caused issues.

These are older Asrock systems, but issues seem to be consistent with all Asrock motherboards. So I would expect yours to be the same.
  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
[http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual](http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by qkslvr221 on 2016-07-29
> **oldfred said:**
> While nomodeset should work with nVidia, some have just used Intel to install and then installed nVidia driver before reconnecting to nVidia card. 
But some versions with Skylake even needed boot parameters for the Intel video.

Asrock as asmedia ports. If you use one of those system will have issue. 
One user reported even connecting the DVD player to asmedia port caused issues.


These X99 Haswell-E chips don't have an Intel IGP like Skylake, unfortunately. By asmedia are you referring to USB or SATA ports? I have all the SSDs hooked up to the Intel SATA ports, and even tried disabling the SSATA controller in BIOS. No DVD or optical drives on here. I even unplugged all other drives besides the SSD with the HTPC installed Ubuntu, but no change.

I'll try the Fixed OC setting and report back later. Thank you for the suggestions.

---

### Post by oldfred on 2016-07-29
I do not know Asmedia ports, but gather that some vendors create more SATA ports on motherboard then the default number that Intel supports. Then those ports use a chip that is not well supported in Linux.

There may be other differences with X99, but have only seen a very few posts with that configuration.
I have two UEFI systems, one Asus Z97 Haswell and one Gigabyte Z170 Skylake and both have worked well. 
But I did make many changes in UEFI settings, no overclock, UEFI boot, fast boot off (at least initially), no network boot, enable USB ports and maybe others. And every update to UEFI from vendor has reset to defaults and I have to do them all over again.

---

### Post by qkslvr221 on 2016-07-29
Well, I tried removing the OC and enabling fixed mode but nothing changed. Bummer.

I also did some research, and it looks like both the SSATA (secondary) and lower USB root hubs are made by ASMedia, so I made sure to not use either. My boot settings are identical to the ones you mentioned, so I'm really at a loss now. :(

---

### Post by oldfred on 2016-07-29
So your Intel chip has no video mode?

With nVidia normally nomodeset works, but some need the extra boot parameters in addition.

Found a couple more X99, I did not save them myself as then I did not see much that would be helpful.
[https://ubuntuforums.org/showthread.php?t=2310445](https://ubuntuforums.org/showthread.php?t=2310445)
[https://ubuntuforums.org/showthread.php?t=2310445](https://ubuntuforums.org/showthread.php?t=2310445)

And issues tend to be by vendor then by model where  chips are similar.

---

