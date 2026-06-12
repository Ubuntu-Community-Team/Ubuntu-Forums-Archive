---
title: "3rd install of Ubuntu not showing up in Grub-have to select &quot;Network&quot; in System Setup"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2014-09-19
So this is really weird. Here is what I have

Dell Inspiron 17
Windows 8
Mint 17
Mint 17 
Ubuntu 14.04

The last one is the one I'm having the odd problem with. When I boot up, the first 3 show up in Grub. The last one doesn't. I'm not sure how I even found it but the way I have to acces it is to first select "System Setup" in the Grub Menu. Then I go into Boot Manager of the laptop then select an option called Network. When I do that, I get a second Grub menu with the new Ubuntu listed and I can boot up. On the 2nd Grub Menu all 3 installs of Ubuntu / Mint show but the Windows partition doesn't.

Anyone have any idea how I fix this?

---

### Post by fantab on 2014-09-19
Download, Install and run **[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** (preferably from Live media), '*Create BootInfo Summary*', _note down the url link_ it creates to the bootinfo file and post the link here....

Don't run any repairs for now.

---

### Post by PopsTheSailor on 2014-09-20
Here is the link. When I ran boot repair I also got a message saying something like EFI detected. Please check options.

[Http://paste.ubuntu.com/8387067/](Http://paste.ubuntu.com/8387067/)

---

### Post by fantab on 2014-09-20
```
parted -l:

Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
[COLOR=#a52a2a]Partition Table: gpt
[/COLOR]
Number  Start   End     Size    File system     Name                          Flags
[COLOR=#a52a2a]1      1049kB  525MB   524MB   fat32           EFI system partition          boot[/COLOR]
2      525MB   567MB   41.9MB  fat32           Basic data partition          hidden
3      567MB   701MB   134MB                   Microsoft reserved partition  msftres
4      701MB   1215MB  514MB   ntfs            Basic data partition          hidden, diag
5      1215MB  51.2GB  50.0GB  ntfs            Basic data partition
7      51.2GB  61.7GB  10.5GB  ext4
10      61.7GB  116GB   54.5GB  ext4
8      116GB   262GB   146GB   ntfs
[COLOR=#a52a2a]9      262GB   262GB   1049kB                                                bios_grub[/COLOR]
11      446GB   488GB   41.9GB  ext4
12      488GB   492GB   4176MB  linux-swap(v1)
6      492GB   500GB   7677MB  ntfs            Microsoft recovery partition  hidden, diag
```

You have EFI boot and not 'legacy'. From a GPT Windows only boots in UEFI... Linux can boot from GPT in 'legacy/MBR' mode but we need a separate partitions with 'bios_grub' boot flag.
In a UEFI boot OS boot from an ESP [EFI system partitions] and not MBR.

You have installed Ubuntu in 'legacy' mode... When all other OS are booting in UEFI mode. Check your UEFI (new BIOS) boot settings and make sure 'UEFI boot' is enabled and NOT 'legacy/csm/mbr'.
Using Gparted from a Live Ubuntu media remove the 'bios_grub' flag from the 9th partition. Make sure that your Ubuntu dvd/usb boots in UEFI mode only... if the installation media sees UEFI enabled then the media will boot in EFI mode, if legacy is enabled then it wll boot in legacy mode. See this link to know the difference: [URL="https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode"]https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode
[/URL]I suggest you go through the above linked page to understand UEFI.

After booting Ubuntu DVD/USB in EFI mode, run Boot-Repair again... go to 'advanced' settings and set your Grub install location to your /dev/sda1 or EFI system partition... finish the repair.
reboot.

> EFI detected. Please check the options.
=================== Advice displayed in case of recommended repair
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

---

### Post by Dennis N on 2014-09-20
Comments:

1588 and 1594 partitions and disks section: Ubuntu (sda11) was not installed in UEFI mode, while the two Mints were. When you boot, the default boot loader is grub-efi from mint 17. It does not show Ubuntu because you installed that in BIOS mode - impossible to boot.

The second grub you mention is Ubuntus in (Legacy) BIOS mode. Why are the two Mints detected here and Windows is not? Maybe because the computer is now in BIOS mode and Windows can't be started; but Mint was installed in UEFI mode too, so why do you get Mint entries? - perhaps non-uefi kernels are present and detected on those as well as UEFI? Just guessing here. I would like to know why Mint shows up myself.

I won't recommend a fix - not sure what would work. 

Also:

Note that the two Mints are sharing the boot folder (ubuntu) and files on sda1 (Mint 16,17 installs its boot folder as ubuntu). What happens when you update?

---

### Post by Dennis N on 2014-09-20
@PopsTheSailor;

Let us know how the suggested repair goes. Do all the OSes on you system boot ok? Thanks.

---

### Post by oldfred on 2014-09-20
Good discussion of issues above.

You also have this which is done by Boot-Repair to "fix" buggy UEFI:
       /EFI/Microsoft/Boot/bkpbootmgfw.efi 

While it has worked for many systems, it is not the most reliable of fixes, other alternatives now also work for most systems. You can only boot Windows from grub menu (of a UEFI install) and cannot directly boot Windows from UEFI menu or perhaps one time boot key. And if Windows does an update it will overwrite the bootmgfw.efi file (which is now really grub) with a new Windows copy and you are back to booting only Windows.

      
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

Fully backup your current efi partition so you do have copies of all those files if currently working. But You shoudl be able to copy and rename folders to make unique boot entries in UEFI. Or just have one Ubuntu entry and boot other systems from grub menu.

Some of the other UEFI rename options if required for your system. 
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by Dennis N on 2014-09-22
This thread is now marked "solved", so I assume this repair worked out, and all OSes are (at least for now) bootable from a single grub menu. 

In the end, the /EFI/ubuntu folder and its contents created in /sda1 by the previous Mint install get replaced, and only Ubuntu now has a folder in sda1 (this happens because Mint 16 and 17 also use 'ubuntu' as the name of that boot folder). 

To be exact, the second Mint install replaced the /EFI/ubuntu folder of the first Mint, then the /EFI/ubuntu folder of Ubuntu replaced the identically-named folder of the second Mint, courtesy of Boot Repair.

What could possibly go wrong? (rhetorical)

---

