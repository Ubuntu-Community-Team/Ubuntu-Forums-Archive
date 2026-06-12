---
title: "Dual boot problem"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by killstatic on 2016-09-19
I installed ubuntu on my sony laptop and it just boots straight to windows after boot repair
[http://paste2.org/s0k9HEKZ](http://paste2.org/s0k9HEKZ)
Please help

Thanks Joshua

---

### Post by oldfred on 2016-09-19
Sony is one that does not boot anything other than Windows. They violate UEFI standard.
But UEFI does have a fallback or hard drive boot entry that still should work.
Boot-Repair should have copied shimx64.efi to /EFI/Boot/bootx64.efi which is a standard drive boot file/folder.
But it does not look like you have an UEFI entry to boot the drive. Your ESP is sda3.

       sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition , yours is sda3 so it should be this:
sudo efibootmgr -c -g -d /dev/sda -p 3 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 

Then in Sony's UEFI choose to boot UEFI hard drive, not ubuntu.
see also:
man efibootmgr

 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

