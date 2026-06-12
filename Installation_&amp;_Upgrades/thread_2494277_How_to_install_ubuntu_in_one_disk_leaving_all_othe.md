---
title: "How to install ubuntu in one disk leaving all other disks untouched"
date: 2024-01-10
forum: Installation &amp; Upgrades
---

### Post by javoerro on 2024-01-10
I have a 2 disk in my pc. one with windows installation, other in blank.


I want to install ubuntu in the blank disk but leaving the windows disk UNTOUCHED, that means without modifiying bootloader by grub. why? because the most of the time, the disk with ubuntu will be disconected phisically from the pc.


i always choose the option "erase disk..." and select de blank one. but regardless that, the installation puts grub in the windows disk.


how to avoid this? thank you!!!

---

### Post by tea for one on 2024-01-11
Via UEFI settings, isolate or de-activate your Windows disk.
Or physically remove it.
Only have the target disk visible to the Ubuntu installer.

---

### Post by yancek on 2024-01-11
> the installation puts grub in the windows disk.
 

That is the way the Ubuntu installer was designed.  This has changed in the more recent releases of Ubuntu on UEFI systems but you don't indicate which release you are using?  The safest (and only really safe way) is the suggestion in post 2.

---

### Post by TheFu on 2024-01-13
> **tea for one said:**
>  Or physically remove it.


^^^^^^^^^^^^^^^ this.  Nothing else will be 100% certain.  Just disconnect either of the SATA cables (data or power).

BTW, doing this will cause some hassles with dual booting and patching, since UEFI expects to see only 1 UEFI partition inside any system.  It would be much less hassle to allow the single UEFI to be shared by 1, 2, 15, 50, different OSes, but just keep the actual OSes in different partitions (either on the same or different physical disks).  Keeping disks separate is of minimal real use.  OSes work at the partition level, not disk level.

---

### Post by oldfred on 2024-01-13
Supposedly the new subiquity installer has a fix, but older Ubiquity installer still has bug.
Only newer versions of Ubuntu use subiquity installer. I just installed Kubuntu 24.04 as test, and it sill used Ubiquity. So version & flavor make a difference.

I only use Something Else install option, make sure external drive is gpt partitioned with ESP, FAT32 with boot,esp flags, so grub has correct place to install.  I then open terminal during install at screen for user & password and use mount command to check mounts. If wrong ESP mounted I umount & mount correct one.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Best work around is disconnect drive, but some others usually work. 

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Note that if you disconnect drive, many UEFI disable the "ubuntu" entry. UEFI typically finds Windows entry if Windows drive disabled, but you can add new UEFI entry with efibootmgr if required. An external drive is then normally booted just live live installer from UEFI boot menu & UEFI entry for the description/name of external drive. That uses /EFI/Boot/bootx64.efi, not the typically internal drive entry of /EFI/ubuntu/shimx64.efi. But external drive must also have /EFI/ubuntu folder as grub's version of bootx64.efi seems to be hard coded to look for /EFI/ubuntu/grub.cfg file to boot.

---

### Post by MAFoElffen on 2024-01-14
> **oldfred said:**
> 
Note that if you disconnect drive, many UEFI disable the "ubuntu" entry. UEFI typically finds Windows entry if Windows drive disabled, but you can add new UEFI entry with efibootmgr if required. An external drive is then normally booted just live live installer from UEFI boot menu & UEFI entry for the description/name of external drive. That uses /EFI/Boot/bootx64.efi, not the typically internal drive entry of /EFI/ubuntu/shimx64.efi. But external drive must also have /EFI/ubuntu folder as grub's version of bootx64.efi seems to be hard coded to look for /EFI/ubuntu/grub.cfg file to boot.
+1 ---
This happens on my new MSI MB. I've had some challenges, because I not only have Multi-boot with OS'es, but do Ubuntu Dev testing, so multiple versions of, or multiple configs of the same OS...

What I used to do is to install each drive as separate, then choose from the UEFI menu to boot that drive. That used to be what I recommended as my preferred answer. That is, until some other factors were added to that. Here the extra challenges that my 13th Gen Z790 board adds to that...

1. If you remove a drive, then it sets the boot drive to the first ESP it finds, and it defaults to a Windows efi file as it's first choice. My board locks this as the fist choice, and I have to go into advances BIOS settings to where that option is buried to change that. Trying to change that boot order via efibootmgr doesn't work on this board. It either just goes to Windows, or it reports that the efi file is "corrupted", because the file it hits is not the one expected.

2. If there are booth SATA & NVME drives present, it looks for ESP's on SATA first, and if found, will not show any on NVMe drives in the boot menu.

3. On some newer custom installs, I've had to create some efi boot files for utilities or alternate boot options or methods manually with efibootmgr.

So yes, technology is advancing, and some other things have been changed and/or added. More things to now consider.

---

