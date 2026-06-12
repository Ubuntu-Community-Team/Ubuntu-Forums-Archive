---
title: "Stuck on GRUB on startup"
date: 2021-12-03
forum: Installation &amp; Upgrades
---

### Post by Matteo_Castagna on 2021-12-03
This is the URL from the boot-repair utility: [https://paste.ubuntu.com/p/FxbvYFrNTg/](https://paste.ubuntu.com/p/FxbvYFrNTg/)

```
boot-repair-4ppa130                                              [20211203_1546]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 29880 of /dev/sde1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys


================================ 0 OS detected =================================


============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0017
Timeout: 1 seconds
BootOrder: 0000,0006,0007,0008,0009,000A,000B,000D,000E,000F,0010,0012,0013,0014,0015,0017,0016,0001,0002,0004,0005
Boot0000* ubuntu    HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive     BBS(HD,,0x0)..GO..NO........o.W.D.C. .W.D.5.0.0.0.A.A.K.S.-.0.0.A.7.B.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.S.A.4.Y.1.4.6.5.5.9........BO..NO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.0.0.W.N.4.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.6.C.0.Y.R.S.N.D.9.R........BO
Boot0002* CD/DVD Drive     BBS(CDROM,,0x0)..GO..NO........o.T.S.S.T.c.o.r.p. .C.D.D.V.D.W. .S.H.-.2.2.4.G.B....................A...........................>..Gd-.;.A..MQ..L.1.S.U.D.Y.6.H.D.0.3.1.0.Y.P. . . . . . ........BO
Boot0004* Unknown Device     BBS(8,,0x0)..GO..NO..........G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.F....................A...............................................<..Gd-.;.A..MQ..L.G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.F........BO..NO..........G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.O.M.B.O....................A....................................................B..Gd-.;.A..MQ..L.G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.O.M.B.O........BO
Boot0005* UEFI: Built-in EFI Shell     VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0006* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0007* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0008* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0009* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000A* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000B* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000D* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000E* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000F* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0010* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0012* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0013* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0014* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0015* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0016* Unknown Device     BBS(9,,0x0)..GO..NO........{.T.O.S.H.I.B.A. .U.S.B. .F.L.A.S.H. .D.R.I.V.E. .P.M.A.P....................A.......................N..Gd-.;.A..MQ..L.T.O.S.H.I.B.A. .U.S.B. .F.L.A.S.H. .D.R.I.V.E. .P.M.A.P........BO
Boot0017* UEFI: TOSHIBA USB FLASH DRIVE PMAP    PciRoot(0x0)/Pci(0x12,0x2)/USB(0,0)/HD(1,MBR,0x51a166,0x800,0x745d800)..BO
This session has been detected as 'live' because df -Th / contains overlay

85fa9d77b929ec4231aba29476574eb6   sda1/BOOT/fbx64.efi
469e608783843a701d172242f016c79c   sda1/BOOT/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdb1    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sda2    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 1EE12332-F085-4487-A86F-E98C52F9E310
        Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 976771071 975720448 465.3G Linux filesystem
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x97e94969
      Boot Start        End    Sectors   Size Id Type
sdb1        2048 1953523711 1953521664 931.5G 83 Linux
Disk sde: 58.19 GiB, 62474158080 bytes, 122019840 sectors
Disk identifier: 0x0051a166
      Boot Start       End   Sectors  Size Id Type
sde1  *     2048 122019839 122017792 58.2G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:gpt:ATA WDC WD5000AAKS-0:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:500GB:500GB:::;
sdb:1000GB:scsi:512:4096:msdos:ATA WDC WD10EZEX-00W:;
1:1049kB:1000GB:1000GB:ext4::;
sde:62.5GB:scsi:512:512:msdos:TOSHIBA USB FLASH DRIVE:;
1:1049kB:62.5GB:62.5GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 vfat     DF43-7186                            99ae749a-fcad-4a82-8958-9d653526689d             EFI System Partition
&#9492;&#9472;sda2                                               5065695f-a9f6-4c52-bccb-460b7d8a4d12             
sdb                                                                                                   
&#9492;&#9472;sdb1 ext4     a69a39ff-b678-4beb-a0fd-fb65058beb10 97e94969-01                          YaQue       
sde                                                                                                   
&#9492;&#9472;sde1 vfat     16F8-2A50                            0051a166-01                          UBUNTU 20_0 

df (filtered): _________________________________________________________________

                   Avail Use% Mounted on
sda1              505.8M   1% /mnt/boot-sav/sda1
sdb1              289.5G  63% /mnt/boot-sav/sdb1
sde1               55.3G   5% /cdrom

Mount options: __________________________________________________________________

sda1              rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sdb1              rw,relatime
sde1              ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid e752a32c-d61c-4773-b80f-b7892db1ea39 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sde1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

========================= sde1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sde1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sde1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda2

00000000  70 95 75 00 00 00 00 00  f8 97 75 00 00 00 00 00  |p.u.......u.....|
00000010  80 9a 75 00 00 00 00 00  a8 9d 75 00 00 00 00 00  |..u.......u.....|
00000020  88 a0 75 00 00 00 00 00  00 a3 75 00 00 00 00 00  |..u.......u.....|
00000030  70 a6 75 00 00 00 00 00  f8 a8 75 00 00 00 00 00  |p.u.......u.....|
00000040  80 ab 75 00 00 00 00 00  f8 ae 75 00 00 00 00 00  |..u.......u.....|
00000050  28 b2 75 00 00 00 00 00  00 b5 75 00 00 00 00 00  |(.u.......u.....|
00000060  88 b7 75 00 00 00 00 00  78 b9 75 00 00 00 00 00  |..u.....x.u.....|
00000070  78 bb 75 00 00 00 00 00  68 be 75 00 00 00 00 00  |x.u.....h.u.....|
00000080  c0 c0 75 00 00 00 00 00  68 c4 75 00 00 00 00 00  |..u.....h.u.....|
00000090  40 c7 75 00 00 00 00 00  20 ca 75 00 00 00 00 00  |@.u..... .u.....|
000000a0  90 cc 75 00 00 00 00 00  e8 ce 75 00 00 00 00 00  |..u.......u.....|
000000b0  e8 d1 75 00 00 00 00 00  18 d4 75 00 00 00 00 00  |..u.......u.....|
000000c0  48 d6 75 00 00 00 00 00  78 d8 75 00 00 00 00 00  |H.u.....x.u.....|
000000d0  68 da 75 00 00 00 00 00  00 f2 75 00 00 00 00 00  |h.u.......u.....|
000000e0  80 f4 75 00 00 00 00 00  70 f6 75 00 00 00 00 00  |..u.....p.u.....|
000000f0  70 f8 75 00 00 00 00 00  18 fc 75 00 00 00 00 00  |p.u.......u.....|
00000100  f0 fe 75 00 00 00 00 00  d0 01 76 00 00 00 00 00  |..u.......v.....|
00000110  40 04 76 00 00 00 00 00  98 06 76 00 00 00 00 00  |@.v.......v.....|
00000120  98 09 76 00 00 00 00 00  c8 0b 76 00 00 00 00 00  |..v.......v.....|
00000130  f8 0d 76 00 00 00 00 00  28 10 76 00 00 00 00 00  |..v.....(.v.....|
00000140  18 12 76 00 00 00 00 00  70 15 76 00 00 00 00 00  |..v.....p.v.....|
00000150  f0 17 76 00 00 00 00 00  e0 19 76 00 00 00 00 00  |..v.......v.....|
00000160  38 1d 76 00 00 00 00 00  b8 1f 76 00 00 00 00 00  |8.v.......v.....|
00000170  e8 21 76 00 00 00 00 00  18 24 76 00 00 00 00 00  |.!v......$v.....|
00000180  48 26 76 00 00 00 00 00  38 28 76 00 00 00 00 00  |H&v.....8(v.....|
00000190  38 2a 76 00 00 00 00 00  90 2d 76 00 00 00 00 00  |8*v......-v.....|
000001a0  70 30 76 00 00 00 00 00  38 32 76 00 00 00 00 00  |p0v.....82v.....|
000001b0  40 36 76 00 00 00 00 00  18 39 76 00 00 00 00 00  |@6v......9v.....|
000001c0  a8 3b 76 00 00 00 00 00  18 3e 76 00 00 00 00 00  |.;v......>v.....|
000001d0  70 40 76 00 00 00 00 00  38 43 76 00 00 00 00 00  |p@v.....8Cv.....|
000001e0  c0 4c 76 00 00 00 00 00  18 50 76 00 00 00 00 00  |.Lv......Pv.....|
000001f0  98 52 76 00 00 00 00 00  c8 54 76 00 00 00 00 00  |.Rv......Tv.....|
00000200


========= Devices which don't seem to have a corresponding hard drive ==========

sdc sdd 

=============================== StdErr Messages ================================

File descriptor 63 (pipe:[86327]) leaked on lvs invocation. Parent PID 16359: /bin/bash
  /dev/sdc: open failed: No medium found
  /dev/sdd: open failed: No medium found
  /dev/sdc: open failed: No medium found
  /dev/sdd: open failed: No medium found

Error code 12
mount -r /dev/sda2 /mnt/boot-sav/sda2

mount -r /dev/sda2 : Error code 12
Error code 12
mount -r /dev/sda2 /mnt/boot-sav/sda2

mount -r /dev/sda2 : Error code 12
Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```


Thanks for any help.

Matteo

---

### Post by oldfred on 2021-12-03
Please use Code tags for terminal or longer text output.
Easy to add with # icon in Forum's advanced editor.
I changed your quote tags to code tags.

What was sda2? Does not even show as ext4, so cannot run fsck. 
Was this an LVM install with encryption?
Your grub boot entry is looking for an UUID, drive hd0,gpt2 that does not exist. That would be sda2?

Separately have have many duplicate UUID boot entries. 
Years ago some hardware crashed with too many entries. But still best not to have many duplicates that are not needed.
I would delete all but one of those.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). With Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by Matteo_Castagna on 2021-12-03
Thank you so much and sorry for misusing the tags.
I am sorry but I am not sure I can answer your questions about sda2. I know I have two physical HDs.
Question: I am currently booted with the liveDVD. I currently see one of the two HD I mentioned above (the one I use for the data - the other line in the picture below is the pen-drive with the liveDBD). I can't see the one where ubuntu is installed. I am starting to fear this is a case of a HD failure, is it possible?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289576&stc=1[/IMG]


This is the result of *sudo efibootmgr -v* :

```

BootCurrent: 0017
Timeout: 1 seconds
BootOrder: 0000,0006,0007,0008,0009,000A,000B,000D,000E,000F,0010,0012,0013,0014,0015,0017,0016,0001,0002,0004,0005
Boot0000* ubuntu    HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive     BBS(HD,,0x0)..GO..NO........o.W.D.C. .W.D.5.0.0.0.A.A.K.S.-.0.0.A.7.B.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.S.A.4.Y.1.4.6.5.5.9........BO..NO........o.W.D.C. .W.D.1.0.E.Z.E.X.-.0.0.W.N.4.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.6.C.0.Y.R.S.N.D.9.R........BO
Boot0002* CD/DVD Drive     BBS(CDROM,,0x0)..GO..NO........o.T.S.S.T.c.o.r.p. .C.D.D.V.D.W. .S.H.-.2.2.4.G.B....................A...........................>..Gd-.;.A..MQ..L.1.S.U.D.Y.6.H.D.0.3.1.0.Y.P. . . . . . ........BO
Boot0004* Unknown Device     BBS(8,,0x0)..GO..NO..........G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.F....................A...............................................<..Gd-.;.A..MQ..L.G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.F........BO..NO..........G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.O.M.B.O....................A....................................................B..Gd-.;.A..MQ..L.G.e.n.e.r.i.c. .F.l.a.s.h. .H.S.-.C.O.M.B.O........BO
Boot0005* UEFI: Built-in EFI Shell     VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0006* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0007* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0008* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0009* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000A* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000B* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000D* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000E* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot000F* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0010* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0012* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0013* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0014* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0015* UEFI: WDC WD5000AAKS-00A7B0    PciRoot(0x0)/Pci(0x11,0x0)/Sata(0,65535,0)/HD(1,GPT,99ae749a-fcad-4a82-8958-9d653526689d,0x800,0x100000)..BO
Boot0016* Unknown Device     BBS(9,,0x0)..GO..NO........{.T.O.S.H.I.B.A. .U.S.B. .F.L.A.S.H. .D.R.I.V.E. .P.M.A.P....................A.......................N..Gd-.;.A..MQ..L.T.O.S.H.I.B.A. .U.S.B. .F.L.A.S.H. .D.R.I.V.E. .P.M.A.P........BO
Boot0017* UEFI: TOSHIBA USB FLASH DRIVE PMAP    PciRoot(0x0)/Pci(0x12,0x2)/USB(0,0)/HD(1,MBR,0x51a166,0x800,0x745d800)..BO

```

---

### Post by Matteo_Castagna on 2021-12-03
Actually this doesn't seem the case.
The "Ubuntu disk" seems healthy.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289578&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289579&stc=1[/IMG]

---

### Post by Matteo_Castagna on 2021-12-03
This might be the problem.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289582&stc=1[/IMG]

---

### Post by oldfred on 2021-12-03
First suggestion is Disks & Smart Status or running Smart Status itself.
So drive looks ok.

I would not expect this to show anything different but you can try it. With gpt it looks at primary & backup partition tables.
sudo gdisk -l /dev/sda

That then does testdisk show?
Does it correct see a second partition on sda?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) & 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

---

### Post by Matteo_Castagna on 2021-12-03
The quick SMART test returned all OKs.
I am now running the longer one.

The *sudo gdisk -l /dev/sda* returns:

```

ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Model: WDC WD5000AAKS-0
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 1EE12332-F085-4487-A86F-E98C52F9E310
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  EFI System Partition
   2         1050624       976771071   465.3 GiB   8300  

```

---

### Post by oldfred on 2021-12-03
Partition table then looks ok.

Usually errors still show ext4, and then you can run fsck to repair it.
But if not seen as ext4, fsck will not work.

Does testdisk show anything?
Do you have good backups.

Many here  say if it takes more than an hour or two to fix, better to just reinstall & restore from backups.

---

### Post by Matteo_Castagna on 2021-12-03
I *should* have good backups, but I normally limit them to data/documents I care the most. 
Reinstalling everything, adjusting all the minor things according to my taste, reinstalling all the applications and re-do the various settings is really something I would like to avoid.
I am happy to wait for the SMART Data & Self-tests to finish. I will let it run overnight if it's needed.

By the way, thanks you so much for assisting me!

---

### Post by oldfred on 2021-12-03
If you have backed up a list of installed apps, then it is easy to reinstall them.
My rsync includes an export of the installed apps into /home.
And all user settings are in /home. I do edit a few files in /etc for system wide settings, but  copy those into /home or have scripted an update to them.

---

### Post by Matteo_Castagna on 2021-12-04
I ended up wasting time trying to solve the problem (with TestDisk I couldn't really find what was wrong) and then reinstalling ubuntu from scratch.
Backups are fine as I have all my docs back.
Is there anything (reasonably accessible) you can point me to in terms of setting up the backup covering apps and settings?
Shall I change this to [Solved] now?

---

### Post by oldfred on 2021-12-04
User settings should be in /home.
System wide settings are in /etc, but if new install best not to just restore it as system settings may change.  The few I change like grub, I just copy into /home.
If you have server apps those would be in their own sub directories in / and you have to back those up.

My rsync backup script file includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages 
My backup rsync script includes the get selections & new install script has the reinstall. 
The dpkg list is a very long text list of all applications and the dependencies. 
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
[https://kvz.io/restore-packages-using-dselectupgrade.html](https://kvz.io/restore-packages-using-dselectupgrade.html)

#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

Because I use LTS as main working install, but have additional / for test installs and each 6 month release, I have scripted most of the additional applications I want. With a test install, I may not want all of the same apps.

---

