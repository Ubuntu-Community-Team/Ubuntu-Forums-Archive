---
title: "Can't boot Windows 7 via grub after installing Ubuntu 14.04 on HP Elitebook"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by Pinkotechie on 2014-09-04
To deal with the fact that my new HP Elitebook 840 was pre-installed with Windows 7 and configured to have 4 primary partitions, I deleted the HP_TOOLS partition and made it into an extended partition, as described here: [http://askubuntu.com/questions/149821/my-disk-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-disk-already-has-4-primary-partitions-how-can-i-install-ubuntu)

I then installed Ubuntu 14.04 from a USB, and that went well, but when I was done no Windows boot option was available on startup, even after using workaround 1 at [https://wiki.archlinux.org/index.php/HP_EliteBook_840_G1#Workaround_1:_Using_the_.22Customized_Boot.22_path_option_.28recommended.29](https://wiki.archlinux.org/index.php/HP_EliteBook_840_G1#Workaround_1:_Using_the_.22Customized_Boot.22_path_option_.28recommended.29).

I ran boot-repair 3 times with no improvement. The pastebin links give the boot info results for each attempt:

1) with the defaut settings:
[http://paste.ubuntu.com/8232689/]("http://paste.ubuntu.com/8237269/")

2) with the deftault settings after creating a secondary FAT32 partition with the boot flag:
[http://paste.ubuntu.com/8237269/](http://paste.ubuntu.com/8237269/)

3) with advanced settings, to set up a "Separate /boot/efi partition"
[http://paste.ubuntu.com/8234180/](http://paste.ubuntu.com/8234180/)

Any ideas how I should proceed?

---

### Post by fantab on 2014-09-04
> Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda8/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda8/EFI/Boot/bootx64.efi
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.

```
parted -l:

Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
**Partition Table: msdos**

Number  Start   End     Size    Type      File system     Flags
1      1049kB  1076MB  1075MB  primary   ntfs
2      1076MB  139GB   137GB   primary   ntfs
4      139GB   485GB   346GB   extended
5      139GB   458GB   319GB   logical   ext4
**8      458GB   458GB   209MB   logical   fat32           boot**
6      458GB   483GB   24.6GB  logical   linux-swap(v1)
7      483GB   485GB   2047MB  logical   fat32
3      485GB   498GB   13.1GB  primary   ntfs
```

> sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

Its a mess.
You have UEfI boot enabled.
You have 'MBR/msdos' disk, with an extended partition. With UEFI boot your Disk needs to be GPT. (MBR disks have only 4 primary partitions limit, GPT does not).
You have Windows and Ubuntu bootloader files in ESP or Efi System Partition. ESP is required by UEFI to boot any OS from GPT disk.

> With UEFI, gpt partitioning is required. If multiple drives, all bootable  drives need to be gpt and best if data drives are also gpt in case  later you want to make it bootable. With gpt there is no primary,  extended, logical partitions as in MBR(msdos) nor the 4 primary  partition limit. 
You can only have one efi partition per drive and with gparted you use  the boot flag to assign it as the efi partition. No other partitions can  have boot flag. Only if booting in BIOS mode with Ubuntu on gpt  partitioned drive, you need a bios_grub partition. 
Windows will only boot in UEFI mode so you cannot install Windows to gpt drive unless booting with UEFI.

You will have to reinstall both os... your hard disk needs to be properly setup.
It needs a GPT table to boot with UEFI or a 'msdos' table for 'legacy' boot.

---

### Post by Gavin_Coyne on 2014-09-04
It sounds like you are having a similar problem to the one I just had installing windows 8.1 dual booting with Ubuntu 14.04.  It took me a while to find a solution. once I had both operating systems installed on seperate paritions I ran the boot-repair, restarted noticed that windows did not show up in grub. Booted up Ubuntu and ran **sudo update-grub **I then restarted and windows was showing up in grub.

---

### Post by Pinkotechie on 2014-09-07
Gavin, your suggestion that I run sudo update-grub didn't help; I think fantab was right that there was no way to make that setup work. The fundamental problem, I think, was that the partition table was MSDOS and the EFI partition needs to be the first partition. 

In any case I took the notion that for EFI to work the partition table really needs to be GPT, and followed a procedure like [http://askubuntu.com/questions/400602/uefi-dual-boot-ubuntu-12-04-3-windows-8-1-one-gpt-hdd](http://askubuntu.com/questions/400602/uefi-dual-boot-ubuntu-12-04-3-windows-8-1-one-gpt-hdd). I now have working Windows 7 and Ubuntu 14.04 installs, but it's very awkward to get Ubuntu to boot; I have to manually navigate to the correct /EFI/ubuntu/grubx64.efi file each time. 

I've tried boot-repair, twice, to no avail: [http://paste2.org/ydMKIn68](http://paste2.org/ydMKIn68)

I've tried to set up the "Customized Boot" path in the HP BIOS to /EFI/ubuntu/grubx64.efi (and making it the first boot option) as described at [https://wiki.archlinux.org/index.php/HP_EliteBook_840_G1](https://wiki.archlinux.org/index.php/HP_EliteBook_840_G1). The system still defaults to booting straight into Windows.

Any suggestions how to get this system to boot into GRUB (and thus give me some control over which OS boots first)?

---

### Post by christopher9 on 2014-09-08
rEFInd ? 

[www.rodsbooks.com/refind/](www.rodsbooks.com/refind/)
[http://sourceforge.net/projects/refind/](http://sourceforge.net/projects/refind/)

---

### Post by fantab on 2014-09-09
[QUOTE=archwiki]The problem is that HP hard coded the paths for the OS boot manager in their UEFI boot manager to \EFI\Microsoft\Boot\bootmgfw.efi to boot Microsoft Windows, regardless of how the UEFI NVRAM variables are changed. [/QUOTE]
> I've tried to set up the "Customized Boot" path in the HP BIOS to  /EFI/ubuntu/grubx64.efi (and making it the first boot option) ... The system still defaults to booting straight into Windows.
Check again the 'customized boot' path... check if you've made any mistakes.

As suggested 'rEFInd' is a good alternative to 'Grub', try it. 
Or try '[EasyBCD]("https://neosmart.net/EasyBCD/")' (its a freeware for personal use), an alternative Windows boot loader that supports Linux booting.
Since HP is using a hard coded boot path... perhaps BCD can help.
Or... if neither works then leave the setup as it is though its tag 'awkward'.

---

### Post by oldfred on 2014-09-10
I am not sure how you got the efi partition.

But you BIOS based install of Windows on a MBR(msdos) drive will not work with UEFI. But it looks like that may be repairable. 
The issue is that you did not install grub to sda or the MBR of the drive, but installed it to the PBR or partition boot sector of Windows. The PBR must have Windows signature as it tells Windows what to boot with bootmgr for newer Windows or ntldr for XP.

      ```
 sda1: _______________________________________________

       File system:       ntfs
    [COLOR=#ff0000]Boot sector type:  Grub2 (v1.99-2.00)[/COLOR]
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 602354832 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    [COLOR=#ff0000]Boot files:        /bootmgr /Boot/BCD[/COLOR]


```    

You can use testdisk to restore a backup PBR that NTFS keeps.
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

