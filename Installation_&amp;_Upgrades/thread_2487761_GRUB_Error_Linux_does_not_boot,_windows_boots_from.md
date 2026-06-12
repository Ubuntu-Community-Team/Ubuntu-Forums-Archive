---
title: "GRUB Error Linux does not boot, windows boots from boot menu"
date: 2023-06-14
forum: Installation &amp; Upgrades
---

### Post by et0rnatus on 2023-06-14
Hello. I need some help please.
One of my computers has Windows and a Linux partition.
We can't boot either when powering on computer.
Windows boots fine from bios boot menu.
Linux does not boot at all.
sda should be the hard drive (sdb a usb, sdc an external drive)

```

boot-repair-4ppa203                                              [20230614_1652]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdc.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/HP/diw.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/HP/BiosUpdate/CryptRSA.efi 
                       /efi/HP/BiosUpdate/CryptRSA32.efi 
                       /efi/HP/BiosUpdate/HpBiosMgmt.efi 
                       /efi/HP/BiosUpdate/HpBiosMgmt32.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate.efi 
                       /efi/HP/BiosUpdate/HpBiosUpdate32.efi 
                       /efi/HP/SystemDiags/CryptRSA.efi 
                       /efi/HP/SystemDiags/CryptRSA32.efi 
                       /efi/HP/SystemDiags/HpSysDiags.efi 
                       /efi/HP/SystemDiags/HpSysDiags32.efi 
                       /efi/HP/SystemDiags/SystemDiags.efi 
                       /efi/HP/SystemDiags/SystemDiags32.efi 
                       /efi/HP/SystemDiags/diw.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


nvme0n1p2: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe


nvme0n1p4: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files:        


sdc2: __________________________________________________________________________


    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg




================================ 1 OS detected =================================


OS#1:   Windows 8 or 10 on nvme0n1p3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: NVIDIA Corporation from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: P61 v02.75 from HP
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled.
BootNext: 0010
BootCurrent: 0014
Timeout: 0 seconds
BootOrder: 0015,0013,000E,000C,000B,000D,000F,0009,0010,0011,0000,0001,0002,0003,0004,0005,0006,0007,0008,0012,000A
Boot0000  Startup Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)....ISPH
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0003  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0007  Boot Menu    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0008  HP Recovery    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0009* ST2000DM008-2FR102     PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)N.....YM....R,Y..p..ISPH
Boot000A* PNY USB 2.0 FD 070194AD9C273836    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)N.....YM....R,Y.....ISPH
Boot000B* IPV6 Network - Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(80e82ce31c62,1)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y..`..ISPH
Boot000C* IPV4 Network - Intel(R) I210 Gigabit  Network Connection    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(80e82ce31c62,1)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y..X..ISPH
Boot000D* IPV6 Network - Intel(R) Ethernet Connection (2) I219-LM    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(80e82ce31c61,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y..h..ISPH
Boot000E* IPV4 Network - Intel(R) Ethernet Connection (2) I219-LM    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(80e82ce31c61,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y..P..ISPH
Boot000F  CD/DVD Drives    PciRoot(0x0)/Pci(0x11,0x5)/Sata(4,0,0)...(..ISPH
Boot0010  USB Drives    PciRoot(0x0)/Pci(0x14,0x0)/USB(10,6)......ISPH
Boot0011  New Mass Storage    PciRoot(0x0)/Pci(0x11,0x5)/Sata(4,0,0)...8..ISPH
Boot0012  Network Boot    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0013* Windows Boot Manager    HD(1,GPT,20c35ec8-b1b3-4b77-a76c-d16de20c556c,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.....................H..ISPH
Boot0014* \efi\boot\bootx64.efi    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/CDROM(1,0x3c4,0x4d00)/File(\efi\boot\bootx64.efi)....ISPH
Boot0015* ubuntu    HD(1,GPT,20c35ec8-b1b3-4b77-a76c-d16de20c556c,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi).@..ISPH


64349b3622c65f495a99dbf6102496e3   nvme0n1p1/Boot/bootx64.efi
a5e9b71b5ba86166bee504e1b254b7cf   nvme0n1p1/Boot/fbx64.efi
f75c300397e73f3fc7bfe46d49819bb2   nvme0n1p1/Boot/mmx64.efi
a6d978d78b2e4c47612cc40b861a58a7   nvme0n1p1/HP/diw.efi
78dce18613524e5ea5d6059f51b7178f   nvme0n1p1/ubuntu/grubx64.efi
f75c300397e73f3fc7bfe46d49819bb2   nvme0n1p1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p1/ubuntu/shimx64.efi
6488d391f74263c9da3c3d47dffa6212   nvme0n1p1/HP/BiosUpdate/CryptRSA.efi
1b8c0684ede8539ccc205cf7a750eca3   nvme0n1p1/HP/BiosUpdate/CryptRSA32.efi
8f275519c9bf3659b3b6fa7878190cb3   nvme0n1p1/HP/BiosUpdate/HpBiosMgmt.efi
a6b6b875d66a62f03caa629bf50848bf   nvme0n1p1/HP/BiosUpdate/HpBiosMgmt32.efi
1df59d6a65a1b5ee2494dc04c114562e   nvme0n1p1/HP/BiosUpdate/HpBiosUpdate.efi
0ff4237254ce3cf1a827412e0bb68e56   nvme0n1p1/HP/BiosUpdate/HpBiosUpdate32.efi
6488d391f74263c9da3c3d47dffa6212   nvme0n1p1/HP/SystemDiags/CryptRSA.efi
1b8c0684ede8539ccc205cf7a750eca3   nvme0n1p1/HP/SystemDiags/CryptRSA32.efi
8a5fa0c97b92fe54ff91d7e441180568   nvme0n1p1/HP/SystemDiags/HpSysDiags.efi
17573676ea768e9207779eb4d4cd3167   nvme0n1p1/HP/SystemDiags/HpSysDiags32.efi
6a7e6cd728d57814d2163b28a95c210d   nvme0n1p1/HP/SystemDiags/SystemDiags.efi
730ee9b336aaea0e5f474e0915c5e6b0   nvme0n1p1/HP/SystemDiags/SystemDiags32.efi
a6d978d78b2e4c47612cc40b861a58a7   nvme0n1p1/HP/SystemDiags/diw.efi
d1f6c29ed98f2a8102fd87c118371e0b   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
85b10a5efd8419adc616cb2a5a70db30   nvme0n1p1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios


Partitions info (2/3): _________________________________________________________


nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 5438BCB9-0F35-4390-94C4-2EDA612647C2
              Start       End   Sectors   Size Type
nvme0n1p1      2048    534527    532480   260M EFI System
nvme0n1p2    534528    567295     32768    16M Microsoft reserved
nvme0n1p3    567296 498606079 498038784 237.5G Microsoft basic data
nvme0n1p4 498606080 500107263   1501184   733M Windows recovery environment
Disk sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: D00480DC-FC4B-4996-A1B6-92F37CED0E05
          Start        End    Sectors  Size Type
sda1         34      32767      32734   16M Microsoft reserved
sda2      32768  761300991  761268224  363G Microsoft basic data
sda3  761300992 3907029134 3145728143  1.5T Linux filesystem
Disk sdb: 28.9 GiB, 31029460992 bytes, 60604416 sectors
Disk identifier: 0x2c534026
      Boot Start     End Sectors  Size Id Type
sdb1  *        0 1802239 1802240  880M  0 Empty
sdb2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk zram0: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram1: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram2: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram3: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram4: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram5: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram6: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram7: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram8: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram9: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram10: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram11: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram12: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram13: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram14: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk zram15: 7.9 GiB, 8437571584 bytes, 2059954 sectors
Disk sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 5837763F-E45F-467B-A7EC-5DBD24702F05
       Start        End    Sectors  Size Type
sdc1      40     409639     409600  200M EFI System
sdc2  411648 3907028991 3906617344  1.8T Microsoft basic data


parted -lm (filtered): _________________________________________________________


sda:2000GB:scsi:512:4096:gpt:ATA ST2000DM008-2FR1:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:390GB:390GB:ntfs:Basic data partition:msftdata;
3:390GB:2000GB:1611GB:::;
sdb:31.0GB:scsi:512:512:msdos:PNY USB 2.0 FD:;
2:494kB:3017kB:2523kB:::esp;
nvme0n1:256GB:nvme:512:512:gpt:SK hynix PC711 HFS256GDE9X073N:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:255GB:255GB:ntfs:Basic data partition:msftdata;
4:255GB:256GB:769MB:ntfs:Basic data partition:hidden, diag;


Free space >10MiB: ______________________________________________________________


sdb: 2.88MiB:29592MiB:29589MiB


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                                   
&#9500;&#9472;sda1                                                    6f7f53cd-29a2-4292-8a04-5431cadc8884                        Microsoft reserved partition
&#9500;&#9472;sda2      ntfs     7612457812453DFD                     24edfabc-d51a-4d5b-a3aa-1a4095f151f7 DATADRIVE1             Basic data partition
&#9492;&#9472;sda3                                                    69e7b6ba-4dbf-ee4e-8290-d6558d42e8e3                        
sdb         iso9660  2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sdb1      iso9660  2020-06-13-00-42-55-00               2c534026-01                          Boot-Repair-Disk 64bit 
&#9492;&#9472;sdb2      vfat     D055-8513                            2c534026-02                          Boot-Repair-Disk 64bit 
sdc                                                                                                                   
&#9500;&#9472;sdc1      vfat     67E3-17ED                            c1f95db8-ccae-4388-96f7-92ab1335b518 EFI                    EFI System Partition
&#9492;&#9472;sdc2      exfat    5FD2-5796                            56089a7e-30a6-4489-bac9-412a0dcde1e9 Secuencia              
nvme0n1                                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     DC85-6D8F                            20c35ec8-b1b3-4b77-a76c-d16de20c556c SYSTEM                 EFI system partition
&#9500;&#9472;nvme0n1p2                                               9e0a469f-a08d-4a57-bdb3-0bec7736bd96                        Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     1C4609BB46099724                     c0522d5d-ed6a-438e-818a-9e93d5f42aa3 Windows                Basic data partition
&#9492;&#9472;nvme0n1p4 ntfs     3C6E1CE06E1C952C                     5b4efb9e-81b8-4045-99b8-bb88520575f4 Windows RE Tools       Basic data partition


Mount points (filtered): _______________________________________________________


                Avail Use% Mounted on
/dev/nvme0n1p1 136.1M  47% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3  19.2G  92% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4 114.8M  84% /mnt/boot-sav/nvme0n1p4
/dev/sda2      219.3G  40% /mnt/boot-sav/sda2
/dev/sdb            0 100% /cdrom


Mount options (filtered): ______________________________________________________




=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================


search.fs_uuid 43a4fd8d-f8eb-4acc-9a07-6de56fa45a80 root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sdb/boot/grub/grub.cfg (filtered) =======================


Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)


==================== sdb: Location of files loaded by Grub =====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


======================== Unknown MBRs/Boot Sectors/etc =========================




/dev/nvme0n1p1: unknown GPT attributes
8000000000000000


/dev/nvme0n1p2: unknown GPT attributes
8000000000000000


/dev/nvme0n1p4: unknown GPT attributes
8000000000000001
Unknown BootLoader on sdc1


Unknown BootLoader on sdc2


Unknown BootLoader on sdb








Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  win-legacy-basic-fix
```

---

### Post by ajgreeny on 2023-06-14
Unfortunately I am unable to help decipher your script output as it is beyond my skills, but should you need to use the boot-info script in future please just copy and paste the link you are shown and do not post the full output as you did originally.

You will see, however, that I have added code tags to your post in order to show that long text output exactly as shown in terminal, including all the tabulation and indents, all of which disappear in a simple copy/paste of plain text.

See my signature below for how to add Code Tags.

---

### Post by oldfred on 2023-06-14
I am not seeing any Linux partition. Partition table says sda3, but it has no UUID and looks like it was erased/formatted?

And the 3 line grub.cfg in the ESP refers to an UUID that does not exist. Was UUID of sda3?

HP also requires you to change boot order in UEFI settings.

---

### Post by et0rnatus on 2023-06-26
Thank you. I have no idea what happened. 
I managed to recover my most important files and did a new install of Ubuntu 22.04.

---

