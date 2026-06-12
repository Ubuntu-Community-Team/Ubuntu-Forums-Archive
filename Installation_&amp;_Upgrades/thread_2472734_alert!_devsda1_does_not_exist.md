---
title: "alert! /dev/sda1 does not exist"
date: 2022-03-10
forum: Installation &amp; Upgrades
---

### Post by fiver22 on 2022-03-10
Hi, after kernel updates I rebooted.

GRUB v2.04 loads as normal -allowing me to select whichever kernel -but regardless of the kernel selected initramfs loads with the message:

`Gave up waiting for root file system device. Common problems: Boot args (cat /proc cmdline) Check rootdelay= did the system wait long enough?) Missing modules (cat /proc/modules; ls /dev) ALERT! /dev/sda1 does not exist. Dropping to a shell BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu6.4) built-in shell (ash) Enter “help” for a list of built-in commands.`

 I initially thought I needed to update-grub, so chrooted and did so. the commands ran without error but on reboot the issue persists.

I'm at a loss and this install is pretty important to me as it serves som samba shares at my office.
The data is intact -I can mount the disk (/dev/sda1/) and browse through the files and I can chroot successfully.

One oddity is that the disk is ZFS -no clue why I did that, it was years ago and hasn't been an issue or required any special care since installation. 

I'm linking to boot repair output in case that tells you anything of use.

[Boot Repair Output]("https://pastebin.ubuntu.com/p/R5924HPt92/")

fstab hasn't changed (so far as I can tell)
the grub entries haven't changed (so far ads I can tell) and appear correct
((...)root=/dev/sda1 (...))

Any help would be appreciated.

Edit: didn't realize pastebin.ubuntu.com required login to view... 
```

boot-repair-4ppa200                                              [20220310_1714]

============================== Boot Info Summary ===============================


sda: ___________________________________________________________________________

    File system:       zfs_member
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 1 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

sdf: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.4 LTS on sda1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GF108 [GeForce GT 430] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1202    from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 0x26fb1217
      Boot Start        End    Sectors  Size Id Type
sda1  *     2048 3907028991 3907026944  1.8T 83 Linux
Disk sdf: 7.5 GiB, 8016363520 bytes, 15656960 sectors
Disk identifier: 0x2c534026
      Boot Start     End Sectors  Size Id Type
sdf1  *        0 1802239 1802240  880M  0 Empty
sdf2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk zram0: 734.7 MiB, 770404352 bytes, 188087 sectors
Disk zram1: 734.7 MiB, 770404352 bytes, 188087 sectors
Disk zram2: 734.7 MiB, 770404352 bytes, 188087 sectors
Disk zram3: 734.7 MiB, 770404352 bytes, 188087 sectors

parted -lm (filtered): _________________________________________________________

sda:2000GB:scsi:512:4096:msdos:ATA ST2000DM001-1ER1:;
1:1049kB:2000GB:2000GB:ext4::boot;
sdf:8016MB:scsi:512:512:msdos:Lexar USB Flash Drive:;
2:494kB:3017kB:2523kB:::esp;

Free space >10MiB: ______________________________________________________________

sdf: 2.88MiB:7645MiB:7642MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE     UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda    zfs_member                                                                                                  
&#9492;&#9472;sda1 zfs_member                                                                                                  
sdf    iso9660    2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sdf1 iso9660    2020-06-13-00-42-55-00               2c534026-01                          Boot-Repair-Disk 64bit 
&#9492;&#9472;sdf2 vfat       D055-8513                            2c534026-02                          Boot-Repair-Disk 64bit 

Mount points (filtered): _______________________________________________________

            Avail Use% Mounted on
/dev/sdf         0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sdf    iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

====================== sdf/boot/grub/grub.cfg (filtered) =======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

==================== sdf: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdf

00000000  33 ed 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |3...............|
00000010  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  04 17 00 00 00 00 00 00  26 40 53 2c 00 00 80 00  |........&@S,....|
000001c0  01 00 00 3f e0 6f 00 00  00 00 00 80 1b 00 00 fe  |...?.o..........|
000001d0  ff ff ef fe ff ff c4 03  00 00 40 13 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by Claus7 on 2022-03-11
Hello,

have you checked this one [https://askubuntu.com/questions/247541/gave-up-waiting-for-root-device-on-ubuntu?](https://askubuntu.com/questions/247541/gave-up-waiting-for-root-device-on-ubuntu?)

Regards!

---

### Post by fiver22 on 2022-03-11
double post

---

### Post by fiver22 on 2022-03-11
> **Claus7 said:**
> Hello,

have you checked this one [https://askubuntu.com/questions/247541/gave-up-waiting-for-root-device-on-ubuntu?](https://askubuntu.com/questions/247541/gave-up-waiting-for-root-device-on-ubuntu?)

Regards!

Thank you for your reply.

I should have mentioned that I had seen that post and tried both booting in different hardware and making sure SATA was configured as AHCI.

I do appreciate your trying to help.

---

### Post by oldfred on 2022-03-11
Do not know ZFS.
But you installed grub to sda1, grub always should be installed to a drive like sda, not a partition like sda1.
With ext4, you can have grub in PBR/BS - partition boot sector, but still must have a working grub in MBR as BIOS only boots from MBR.
With Windows having grub in PBR, breaks NTFS, not sure if ZFS expects some info in PBR or having grub in PBR is ok.

---

### Post by fiver22 on 2022-03-11
> **oldfred said:**
> Do not know ZFS.
But you installed grub to sda1, grub always should be installed to a drive like sda, not a partition like sda1.
With ext4, you can have grub in PBR/BS - partition boot sector, but still must have a working grub in MBR as BIOS only boots from MBR.
With Windows having grub in PBR, breaks NTFS, not sure if ZFS expects some info in PBR or having grub in PBR is ok.

I'll try moving grub to to sda -thanks!

---

