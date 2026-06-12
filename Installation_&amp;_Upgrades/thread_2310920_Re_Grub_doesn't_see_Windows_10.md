---
title: "Re: Grub doesn't see Windows 10"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by Spud37 on 2016-01-23
I just repartioned and installed ubuntu 15.10 onto my thinkpad 11e, which had windows 10pro installed. I thought just installing ubuntu 15.10 would normally work and show the option to boot to windows 10 in grub like it has done when i have dual-booted before. Now I can't find a way to either fix grub to allow me to boot into windows 10. I have searched and tried a few different things that were suggested to fix it. I have tried boot repair, but to no avail. Even tried to install ubuntu again hoping that would fix grub but no luck. I think it may be possible that one of the problems is all the other partitions I actually saw in gparted. Most being recovery or other window small partitions. 


Worse case I need a way to perhaps just wipe ubuntu for now and allow me to boot to windows 10 on my laptop. I am not sure how to fix the bootloader for just windows 10, never had to before. Thanks for any help.

```
>sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D8F1A3A8-85EB-4158-9EA4-0D7DEC7A5976


Device         Start       End   Sectors  Size Type
/dev/sda1       2048    534527    532480  260M EFI System
/dev/sda2     534528    567295     32768   16M Microsoft reserved
/dev/sda3     567296 189310975 188743680   90G Microsoft basic data
/dev/sda4  248020992 250068991   2048000 1000M Windows recovery environment
/dev/sda5  189310976 245923839  56612864   27G Linux filesystem
/dev/sda6  245923840 248020991   2097152    1G Linux swap


Partition table entries are not in disk order.
```

So I fairly certain that windows 10 is sda4, and ubuntu is sda5. But trying to adjust any of the booting to sda4 fails.

EDIT: I love ubuntu and have been a long time user but now I even have ubuntu freezing on me. Not only with the booting into windows issue. I dont have this issue on my computer that has windows 7 and ubuntu or the other laptop with both win10 and ubuntu. Any help would be amazing. I think i may just try and find a way to revert back to windows and delete the linux partition for now. Perhaps until the next release.

---

### Post by oldfred on 2016-01-23
Please use code tags for longer code or text.
Easy to add with # icon in forum's advanced editor.

Also fdisk does not work with gpt partitioned drives. It will with 16.04 version.
Use gdisk or parted.

Did you install Ubuntu in 35 year old BIOS boot mode on an new UEFI system? BIOS & UEFI are not compatible and once you start to boot from UEFI menu you cannot switch. Or from grub menu can only boot systems installed in the same boot mode as Ubuntu/grub.
You should be able to choose which system to boot from UEFI boot tab or perhaps one time boot key which varies by brand but often is f10 or f12.

If drive is gpt, then Windows must be UEFI as it only boots in UEFI mode from gpt partitioned drives.

You can use Boot-Repair's advanced options to convert a BIOS Ubuntu install to UEFI. It actually is just uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI).

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If still issues post link to summary report from Boot-Repair.

---

### Post by Spud37 on 2016-01-23
Sorry about the code. Also I'm not sure. I just installed ubuntu the normal way and thought it would work. It is a new laptop with Win10 on it. Right now I am just looking at restoring the old bootloader so it will just boot windows 10, then i will delete the ubuntu partition until april. then i will try again. Partly because i need this working by monday or sooner for school. I was hoping to have ubuntu on there as well because it runs a bit faster and I really like ubuntu but right now i just need windows up and running again.

---

### Post by oldfred on 2016-01-23
If UEFI Windows, there is nothing to reinstall.
But you have to go into your UEFI/BIOS and make sure UEFI is on. Secure boot is optional.
And then choose to boot Windows. 
Or use one time boot key.

---

### Post by Spud37 on 2016-01-23
> **oldfred said:**
> If UEFI Windows, there is nothing to reinstall.
But you have to go into your UEFI/BIOS and make sure UEFI is on. Secure boot is optional.
And then choose to boot Windows. 
Or use one time boot key.
Thanks

It is UFEI Windows. It does seem to be one. I also found that if I used the inturrupt boot and choose windows boot manager it will boot to windows. Where as if I allow it to go though as normal it goes to grub which will boot ubuntu but not windows. Everytime I selected one of the windows options it says image not found or invalid.

Okay turning off Secure boot seems to have worked. I can now dual boot. Thank you to both you for your help. One last question can I edit the grub list, it doesnt seem to be like last time i messed around with grub, which has been over two years now.

---

### Post by oldfred on 2016-01-24
I do prefer to manually edit grub either /etc/default/grub or /etc/grub.d/40_custom        , but depending on what you want there are different options.
I generally do not like grub customizer as it replaces the grub scripts which later can complicate things, but it is a gui which some like.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)


 kde grub2 customizer (can install in any Ubuntu)
sudo apt-get update && sudo apt-get install kde-config-grub2

   Creator of grub customizer
[http://ubuntuforums.org/member.php?u=1247908](http://ubuntuforums.org/member.php?u=1247908)
Customizer has backups of original files
[http://ubuntuforums.org/showthread.php?t=2279347&page=3](http://ubuntuforums.org/showthread.php?t=2279347&page=3)

---

### Post by siepo on 2016-01-24
> **oldfred said:**
> I do prefer to manually edit grub either /etc/default/grub or /etc/grub.d/40_custom        , but depending on what you want there are different options.
I generally do not like grub customizer as it replaces the grub scripts which later can complicate things, but it is a gui which some like.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)


These are rather long pages, and lack an UEFI Windows example. My /etc/grub.d/40_custom looks as follows:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw81.efi
menuentry "Windows 8.1 UEFI" {
  search --no-floppy --fs-uuid --set 9EA3-3FA6
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw81.efi
}

```

The code 9EA3-3FA6 is taken from the output of blkid. To be precise, from the line which contains PARTLABEL="EFI system partition" The file (${root})/efi/Microsoft/Boot/bootmgfw81.efi is the Windows EFI bootfile.

Check as sudo exactly what efi files you have in /boot/efi/EFI/Microsoft/Boot. In most cases, the filename itself is more likely to be bootmgr.efi or bootmgfw.efi.

---

