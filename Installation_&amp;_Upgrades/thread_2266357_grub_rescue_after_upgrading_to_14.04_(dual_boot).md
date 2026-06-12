---
title: "grub rescue after upgrading to 14.04 (dual boot)"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by Jeremy_Poulain on 2015-02-22
I had a dual boot on my labtop (windows 8 and ubuntu 12.04).

I've upgraded my ubuntu to 14.04 two days ago.

I now have a grub rescue with file not found error. I can't boot on windows not ubuntu.

You'll find pastebin [http://paste.ubuntu.com/10339310/](http://paste.ubuntu.com/10339310/)

I tried to boot on a USB with ubuntu to try to use boot-repair. It says that it is repaired but it does not.

Any help would be appreciated.

---

### Post by oldfred on 2015-02-22
You show this file:
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 

That file was created by old versions of Boot-Repair for systems that only boot Windows as vendor has modified UEFI to only boot the Windows entry by description. That is not per UEFI standard.
And that file is actually a copy of grubx64.efi or shimx64.efi. But if you upgraded you new copies of grub/shim and the old copy does not work with the newer version of grub you now have installed.
And the rename of the original Windows file meant you could only boot Windows from the grub menu. 

Boot-Repair does not do the rename anymore. That also was done as grub2's os-prober could not create a valid Windows boot entry. But that now has been fixed.

What brand/model computer? 
Many copy the newer grub or shim files into /EFI/Boot folder and rename bootx64.efi and rename grub or shim to be bootx64.efi. Then a hard drive boot entry in UEFI will boot grub menu. 
And you can keep correct Windows efi file, so you can directly boot Windows from UEFI menu. Windows updates may also overwrite the Windows file (that is really grub file) and cause you to lose your grub boot. Best to keep them separate.

First backup entire efi partition. It is not large.

First we can fix Windows by un-renaming the bkpbootmgfw.efi back to bootmgfw.efi. You have to delete or further rename the current bootmgfw.efi.
Then you should be able to directly boot Windows from UEFI menu.
If not, copy this file from c: folder into efi folder:
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

    
Then we can copy grub's newer files into /EFi/Boot and rename to bootx64.efi. After major grub updates you may have to do this again,
      
 sudo mount /dev/sda1 /mnt
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

Then see if hard drive boot entry in UEFI boots to grub menu.

---

