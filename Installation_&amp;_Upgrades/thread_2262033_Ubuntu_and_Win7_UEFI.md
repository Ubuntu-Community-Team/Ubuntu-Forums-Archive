---
title: "Ubuntu and Win7 UEFI"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by Tom_Dalton on 2015-01-22
Before you tell me "go check the other posts, this is already answered..." I've read dozens of other posts with various answers, and tried many of them! I'm trying!

Here's the messy result so far:

paste.ubuntu.com/9825379

I did EasyBCD and Wubi inside Windows before I realized that was probably all horrible, and then I tried a manual "something else" installation from my Ubuntu 14 LiveCD. Now when I power on my laptop, I go straight to a "WINDOWS FAILED to start \efi\microsoft\boot\bcd status 0xc0000098" error message and I can't do anything else.

I've got my Ubuntu LiveCD -- is there any way I can fix things from here? I *really* don't want to lose my Windows system, and I'd love it if I could get Ubuntu also working!

Maybe I should add... I'm pretty sure the laptop is booting UEFI, with no Secure Boot. If I set it to "Legacy" it just goes immediately to "No OS found".

---

### Post by oldfred on 2015-01-22
With UEFI you do not need EasyBCD except perhaps as another Windows repair tool for the BCD. Do not use it as still another boot manager. You already have UEFI as a boot manager and grub as both a boot manager & boot loader for Ubuntu.

You should un-install wubi. that is not an obsolete version and wubi does not work with gpt partitioned drives which UEFI requires. You do that from inside Windows like any Windows application.

Because it is Windows 7, you do not have secure boot or the always on hibernation or fast boot. But do not turn on hibernation,.

Did you install twice, once with sda6 as a separate /boot partition, then without it? Better not ot have a separate /boot anyway.

Grub really only boots a working Windows, and Boot-Repair can only do minor fixes to Windows. You need to boot into Windows repair console or f8. But in most cases much better to have a Windows repair flash drive or CD.

Your installs are UEFI, do do not turn on Legacy/BIOS/CSM boot mode. Just always boot in UEFI.

```
BootOrder: 0002,0000,0001
Boot0000* EFI DVD/CDROM    ACPI(a0341d0,0)PCI(1f,2)03120a00040000000000CD-ROM(1,76991,1240)RC
Boot0001* Windows Boot Manager    HD(3,286a800,82000,b127c390-292c-4685-a711-039227e05e39)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0002* [COLOR=#ff0000]ubuntu[/COLOR]    HD(3,286a800,82000,b127c390-292c-4685-a711-039227e05e39)File(EFIubuntugrubx64.efi)

```

You show ubuntu entry in UEFI. But I see mention of Sony. What brand/model is this?
Sony will only boot Windows from UEFI as it (not per UEFI standard) modifies UEFI to only boot the Windows description and needs work arounds to boot Ubuntu.

       One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )

      
 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies. Yours is sda3.
sudo mount /dev/sda3 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by Tom_Dalton on 2015-01-22
Thanks for the response!

I did the steps you provided, copying the Ubuntu boot files into /EFI/Boot and replacing bootx64 with the grubx64. When I reboot, the computer still goes immediately to the Windows Boot Manager with the error message about \EFI\Microsoft\Boot\BCD.

I will be able to try a Windows 7 "repair" later -- that might help fix the Windows problems?
Then should I clean up and remove some of the other partitions that resulted from my varied attempts at creating this?

---

### Post by oldfred on 2015-01-23
Has some info on uninstalling wubi.
If editing BCD, you probably want to remove the wubi entry anyway.

The only other partition looks like sda6, but it is small and then the space is difficult to add to anything but sda5.

---

### Post by Tom_Dalton on 2015-01-27
I ended up using a Windows 7 restore disk to get my Windows working again, and just blew away the Ubuntu partitions and stuff. I'll try it again once I have a separate machine to work with. UEFI seems to have greatly complicated things!

---

