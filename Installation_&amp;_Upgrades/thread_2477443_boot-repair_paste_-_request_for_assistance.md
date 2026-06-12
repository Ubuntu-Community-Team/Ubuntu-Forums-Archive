---
title: "boot-repair paste - request for assistance"
date: 2022-07-25
forum: Installation &amp; Upgrades
---

### Post by djmills32 on 2022-07-25
I have a laptop with an internal drive and itt's boot config was messed up by installing Ubuntu on an external SSD.

I needed to repair grub for both the internal and external Ubuntu's. On my 3rd attempt, the internal repair succeeded and I can now boot that again. But the external one refuses to repair. 

Please advise how to get it to work.

The paste from boot-repair is:
```
boot-repair-4ppa200                                              [20220725_0911]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

nvme0n1p3: _____________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/BOOT/grub.cfg /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.4 LTS on mapper/my_encrypted_volume

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP106M [GeForce GTX 1060 Mobile] UHD Graphics 630 (Mobile) from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.1 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: FX505GM.301 from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled but mokutil says: SecureBoot enabled - Please report this message to boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0001,0002,0003,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu	HD(1,GPT,1411f6da-b989-4099-88df-c6e2c25d36a6,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* ubuntu	HD(1,GPT,e1529f6a-75a1-40e9-974d-7ad55f5d9178,0xffff,0xefd95)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0003* UEFI: VerbatimSTORE N GO PMAP, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x761629,0x800,0xe6d800)..BO

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/BOOT/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   nvme0n1p1/BOOT/fbx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   nvme0n1p1/BOOT/grubx64.efi
469e608783843a701d172242f016c79c   nvme0n1p1/BOOT/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   nvme0n1p1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/BOOT/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/BOOT/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda1/BOOT/fbx64.efi
07fdcd25fda5090760b0afab83806aba   sda1/BOOT/grubx64.efi
469e608783843a701d172242f016c79c   sda1/BOOT/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   sda1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sda	: is-GPT,	no-BIOSboot,	has---ESP, 	usb-disk,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	grubenv-ng,	noupdategrub,	not-far
sda1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	grubenv-ok,	noupdategrub,	not-far
mapper/my_encrypted_volume	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	no-grubenv,	update-grub,	not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
mapper/my_encrypted_volume	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme0n1p2	: is---sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda2	: is---sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
mapper/my_encrypted_volume	: not--sepboot,	no---boot,	fstab-has-goodBOOT,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: B5648A2F-54AB-4020-BF7F-A947ED2D0173
            Start       End   Sectors   Size Type
nvme0n1p1    2048   1050623   1048576   512M EFI System
nvme0n1p2 1050624   2549759   1499136   732M Linux filesystem
nvme0n1p3 2549760 500117503 497567744 237.3G Linux filesystem
Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: FADED5DE-FB3C-4972-B69D-FDF0365ACB3C
        Start       End   Sectors   Size Type
sda1    65535   1047955    982421 479.7M EFI System
sda2  1048560   4062231   3013672   1.4G Linux filesystem
sda3  4063170 976733639 972670470 463.8G Linux filesystem
Disk sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: DA8CB4B8-9AD2-43A8-8AAD-12CDD9D1CC76
      Start        End    Sectors   Size Type
sdb1   2048 1953523711 1953521664 931.5G unknown
Disk sdc: 7.22 GiB, 7746879488 bytes, 15130624 sectors
Disk identifier: 0x00761629
      Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 15130623 15128576  7.2G  c W95 FAT32 (LBA)
Disk mapper/my_encrypted_volume: 463.81 GiB, 497990500352 bytes, 972637696 sectors

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:gpt:TOSHIBA TOSHIBA USB DRV:;
1:33.6MB:537MB:503MB:fat32:EFI System Partition:boot, esp;
2:537MB:2080MB:1543MB:ext4::;
3:2080MB:500GB:498GB:::;
sdb:1000GB:scsi:512:4096:gpt:ATA ST1000LX015-1U71:;
1:1049kB:1000GB:1000GB:::;
sdc:7747MB:scsi:512:512:msdos:Verbatim STORE N GO:;
1:1049kB:7747MB:7746MB:fat32::boot, lba;
mapper/my_encrypted_volume:498GB:dm:512:512:loop:Linux device-mapper (crypt):;
1:0.00B:498GB:498GB:ext4::;
nvme0n1:256GB:nvme:512:512:gpt:WDC PC SN520 SDAPNUW-256G-1002:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1305MB:768MB:ext4::;
3:1305MB:256GB:255GB:::;

Free space >10MiB: ______________________________________________________________

sda: 0.02MiB:32.0MiB:32.0MiB
sda: 476921MiB:476940MiB:19.3MiB

blkid (filtered): ______________________________________________________________

NAME                    FSTYPE      UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                                       
&#9500;&#9472;sda1                  vfat        EA27-1242                            e1529f6a-75a1-40e9-974d-7ad55f5d9178             EFI System Partition
&#9500;&#9472;sda2                  ext4        513ee88b-d105-4778-a080-b24fa0a34981 44ebdd69-543b-461d-af0a-ab38448455aa             
&#9492;&#9472;sda3                  crypto_LUKS 4d28703f-8cee-4b4b-a81a-74283aab20df 1179ab37-ee45-44e0-9f80-e643b5c3aa14             
  &#9492;&#9472;my_encrypted_volume ext4        dec6fd26-b838-4740-a61f-900b4339b7f2                                                  
sdb                                                                                                                       
&#9492;&#9472;sdb1                  crypto_LUKS aecd9fe9-ce9d-4adc-91fd-64cce3ad7f61 b270d8f1-f4a1-4fbe-9936-7f5dc8f742d0             
sdc                                                                                                                       
&#9492;&#9472;sdc1                  vfat        F4E8-6A19                            00761629-01                          UBUNTU 20_0 
nvme0n1                                                                                                                   
&#9500;&#9472;nvme0n1p1             vfat        E945-B668                            1411f6da-b989-4099-88df-c6e2c25d36a6             EFI System Partition
&#9500;&#9472;nvme0n1p2             ext4        cce01c2c-ca10-41ef-b808-5e938fb0d33c 56ff876b-05bd-4de1-97d3-5f3a1df5a4c1             
&#9492;&#9472;nvme0n1p3             crypto_LUKS 9d46b31e-6c39-4aa4-9a7d-2862903cc034 2c6f580e-8828-48ca-884e-970ed3e8c4f3             

Mount points (filtered): _______________________________________________________

                                 Avail Use% Mounted on
/dev/mapper/my_encrypted_volume 425.2G   2% /mnt/boot-sav/mapper/my_encrypted_volume
/dev/nvme0n1p1                  503.2M   2% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                  406.8M  35% /mnt/boot-sav/nvme0n1p2
/dev/sda1                       471.2M   2% /mnt/boot-sav/sda1
/dev/sda2                         1.1G  17% /mnt/boot-sav/sda2
/dev/sdc1                         4.6G  36% /cdrom

Mount options (filtered): ______________________________________________________

/dev/mapper/my_encrypted_volume ext4            rw,relatime,stripe=8191
/dev/nvme0n1p1                  vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2                  ext4            rw,relatime
/dev/sda1                       vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                       ext4            rw,relatime,stripe=8191
/dev/sdc1                       vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
my_encrypted_volume

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid cce01c2c-ca10-41ef-b808-5e938fb0d33c root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

====================== nvme0n1p2/grub/grub.cfg (filtered) ======================

Ubuntu   9115b007-5380-4f1c-8306-d2489b2dd3d0
Ubuntu, with Linux 5.15.0-41-generic   9115b007-5380-4f1c-8306-d2489b2dd3d0
Ubuntu, with Linux 5.4.0-42-generic   9115b007-5380-4f1c-8306-d2489b2dd3d0
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
   0.651386261 = 0.699420672    grub/grub.cfg                                  2
   0.948719025 = 1.018679296    vmlinuz                                        1
   0.948719025 = 1.018679296    vmlinuz-5.15.0-41-generic                      1
   0.644649506 = 0.692187136    vmlinuz-5.4.0-42-generic                       1
   0.644649506 = 0.692187136    vmlinuz.old                                    1
   1.196285248 = 1.284501504    initrd.img                                     3
   1.196285248 = 1.284501504    initrd.img-5.15.0-41-generic                   3
   1.079097748 = 1.158672384    initrd.img-5.4.0-42-generic                    4
   1.079097748 = 1.158672384    initrd.img.old                                 4

====================== sda1/efi/BOOT/grub.cfg (filtered) =======================

search.fs_uuid c046136a-f1c1-4b47-b022-1a0f40dc3c2c root hd0,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid c046136a-f1c1-4b47-b022-1a0f40dc3c2c root hd1,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

======================== sda2/grub/grub.cfg (filtered) =========================

Ubuntu   dec6fd26-b838-4740-a61f-900b4339b7f2
Ubuntu, with Linux 5.15.0-41-generic   dec6fd26-b838-4740-a61f-900b4339b7f2
Ubuntu, with Linux 5.4.0-42-generic   dec6fd26-b838-4740-a61f-900b4339b7f2
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   1.531124115 = 1.644032000    grub/grub.cfg                                  2
   1.080547333 = 1.160228864    vmlinuz                                        1
   1.080547333 = 1.160228864    vmlinuz-5.15.0-41-generic                      1
   0.648426056 = 0.696242176    vmlinuz-5.4.0-42-generic                       2
   0.648426056 = 0.696242176    vmlinuz.old                                    2
   1.530822754 = 1.643708416    initrd.img                                     6
   1.530822754 = 1.643708416    initrd.img-5.15.0-41-generic                   6
   1.264438629 = 1.357680640    initrd.img-5.4.0-42-generic                    3
   1.264438629 = 1.357680640    initrd.img.old                                 3

====================== sdc1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

========================= sdc1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdc1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdc1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

================================= User choice ==================================

Is there RAID on this computer? no



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
mapper/my_encrypted_volume,
using the following options:  sda2/boot sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Blockers in case of suggested repair: __________________________________________

 Encrypted partition detected. Please retry after mounting your encrypted partitions so that the tool can verify their contents. (sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume)

Confirmation request before suggested repair: __________________________________

You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume)
Are you sure you want to continue anyway?You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (sudo cryptsetup luksOpen /dev/nvme0n1p3 myvolume)
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.4 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !
```

---

### Post by oldfred on 2022-07-25
Always better to post link to Summary report, rather than post in line.

With LVM & encrypted installs, you typically have to mount LVM & decrypt install for os-prober or Boot-Repair to work.
With two LVM & encrypted installs it then requires both to be decripted.

Your ESP on sda1 /EFI/Boot/grub.cfg & /EFI/ubuntu/grub.cfg refer to UUID c046136a-f1c1-4b47-b022-1a0f40dc3c2c which does not exist.
You can edit manually to be UUID of your ext4 /boot partition on sda2 to 513ee88b-d105-4778-a080-b24fa0a34981.
Or you can use Boot-Repair's advanced mode, chose install on sda & sda as drive to install grub into.

You may want to change UEFI description of one or the other as both say "ubuntu"
You can just use efibootmgr to add entry & delete old entry.

---

