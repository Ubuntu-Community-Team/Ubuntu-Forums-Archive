---
title: "Can not choose boot from WIN7 after installed Ubuntu 14.04"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by rainer6 on 2015-02-27
Can not choose boot from WIN7 after installed Ubuntu 14.04. Maybe i made a mistake and installed Ubuntu not in EFI-Mode. I used a Boot-Repair USB-Stick to solve the problem. I selected recommended repair and now i have boot options but WIN7 is lacking.
Boot-Repair gave me following link: paste.ubuntu.com/10451550

---

### Post by fantab on 2015-02-27
> Maybe i made a mistake and installed Ubuntu not in EFI-Mode.
Your HDD set up does NOT support UEFI booting. Both your Windows and Ubuntu is installed in BIOS/Legacy mode.
However, your Live Ubuntu USB/DVD is perhaps booting in UEFI mode, maybe because UEFI- boot is enabled in UEFI/BIOS menu.
```

parted -l:

Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
[COLOR=#b22222]Partition Table: msdos[/COLOR]

Number  Start   End    Size    Type      File system     Flags
1      1049kB  106MB  105MB   primary   ntfs
2      106MB   105GB  105GB   primary   ntfs
3      105GB   106GB  1024MB  primary   ext4            boot
4      106GB   200GB  94.2GB  extended
5      106GB   114GB  8191MB  logical   linux-swap(v1)
6      114GB   165GB  51.2GB  logical   ext4
7      165GB   200GB  34.8GB  logical   ext4
```

Also 'fdisk' reports that you have:
```

/dev/sda4       206804990   390834175    92014593    5  Extended
[COLOR=#b22222]Partition 4 does not start on physical sector boundary[/COLOR].
/dev/sda5       206804992   222803967     7999488   82  Linux swap / Solaris
```

So, boot with your Ubuntu USB/DVD in BIOS/Legacy/Non-Uefi mode: [**see here**]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know the difference.
You may have to disable UEFI booting in UEFI/BIOS menu and enable BIOS/Legacy/CSM' mode.

Download and install 'gdisk' package in Live Ubuntu. Then run:
```
sudo fixparts /dev/sda
```
[Fixparts tutorial]("http://www.rodsbooks.com/fixparts/"). Just run fixparts and it should correct the 'Partition 4 does not start on physical sector boundary'. 'q' will quit without saving, and 'w' will quit saving changes. 
It is recommended that you backup your partition table as shown in the tutorial.

Reinstall Grub: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
Reboot... 

If you still have problems booting Windows7, then you will have to '[**Fix MBR**]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")' in Windows.
This process will remove grub from MBR and replace it with Windows' loader. 
If Windows boot is fine then reinstall-grub as shown above.

good luck...

---

