---
title: "New motherboard - multiboot Ubuntu/Windows - advice needed..."
date: 2019-09-03
forum: Installation &amp; Upgrades
---

### Post by LinuxAlexs on 2019-09-03
Hello

I'm changing my 7 year old motherboard (which is legacy bootup) to a UEFI motherboard (Gigabyte Designare Z390), and I'm looking for advice before I change it.

I am using two SSD drives, which has multiple partitions for various OS's. I am running Grub and this gives me options to boot to the Ubuntu and 3 different Windows 10 installations.

So I'm looking for advice on how to prepare the PC before I change the motherboard and do the final shutdown.
BTW please note I will be using the same display adaptor card, so video drivers should hopefully not be an issue?

What I have done:

I have an full Acronis DiskImage backup of all the SSD's.
Made an Ubuntu USB boot disk.
Have Windows 10 (latest version) setup DVD's on standby.
I'm going to "SysPrep" each version of Windows before I change the motherboard.

So what do I need to do with Grub and Ubuntu on my old motherboard before I replace it and then shutdown for the final time (before the upgrade)?

I notice with this new motherboard BIOS I can disable CSM and set boot to legacy, maybe I should do that and then worry about changing to UEFI another time?
If I do this I wouldn't need to touch GRUB and everything should work fine?
Is there a way perhaps to SYSPREP'ing Linux?

Please let me know if you have any migration tips.

Thanks

Alex

---

### Post by oldfred on 2019-09-03
I recommend UEFI, but if old system is BIOS/CSM/Legacy, you still can boot those drives in BIOS mode. It is a lot to convert as drives should be gpt, not 35 year old MBR as well.
 If you backup /home, installed apps and have a standard desktop, you can do a new install in UEFI mode and restore backups relatively easily. Also does a major houseclean.

I would suggest a new SSD also. My Gigabyte build was several years ago Z170. Probably has similar UEFI. Back then, NVMe SSD were a lot more than SSD. But I installed M.2 SSD and was amazed by how small it was, same size as flash drive. 

Make sure you have good backups.

If BIOS, you may not have to do anything, other than in UEFI settings on new system make sure it is not using UEFI Secure Boot (which does not allow CSM boot) and maybe other settings. Secure Boot may be "Windows" or "Other". But fine print in manual may still say if Windows 7 use "Other". Windows 7 does not support Secure Boot, so really the Secure boot setting.

I converted my first drive to gpt with my old BIOS only system in 2010. Then in 2012, still with BIOS system, started including both the ESP & bios_grub partitions so I could install grub for UEFI or for BIOS boot on a gpt drive. It was another couple years before I got first UEFI system.

For more info on UEFI, see link in my signature.
       [https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/](https://www.zdnet.com/article/linux-on-your-laptop-heres-what-you-need-to-know-about-uefi-firmware/) 
    
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Dennis N on 2019-09-03
I would change out the power supply (also 7 years old?) and go with good modular power supply. I would use NVMe m.2 SSD drives only (you have 2 connectors) and not SATA, and thus eliminate all the SATA cables inside the case, plus a big boost in speed over SATA SSDs.

---

### Post by LinuxAlexs on 2019-09-03
I've already got Samsung EVO 860 SSD's, a decent Wattage Corsair PSU, NVidea Geforce 1070, Windows 10 on existing PC. The only thing that is ancient is the motherboard/CPU/memory which will be swapped out.
I also have decent backups etc. I don't want to upgrade my SSD's either right now (budget), I'm using SATA.

My actual question was - am I going to boot if I set legacy boot mode in the BIOS, full details in opening post, after I change the motherboard.
Will GRUB (pointing to Windows and Ubuntu) and Ubuntu itself be OK?
I'll try to convert UEFI another time  if I can (when I buy  NVMe m.2 SSD's perhaps),, just want to be up and running.

Many Thanks

Alex

---

### Post by LinuxAlexs on 2019-09-05
So I'll be OK you think?
Ubuntu and grub will work?

Will be doing this next week.
My hardware and backups are sorted.
Comments appreciated!

Thanks

---

### Post by LinuxAlexs on 2019-09-06
Oh well... let's see then...

---

### Post by LinuxAlexs on 2019-09-17
Well just in case anybody is interested it worked great apart from Windows. My mistake was to sysprep it. Restoring from backup (effectively untouched) resolved it.

Ubuntu behaved like a champ. One crash after running update and then everything was fine.

---

