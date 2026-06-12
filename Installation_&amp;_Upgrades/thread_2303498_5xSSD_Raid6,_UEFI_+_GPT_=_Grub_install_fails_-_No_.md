---
title: "5xSSD Raid6, UEFI + GPT = Grub install fails - No boot device"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by Stefan_Grnberg on 2015-11-19
Hi.
The past 2 days i have been trying to install Mint, Debian and Ubuntu on my computer as solo os.
However, in all installations, grub always fails installing.
I have created GPT Partition table, and ef02 partition typed partition with 1MB, 2048 sectors, 512 MB(Used several guides) and none works (all tagged with flag bootable and bios_grub also tried)
The reason i need GPT is that i have a 3TB ntfs drive.

Bios is set to EFI boot only, secure boot is off.

What else can i try to get grub install and the uefi booting?

---

### Post by oldfred on 2015-11-19
I do not know RAID.
But issue may be boot flag and/or how you boot installer.

How you boot installer is then how it installs either UEFI or BIOS.
But with gpt a boot flag partition must be the ESP - efi system partition for UEFI boot. No other partition should have boot flag.
And if BIOS booting you boot installer in BIOS Mode, but grub must see the bios_grub partition. That must be unformatted 1 or 2MB with the bios_grub flag.

With gdisk the ESP is set with the ef00 code and bios_grub with ef02 as you have been doing. Only parted/gparted used the boot flag to set the ESP. The actual codes used are the very long GUID system codes. 

Boot flag on gpt is totally different than boot flag in BIOS/MBR. 
And in BIOS, boot flag is not used by grub. 
Boot flag is required by Windows in MBR to know which NTFS partition is bootable. Some other Linux boot loaders like Lilo & syslinux also use boot flag.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Stefan_Grnberg on 2015-11-20
Hi.. im not sure how.. but when today when i changed my bios into RAId instead of achi(?) for my disks.. i suddenly booted ubuntu that i have seemed to installed yesterday.
So now im up and running.

afaik i run a gpt/efi setup atm. im not sure how i managed this (has a few drops of white yesterday), but now i can boot into ubuntu.. so i'll count it as a success.
Because my mainboard cant do raid6. im "stuck" with raid 5. its probably "good enough".
So now im just left to learn to live without windows.
So today.. i installed additional softare (as in nvidia stuff).
got netflix to play in chrome.
restored windows firefox profile.

---

### Post by rocco6 on 2015-11-21
Try Boot Repair.

---

