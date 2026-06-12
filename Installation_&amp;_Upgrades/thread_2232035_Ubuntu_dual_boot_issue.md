---
title: "Ubuntu dual boot issue"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by arun17 on 2014-06-29
I tried to install ubuntu along with windows for dual boot and I couldn't run ubuntu after installation. I ran boot repair and I got this error message : [http://paste.ubuntu.com/7720149/](http://paste.ubuntu.com/7720149/) 

Can someone help me fix this issue?

---

### Post by DaniPhii on 2014-06-29
Does GRUB appears when you turn on your PC? I don't know if you ran boot repair from another location.

---

### Post by Bucky Ball on 2014-06-29
Things look ok from your bootinfoscript. sda3 is the important bit. You have installed in EFI mode and you have a grub entry in sda3, the EFI boot partition and also a grub in sda8. That, I think, is how it should be.

I'm no expert on this, but I think something needs to be tweaked with the shim. Hopefully someone more knowledgeable can chime in ... :-k

---

### Post by oldfred on 2014-06-29
It looks like grub reinstalled ok error code 0 is no errors. Boot-Repair can pick up some miscellaneous errors that are not critical.

 grub-install /dev/sda: exit code of grub-install /dev/sda:0

  >  BootOrder: 0000,0003,2001
Boot0002* EFI DVD/CDROM
Boot0003* Windows Boot Manager
Boot2001* EFI USB Device
Boot0000* ubuntu.



Can you boot ubuntu entry in UEFI menu or one time boot key if UEFI is on or even UEFI with secure boot? It does look like you have the signed kernels that should work with secure boot on, but often better with it off. And grub has a bug and you cannot currently boot Windows from grub menu if secure boot is on.

Some systems have been modified to only boot the UEFI entry that says Windows. That is not per UEFI standard.

---

### Post by arun17 on 2014-06-29
I tried one time boot key without secure boot and I was not able to access the boot menu. But what i did try was to boot in legacy mode, which would then complain "No Operating System Found". And again, when I switch back to UEFI boot mode and then restart and keep pressing F10 to get to the boot menu. I couldn't explain that and when I try restarting, it doesn't work, unless I follow the procedure as mentioned above.

---

### Post by Bucky Ball on 2014-06-29
Try hitting the shift key just after boot.

---

### Post by DaniPhii on 2014-06-29
> **arun17 said:**
> No the grub doesn't appear when I turn on my PC
It seems as though you haven't installed GRUB in MBR of your HDD. You have to install GRUB in /dev/sda but not in /dev/sda8 or any partition. That way GRUB should find Windows 8 boot config in /dev/sda2, 3 and/or 5. And that same way GRUB should appear when you turn on your PC.

Before doing everything, you should see this: [http://ubuntuforums.org/showthread.php?t=2231963](http://ubuntuforums.org/showthread.php?t=2231963)

---

### Post by oldfred on 2014-06-29
@DaniPhii
This is an UEFI system, so grub or any boot loader is not normally installed to the protective MBR of a gpt partitioned drive. UEFI systems boot from the efi partition which is sda3.

Just notices sda1 says Sony, so it has issues and will only boot Windows. 
I suggest A: copying shim to /efi/boot and renaming it to bootx64.efi 
or E: use rEFInd.

       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming shimx64.efi or grubx64.efi to be  /EFI/Boot/bootx64.efi (back up originalbootx64.efi)
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by DaniPhii on 2014-06-29
> **oldfred said:**
> @DaniPhii
This is an UEFI system, so grub or any boot loader is not normally installed to the protective MBR of a gpt partitioned drive. UEFI systems boot from the efi partition which is sda3.Oops, I thought it would work the way I suggested, as I guessed GRUB would automatically update its configuration once it's installed to boot Windows 8 properly, but I see I guessed wrong.

Sorry for this. :oops: 

But then I have some doubts. Does this mean that we can't repartition the HDD the way we want? Is that how new PCs work? Can't we modify BIOS configuration to use our PCs as always? Wow, things are truly changing then with Windows 8. :eek:

---

### Post by oldfred on 2014-06-29
To add to the confusion, there are now two totally different systems UEFI and BIOS. 

The Ubuntu installer will boot with either UEFI or BIOS, and how you boot installer is how it installs.
From a new UEFI system you should see two boot choices for flash drive or DVD installer. One will say UEFI and the other may just show name/label of flash drive and is then BIOS boot.

UEFI and BIOS are not compatible to the extent once you start booting in one mode you cannot change to the other mode. Or grub can only boot systems installed in same boot mode.
You can have both UEFI and BIOS on one or mulitple drives but have to keep track of which way you are booting.

And UEFI needs gpt partitioning, BIOS needs MBR(msdos) partitioning. But Ubuntu will boot from a gpt partitioned drive with either UEFI or bios if correct supporting partitions are on drive. You need an efi partition for UEFI and a bios_grub partition for BIOS booting from gpt partitioned drives.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

