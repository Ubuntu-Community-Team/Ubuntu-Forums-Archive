---
title: "Boot problems on Dell XPS 13 after replacement of motherboard"
date: 2016-06-18
forum: Installation &amp; Upgrades
---

### Post by wrp2 on 2016-06-18
I recently had a spill that damaged my Dell XPS 13 Developer Edition, which was preinstalled with Ubuntu 16.04. My motherboard has been replaced. I removed the SSD before repair; now I can't boot from it anymore - I don't even get to grub; I just get a "No bootable device found." error and can go no further.

When I try booting from the UEFI partition from BIOS options, I get an error from initramfs: "Unable to find a medium containing a live file system".

I tried setting up a USB with Boot Repair. I can boot up with this, and from there I can see that the correct partitions are still there and the Ubuntu partition still looks good on /dev/sda4. /dev/sda1 is the EFI system partition. I can mount /dev/sda4 just fine.

But how do I get the system to boot correctly again?

Thanks in advance.

---

### Post by oldfred on 2016-06-20
UEFI loses its settings in NVRAM when a drive is disconnected.
Some will find the settings in the ESP - efi system partition on cold boot, not warm reboot.

You can manually add settings with efibootmgr, or use Boot-Repair to uninstall/reinstall grub which will add a new entry also.

       sudo efibootmgr -v  

 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and YN is the partition number.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected) 

I also like to create the fallback or default hard drive boot entry on the internal drive. The /EFI/Boot/bootx64.efi is also the default boot entry for all external drives, but you can create on internal drives also. Boot-Repair will copy shim and rename it to bootx64.efi if you select the 'Use the standard EFI file' in advanced options. But do not think it adds the entry in UEFI.
      
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  


 Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
-c | --create
-g | --gpt
-d | --disk DISK -  The disk containing the loader (defaults to /dev/sda) 
sdX where drive sda, sdb etc
-p | --part PART -    Partition number containing the bootloader (defaults to 1)  or sda1
-w | --write-signature
-L | --label LABEL -     Boot manager display label (defaults to "Linux") 
-l | --loader NAME -     Specify a loader (defaults to \\elilo.efi)

---

