---
title: "Ubuntu not loading after installed alongside Windows 7. Boot-repair could not fix."
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by vic9 on 2014-08-19
I tried to install Ubuntu 14.04 alongside Windows 7. After installation, my PC boots directly to Windows 7. It doesn't show the menu for me to boot into Ubuntu. 
I tried to use Boot-repair as mentioned in [link]("https://help.ubuntu.com/community/UEFI"). Using the recommendation repair didn't solve my problem. 

I ran Boot-repair two times with two different settings (activating and deactivating [COLOR=#000000][FONT=arial]the [Backup and rename Windows EFI files] option). However, it's still the same. 
[/FONT][/COLOR]Boot-repair also suggested me to change into EFI mode which I have no idea how to do that. 
My Bios Boot option is similar to this picture: [http://i1236.photobucket.com/albums/ff457/Kizwan_Chronos/17062012549.jpg](http://i1236.photobucket.com/albums/ff457/Kizwan_Chronos/17062012549.jpg)

When EFI Boot was enabled, Boot-repair recognized that my PC is booted into Legacy mode. When I turned off the EFI Boot, it still said that my PC is booted into Legacy mode.

Here is the BootInfo summary link: [http://paste.ubuntu.com/8092519/](http://paste.ubuntu.com/8092519/)

Do you have any idea how to fix this problem ? Thank you very much for your help.

---

### Post by fantab on 2014-08-19
```
parted -l:

Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**

Number  Start   End    Size    File system     Name                          Flags
**1      1049kB  211MB  210MB   fat32           EFI system partition          boot**
2      211MB   345MB  134MB                   Microsoft reserved partition  msftres
3      345MB   152GB  151GB   ntfs            Basic data partition          msftdata
4      152GB   300GB  149GB   ntfs            Basic data partition          msftdata
5      300GB   671GB  370GB   ntfs            Basic data partition          msftdata
**7      671GB   671GB  1049kB                                                bios_grub**
8      671GB   715GB  44.0GB  ext4
9      715GB   723GB  8477MB  linux-swap(v1)
6      723GB   750GB  26.8GB  ntfs            Basic data partition          hidden, diag
```

Your Windows appears to be installed in UEFI mode as it has an ESP [Efi System Partition].
If Windows is installed in UEFI mode then, for all practical purpose, you must also install Ubuntu in EFI mode.
In your case, Ubuntu is not installed in UEFI mode, but in 'legacy mode'. This probably happened because you may have booted Ubuntu DVD/USB in 'legacy mode'.

I suggest you re-install Ubuntu in UEFI mode. [Check]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") whether you are booting in EFI or Legacy.
But before you do that:
1. Enable UEFI boot in Uefi/Bios menu.
2. Using gparted remove the 'bios_grub' flag from your 7th partition. This is probably confusing the installer. 'bios-grub' flag is needed on GPT disk if you want to boot Linux in 'legacy' mode from GPT.
3. Reinstall Ubuntu.

---

### Post by oldfred on 2014-08-20
Boot-Repair can convert a BIOS install to UEFI install by uninstalling grub-pc and installing grub-efi-amd64.

But if you reinstall be sure to use Something Else or you may erase entire hard drive.
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

UEFI & BIOS are not compatible. How you boot install media is how it installs. You should be able to dual boot but only from UEFI/BIOS menu. And you may have to turn on/off UEFI or BIOS/CSM/Legacy settings. Some auto switch and you can use one time boot key often f12, but varies by vendor.


 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

