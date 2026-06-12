---
title: "How to access ubuntu alongside Windows 7"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by joey_tbf on 2015-04-26
Hello.  I am joey

I am new here. I want to learn no linux/unix/ubuntu so i have installed it on my laptop. 

I installed it visa USB stick. But the problem is after i restarted my computer. Windows 7 starts up. 

I thought i would get the choice of which os to start. 

How can i access or get my laptop to ask me which OS to log into. 


Thanks,

---

### Post by yancek on 2015-04-26
That would be explained by your not correctly installing the Ubuntu Grub bootloader although there may be other reasons.  During the installation, there is an option for "Device for bootloader installation" which is set to a default of /dev/sda.  That would install to the master boot record of the primary drive and create a menuentry for both Ubuntu and windows from which you could select on boot.  Either you changed this or something went wrong.  More information would be needed and probably the best way to get it is to boot the Ubuntu flash drive and go to the site below.  Download and run boot repair selecting the option to "Create a Bootinfo Summary" and post the output here.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by joey_tbf on 2015-04-26
Here is my summy

```
[COLOR=#444444][FONT=Calibri] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015][/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]============================= Boot Info Summary: ===============================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri] => Windows 7/8/2012 is installed in the MBR of /dev/sda.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri] => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda1: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       ntfs[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  Windows 7/2008: NTFS[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Operating System:  [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot files:        /bootmgr /Boot/BCD[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda2: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       ntfs[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  Windows 7/2008: NTFS[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Operating System:  Windows 7[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot files:        /Windows/System32/winload.exe[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda3: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       Extended Partition[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  Unknown[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info: [/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda5: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  -[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info: [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Operating System:  Ubuntu 14.04 LTS [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot files:        /etc/fstab[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda6: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       swap[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  -[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info: [/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sdb1: __________________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]    File system:       vfat[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector type:  SYSLINUX 4.07 2013-07-25[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot sector info:  Syslinux looks at sector 29888 of /dev/sdb1 for its [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]                       second stage. SYSLINUX is installed in the /uui [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]                       directory. No errors found in the Boot Parameter Block.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Operating System:  [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]                       /EFI/BOOT/grubx64.efi[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]============================ Drive/Partition Info: =============================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Drive: sda _____________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2             206,848   953,376,207   953,169,360   7 NTFS / exFAT / HPFS[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda3         953,376,766   976,771,071    23,394,306   5 Extended[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5         953,376,768   960,229,375     6,852,608  83 Linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda6         960,231,424   976,771,071    16,539,648  82 Linux swap / Solaris[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]Drive: sdb _____________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Disk /dev/sdb: 3926 MB, 3926949888 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 477 cylinders, total 7669824 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]/dev/sdb1    *             63     7,669,823     7,669,761   c W95 FAT32 (LBA)[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]"blkid" output: ________________________________________________________________[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Device           UUID                                   TYPE       LABEL[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]/dev/loop0                                              squashfs   [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1        F2442E3C442E03C7                       ntfs       System Reserved[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2        D0A23007A22FF0A0                       ntfs       [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5        9e570865-d08d-49f5-92a2-ec76b66738a7   ext4       [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda6        e1b622bc-5ce7-4599-9c60-673df6f2afe3   swap       [/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1        1F03-3C37                              vfat       UUI[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]========================= "ls -l /dev/disk/by-id" output: ======================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]total 0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root  9 Apr 26 14:49 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763 -> ../../sda[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26 14:50 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763-part1 -> ../../sda1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26 14:50 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763-part2 -> ../../sda2[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763-part3 -> ../../sda3[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763-part5 -> ../../sda5[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 ata-WDC_WD5000LPVX-22V0TT0_WD-WX11E83EY763-part6 -> ../../sda6[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root  9 Apr 26 14:49 usb-Kingston_DataTraveler_G3_001CC0EC2F39EB71B5CB0077-0:0 -> ../../sdb[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 usb-Kingston_DataTraveler_G3_001CC0EC2F39EB71B5CB0077-0:0-part1 -> ../../sdb1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root  9 Apr 26 14:49 wwn-0x50014ee603f63753 -> ../../sda[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26 14:50 wwn-0x50014ee603f63753-part1 -> ../../sda1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26 14:50 wwn-0x50014ee603f63753-part2 -> ../../sda2[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 wwn-0x50014ee603f63753-part3 -> ../../sda3[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 wwn-0x50014ee603f63753-part5 -> ../../sda5[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]lrwxrwxrwx 1 root root 10 Apr 26  2015 wwn-0x50014ee603f63753-part6 -> ../../sda6[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]================================ Mount points: =================================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Device           Mount_Point              Type       Options[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=============================== sda5/etc/fstab: ================================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]--------------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# / was on /dev/sda5 during installation[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]UUID=9e570865-d08d-49f5-92a2-ec76b66738a7 /               ext4    errors=remount-ro 0       1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# swap was on /dev/sda6 during installation[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]UUID=e1b622bc-5ce7-4599-9c60-673df6f2afe3 none            swap    sw              0       0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]--------------------------------------------------------------------------------[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=========================== sdb1/boot/grub/grub.cfg: ===========================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]--------------------------------------------------------------------------------[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]if loadfont /boot/grub/font.pf2 ; then[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    set gfxmode=auto[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    insmod efi_gop[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    insmod efi_uga[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    insmod gfxterm[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    terminal_output gfxterm[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]fi[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]set menu_color_normal=white/black[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]set menu_color_highlight=black/light-gray[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]menuentry "Try Ubuntu without installing" {[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    set gfxpayload=keep[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    initrd    /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]}[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]menuentry "Install Ubuntu" {[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    set gfxpayload=keep[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    initrd    /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]}[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]menuentry "OEM install (for manufacturers)" {[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    set gfxpayload=keep[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    initrd    /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]}[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]menuentry "Check disc for defects" {[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    set gfxpayload=keep[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]    initrd    /casper/initrd.lz[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]}[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]--------------------------------------------------------------------------------[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]======================== Unknown MBRs/Boot Sectors/etc: ========================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Unknown BootLoader on sda3[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]00000000  fc 1d 8f 2e 78 8c 46 46  b2 a7 92 ec 91 9e ea 21  |....x.FF.......!|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000010  eb 3d 09 85 f6 27 f2 9a  f1 cb 6c 30 dd 24 25 06  |.=...'....l0.$%.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000020  8d 9b c3 65 fd 91 36 aa  0c bf 09 73 a1 f9 d8 77  |...e..6....s...w|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000030  76 cc b7 8e 8a ba 5c 40  7b 03 0b 05 c0 bb 3e 4d  |v.....\@{.....>M|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000040  51 fd c2 52 d6 05 56 c9  9f 0c 85 8e 86 09 6b b3  |Q..R..V.......k.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000050  25 ec 90 95 f2 f4 52 b7  b6 cc 34 2c f2 f3 66 bb  |%.....R...4,..f.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000060  e2 36 b4 a5 fb 6e 05 5e  56 d4 d4 c2 62 87 f0 e3  |.6...n.^V...b...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000070  a5 4e 9f 33 65 87 97 28  93 02 b3 18 59 b8 22 24  |.N.3e..(....Y."$|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000080  a9 b7 72 60 23 07 8e 8b  86 70 b6 ca f3 51 b7 cd  |..r`#....p...Q..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000090  04 e8 bc c4 b2 6e dc 91  8d f9 3b 3d a8 76 63 4a  |.....n....;=.vcJ|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000a0  33 25 86 6b 2e c1 c8 00  87 17 f5 cc 6a f2 69 6d  |3%.k........j.im|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000b0  18 6a 94 9c 4b dc 1f d7  fd 6b b8 6b 6a ba 7c 6b  |.j..K....k.kj.|k|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000c0  fe f7 c6 1a 07 86 69 4b  79 0f c3 26 7d 4b de 97  |......iKy..&}K..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000d0  a7 21 13 83 32 f8 b4 13  0e ca 7c 41 31 c6 6b 95  |.!..2.....|A1.k.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000e0  fc 37 77 34 7b 9d 23 d5  24 12 f2 30 1c 7a e9 73  |.7w4{.#.$..0.z.s|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000f0  d5 5a 9e c3 a3 94 6f f1  b9 ec 57 30 85 a9 46 36  |.Z....o...W0..F6|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000100  51 83 aa 03 d6 5c 85 1c  48 c7 f2 3e 1d 4c 7f 1e  |Q....\..H..>.L..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000110  20 d2 3a eb 20 1c 40 7c  27 3d b3 39 68 17 02 18  | .:. .@|'=.9h...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000120  70 29 69 a6 fb 61 44 74  7a 60 9f 46 8a 10 db 72  |p)i..aDtz`.F...r|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000130  be db 84 a7 24 3d c3 d0  40 09 33 99 da 24 77 e2  |....$=..@.3..$w.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000140  c2 1f 99 d8 25 58 73 89  fb 16 6b c8 3f 01 26 de  |....%Xs...k.?.&.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000150  2f 91 05 14 4c 41 73 d4  0d d4 7a 86 58 ae 1b 09  |/...LAs...z.X...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000160  df 1a ac 70 17 63 3f 8a  c7 22 24 66 a2 8d d7 4e  |...p.c?.."$f...N|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000170  9e c1 9f 62 67 d0 52 8e  8c ab 31 0a ba d7 9f 62  |...bg.R...1....b|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000180  f6 25 73 a2 3d 11 b1 d1  f2 7e a7 1a 04 8a ec 7f  |.%s.=....~......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000190  4d 2e 81 e6 9f 3b 4c 84  ba 6d eb 00 f7 b9 03 88  |M....;L..m......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001a0  1e b9 84 b8 2f ff 8a af  e4 74 98 8a 5a d4 40 97  |..../....t..Z.@.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001b0  bf 63 e8 b0 18 63 cf fa  3e 99 92 ec 24 55 00 fe  |.c...c..>...$U..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 68 00 00 fe  |............h...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001d0  ff ff 05 fe ff ff 02 90  68 00 00 68 fc 00 00 00  |........h..h....|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000200[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=============================== StdErr Messages: ===============================[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]File descriptor 9 (/proc/6387/mounts) leaked on lvs invocation. Parent PID 13470: bash[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]File descriptor 63 (pipe:[46934]) leaked on lvs invocation. Parent PID 13470: bash[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]  No volume groups found[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]ADDITIONAL INFORMATION :[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]=================== log of boot-info 2015-04-26__14h49 ===================[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]boot-info version : 4ppa33[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]boot-sav version : 4ppa33[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]glade2script version : 3.2.2~ppa47~saucy[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]boot-sav-extra version : 4ppa33[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]boot-info is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]CPU op-mode(s):        32-bit, 64-bit[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ls: cannot access /home/usr/.config: No such file or directory[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== os-prober:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1:Windows 7 (loader):Windows:chain[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5:Ubuntu 14.04 LTS (14.04):Ubuntu:linux[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== blkid:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/loop0: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1: LABEL="System Reserved" UUID="F2442E3C442E03C7" TYPE="ntfs"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2: UUID="D0A23007A22FF0A0" TYPE="ntfs"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5: UUID="9e570865-d08d-49f5-92a2-ec76b66738a7" TYPE="ext4"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda6: UUID="e1b622bc-5ce7-4599-9c60-673df6f2afe3" TYPE="swap"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1: LABEL="UUI" UUID="1F03-3C37" TYPE="vfat"[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Windows not detected by os-prober on sda2.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Warning: extended partition does not start at a cylinder boundary.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]DOS and Linux will interpret the contents differently.[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== sda5/etc/grub.d/ :[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]drwxr-xr-x  2 root root    4096 Apr 26 02:19 grub.d[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]total 76[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root  9424 Apr 11  2014 00_header[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root 11608 Apr 11  2014 10_linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root 10412 Apr 11  2014 20_linux_xen[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root   214 Apr 11  2014 40_custom[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rwxr-xr-x 1 root root   216 Apr 11  2014 41_custom[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]-rw-r--r-- 1 root root   483 Apr 11  2014 README[/FONT][/COLOR]




[COLOR=#444444][FONT=Calibri]=================== sda5/etc/default/grub :[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# If you change this file, run 'update-grub' afterwards to update[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# /boot/grub/grub.cfg.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# For full documentation of the options in this file, see:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#   info -f grub -n 'Simple configuration'[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]GRUB_DEFAULT=0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_HIDDEN_TIMEOUT=0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_TIMEOUT=10[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]GRUB_CMDLINE_LINUX=""[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# This works with Linux (no patch required) and with any kernel that obtains[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# Uncomment to disable graphical terminal (grub-pc only)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_TERMINAL=console[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# The resolution used on graphical terminal[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# note that you can use only modes which your graphic card supports via VBE[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]# you can see them in real GRUB with the command `vbeinfo'[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_GFXMODE=640x480[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_DISABLE_LINUX_UUID=true[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# Uncomment to disable generation of recovery mode menu entries[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_DISABLE_RECOVERY="true"[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]# Uncomment to get a beep at grub start[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]#GRUB_INIT_TUNE="480 440 1"[/FONT][/COLOR]



[COLOR=#444444][FONT=Calibri]=================== No kernel in /mnt/boot-sav/sda5/boot:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]abi-3.13.0-24-generic[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]config-3.13.0-24-generic[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]grub[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]memtest86+.bin[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]memtest86+.elf[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]memtest86+_multiboot.bin[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]System.map-3.13.0-24-generic[/FONT][/COLOR]



[COLOR=#444444][FONT=Calibri]=================== UEFI/Legacy mode:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]This live-session is not in EFI-mode.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]EFI in dmesg.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][    0.000000] ACPI: UEFI 0000000078b1b000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri][    0.000000] ACPI: UEFI 0000000078b19000 000042 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]SecureBoot maybe enabled.[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=================== PARTITIONS & DISKS:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda5    : sda,    not-sepboot,    no-grubenv    grub2,    signed grub-pc ,    update-grub,    64,    no-kernel,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=================== parted -l:[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Model: ATA WDC WD5000LPVX-2 (scsi)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500GB[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512B/4096B[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Number  Start   End    Size    Type      File system     Flags[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]1      1049kB  106MB  105MB   primary   ntfs            boot[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]2      106MB   488GB  488GB   primary   ntfs[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]3      488GB   500GB  12.0GB  extended[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]5      488GB   492GB  3509MB  logical   ext4[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]6      492GB   500GB  8468MB  logical   linux-swap(v1)[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]Model: Kingston DataTraveler G3 (scsi)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk /dev/sdb: 3927MB[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition Table: msdos[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Number  Start   End     Size    Type     File system  Flags[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]1      32.3kB  3927MB  3927MB  primary  fat32        boot, lba[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== parted -lm:[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]BYT;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda:500GB:scsi:512:4096:msdos:ATA WDC WD5000LPVX-2;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]1:1049kB:106MB:105MB:ntfs::boot;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]2:106MB:488GB:488GB:ntfs::;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]3:488GB:500GB:12.0GB:::;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]5:488GB:492GB:3509MB:ext4::;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]6:492GB:500GB:8468MB:linux-swap(v1)::;[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]BYT;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb:3927MB:scsi:512:512:msdos:Kingston DataTraveler G3;[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]1:32.3kB:3927MB:3927MB:fat32::boot, lba;[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== lsblk:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]KNAME TYPE FSTYPE     SIZE LABEL    MODEL    UUID[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda   disk          465.8G          WDC WD50[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda1  part ntfs       100M System Reserved[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]F2442E3C442E03C7[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda2  part ntfs     454.5G                   D0A23007A22FF0A0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda3  part              1K[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda5  part ext4       3.3G                   9e570865-d08d-49f5-92a2-ec76b66738a7[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda6  part swap       7.9G                   e1b622bc-5ce7-4599-9c60-673df6f2afe3[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sdb   disk            3.7G          DataTrav[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sdb1  part vfat       3.7G UUI               1F03-3C37[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]loop0 loop squashfs   922M[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]KNAME ROTA RO RM STATE   MOUNTPOINT[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda      1  0  0 running[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda1     1  0  0         /mnt/boot-sav/sda1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda2     1  0  0         /mnt/boot-sav/sda2[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda3     1  0  0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda5     1  0  0         /mnt/boot-sav/sda5[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sda6     1  0  0         [SWAP][/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sdb      1  0  1 running[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sdb1     1  0  1         /cdrom[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]loop0    1  1  0         /rofs[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=================== mount:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/cow on / type overlayfs (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]proc on /proc type proc (rw,noexec,nosuid,nodev)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]udev on /dev type devtmpfs (rw,mode=0755)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/loop0 on /rofs type squashfs (ro,noatime)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /sys/fs/cgroup type tmpfs (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /sys/fs/fuse/connections type fusectl (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /sys/kernel/debug type debugfs (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /sys/kernel/security type securityfs (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]tmpfs on /tmp type tmpfs (rw,nosuid,nodev)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /run/shm type tmpfs (rw,nosuid,nodev)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none on /sys/fs/pstore type pstore (rw)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=================== ls:[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhost-net video0 zero[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ls /dev/mapper:  control[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== hexdump -n512 -C /dev/sda1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000040  f6 00 00 00 01 00 00 00  c7 03 2e 44 3c 2e 44 f2  |...........D<.D.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000200[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== hexdump -n512 -C /dev/sda2[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000020  00 00 00 00 80 00 80 00  c8 35 d0 38 00 00 00 00  |.........5.8....|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000040  f6 00 00 00 01 00 00 00  a0 f0 2f a2 07 30 a2 d0  |........../..0..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]00000200[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== df -Th:[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Filesystem     Type       Size  Used Avail Use% Mounted on[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/cow           overlayfs  3.9G   91M  3.8G   3% /[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]udev           devtmpfs   3.9G   12K  3.9G   1% /dev[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]tmpfs          tmpfs      788M  1.2M  787M   1% /run[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1      vfat       3.7G  964M  2.8G  26% /cdrom[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/loop0     squashfs   923M  923M     0 100% /rofs[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]tmpfs          tmpfs      3.9G  1.2M  3.9G   1% /tmp[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none           tmpfs      3.9G   76K  3.9G   1% /run/shm[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]none           tmpfs      100M   56K  100M   1% /run/user[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2      fuseblk    455G  454G  1.1G 100% /mnt/boot-sav/sda2[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5      ext4       3.2G  3.2G     0 100% /mnt/boot-sav/sda5[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]=================== fdisk -l:[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk identifier: 0xbc01f9b7[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda2          206848   953376207   476584680    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda3       953376766   976771071    11697153    5  Extended[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Partition 3 does not start on physical sector boundary.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda5       953376768   960229375     3426304   83  Linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sda6       960231424   976771071     8269824   82  Linux swap / Solaris[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Disk /dev/sdb: 3926 MB, 3926949888 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]255 heads, 63 sectors/track, 477 cylinders, total 7669824 sectors[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Disk identifier: 0xc8ecaf51[/FONT][/COLOR]

[COLOR=#444444][FONT=Calibri]Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]/dev/sdb1   *          63     7669823     3834880+   c  W95 FAT32 (LBA)[/FONT][/COLOR]




[COLOR=#444444][FONT=Calibri]=================== Suggested repair[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda5 into the MBR of sda, using the following options:     kernel-purge[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot[/FONT][/COLOR]


[COLOR=#444444][FONT=Calibri]=================== User settings[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]The settings chosen by the user will not act on the boot.[/FONT][/COLOR]

```

---

### Post by yancek on 2015-04-26
The first line of the report indicates that windows code is installed to the master boot record so that means you did not install the Ubuntu Grub bootloader.  You have Ubuntu installed to sda5 but it does not show any boot files that are normally shown there.  Since it is a new install, it may be easier to reinstall Ubuntu.  You could try reinstalling Grub using the methods at the link below, installing via the Live CD would probably be best in your circumstances. 

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by Mark Phelps on 2015-04-26
BEFORE you make any other changes, do yourself a favor and use the Backup feature of Win7 to create and burn a Win7 Repair CD.  You will need this later if the boot loader gets corrupted in some way, and if you don't make it now (which is for free), then later, when you can't boot into Win7, you will have to PAY to download the ISO file to make it.

---

### Post by joey_tbf on 2015-04-29
Thanks for all the information.  I was unable to install both alongside.  I got to a screen where it said i had to make partitions because the current one was full. 

I used the slider to move it but it gave me a list of a bunch of partition.  I got fustrated and i decided to install it by itself. 

So now my laptop only has unbuntu.  I am playing with it now.  

I also have the orignal windows cd so i didn't make a backup cd.  I don't use the laptop often so i usually just install a fresh copy on windows if needed.   

Time to learn in terminal language! :D

---

### Post by yancek on 2015-04-29
If you decide to reinstall windows later, it will overwrite the boot code for Ubuntu without asking you or informing you that it is being done.  I would suggest you bookmark the link from my earlier post as it explains how to get the Grub bootloader back to boot both again.

Good luck with Ubuntu.

---

### Post by joey_tbf on 2015-05-19
Ok i will do that soon.  I've just been playing around with it lately. But my mission is to have both OS's on the same laptop. 


What i'm reading here is that for in order to have both of them on the same laptop.  The only way to do it is:

1. Install windows first. 
2. Install Ubuntu second. 



So i guess:
It's not possible to install unbuntu first. Then install windows second.

---

### Post by Vladlenin5000 on 2015-05-19
Not the only way but the recommended one for sure. Reason: Post #7.

---

