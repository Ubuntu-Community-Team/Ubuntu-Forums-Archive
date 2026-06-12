---
title: "Installed Windows before Ubuntu, both in BIOS mode, but GRUB install failed"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by ajthemacboy on 2015-05-25
Let me start by saying I've been trying to get it to work for 2 days,  and that I've read a lot. The answer could be extremely obvious but I  need someone to point it out.
  
I was trying to dual boot Windows and Ubuntu (yes, I followed a  guide, but I don't remember which one) when the Grub install failed. So I  aborted and kept tinkering with my disk configuration with no luck. 

  
I tried Boot Repair from a CD in UEFI mode and that didn't work. Note that I can boot Windows fine in both EFI and UEFI mode.

  
Here are the steps I took:

  
[LIST=1]
[*]Booted the Ubuntu GNOME installer in BIOS mode (fast boot disabled and CSM enabled.) 
[*]Formatted the entire disk in GParted. 
[*]Here is the configuration: [http://imgur.com/1dYoTdh](http://imgur.com/1dYoTdh) 
[/LIST]
  
The first 100 MB partition I flagged 'boot' and 'esp'. The 10 MB one  is bios_grub. The 90 MB space is just in case I need it in the future.

  
The 8GB volume is SWAP. The first 250GB volume is where Linux is  installed. It is EXT4. The second is also EXT4, but nothing is installed  there. The rest are the various Windows partitions.

  
[LIST=1]
[*]Partitioned my disk in various partitions for Ubuntu and Windows. 
[*]Booted Windows disk in BIOS mode and installed. 
[*]Booted Ubuntu installer and installed. 
[*]Grub install failed. 
[/LIST]
  Here is my latest attempt at boot-repair: [http://paste.ubuntu.com/11314742/](http://paste.ubuntu.com/11314742/)
  
In this attempt I tried to do a manual install to SDA1, with the overall bootloader install to SDA, if I remember correctly.

  
Where should I go from here? Should I erase all Ubuntu partitions and try again?

  Thanks!

---

### Post by grahammechanical on 2015-05-25
Compare these two statements

> I can boot windows fine in both EFI and UEFI

> fastboot disabled CSM enabled

If another OS is installed in EFI mode then Ubuntu has to be installed in EFI mode as well otherwise we get this situation. If I was in this situation I would install again both Ubuntu and Windows. I would put Windows 8 at the start of the disk and install in EFI mode and then I would install Ubuntu in EFI mode as well in accordance with this guide

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in UEFI mode, then you must install Ubuntu in  UEFI mode too.


Regards.

---

### Post by ajthemacboy on 2015-05-25
I installed both in BIOS mode, but since I was unable to boot Linux at that point, I switched back to UEFI mode. 

Then, Windows booted fine, so I booted Lubuntu live from a DVD to use boot repair (since flash drives don't work for me in UEFI mode.)

However, boot repair didn't fix the problem, so now I guess I need to renistall Ubuntu from a DVD in UEFI mode. I'd prefer not to have to reinstall Windows again.. it's such a pain compared to Linux to get things set up.

---

### Post by Bucky Ball on 2015-05-25
> **ajthemacboy said:**
> I installed both in BIOS mode, but since I was unable to boot Linux at that point, I switched back to UEFI mode. 

Then, Windows booted fine ...

Then Windows was installed in EFI.

Switch off fast boot in the BIOS and install Ubuntu again in UEFI. Don't worry about installing Win. At the partitioning section, choose 'Something Else' and install the Ubuntu / to the existing / that the other install created. You can use the /swap partition that should be there already also. The install should write an entry for Ubuntu in the existing EFI partition. You don't need to do anything there. Just install the OS.

Good luck.

---

### Post by oldfred on 2015-05-25
You can only have one ESP - efi system partition per hard drive. You show sda1 as the efi partition, but Windows has its efi boot files in sda7??

Best to be consistent in booting. Always in UEFI or always in CSM/BIOS/Legacy mode.
Your UEFI should show two boot options for USB flash drives. One clearly UEFI and the other just name/label of flash drive. With some systems to use flash drive, you have to turn on boot settings to allow USB boot. And some (Acer, others?) also then require passwords to change that setting or open up the added settings you need.

---

### Post by oldfred on 2015-05-27
More good advice here:
[http://askubuntu.com/questions/627666/installed-windows-before-ubuntu-both-in-bios-mode-but-grub-install-failed](http://askubuntu.com/questions/627666/installed-windows-before-ubuntu-both-in-bios-mode-but-grub-install-failed)

---

