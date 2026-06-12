---
title: "Ubuntu is not booting after restore"
date: 2022-07-05
forum: Installation &amp; Upgrades
---

### Post by fallen-witcher84 on 2022-07-05
My harddrive messed up today and I backed up some time ago the whole drive with the disks utility.
I tried today the restoring but the system don't boot after finishing the process. There is only the message that there is no bootable device and I should insert one and reboot.

Is it possible that the grub is missing?
There was a message before the restoring start that the image is 14,7 mb smaller as the target device. Maybe its important. It's not my first restoring. The first restoring was because I switched from HDD to SSD. It was the same procedure but it looks like the is something wrong this time.

I remember one time there was a a similar problem. There was something wrong with uuid.

---

### Post by fallen-witcher84 on 2022-07-05
I tried my luck with boot-repair but it hasn't worked
```
boot-repair-4ppa200                                              [20220705_1542]


============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


sda: ___________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img




================================ 0 OS detected =================================




================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Atom Processor Z36xxx/Z37xxx Series Graphics & Display from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: P1.30(5.6) from American Megatrends Inc.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________




Partitions info (1/3): _________________________________________________________




Partitions info (2/3): _________________________________________________________




Partitions info (3/3): _________________________________________________________




fdisk -l (filtered): ___________________________________________________________


Disk sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk sdb: 28.65 GiB, 30765219840 bytes, 60088320 sectors
Disk identifier: 0x286d0156
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 60088319 60086272 28.7G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:240GB:scsi:512:512:loop:ATA CT240BX500SSD1:;
1:0.00B:240GB:240GB:ext4::;
sdb:30.8GB:scsi:512:512:msdos:SanDisk' Cruzer Fit:;
1:1049kB:30.8GB:30.8GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda    ext4     e0ae8182-d911-4db8-bd04-7458590da666                                                  
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     588F-8703                            286d0156-01                          UBUNTU 22_0 


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sdb1               25.2G  12% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sdb1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


====================== sda/boot/grub/grub.cfg (filtered) =======================


Ubuntu   e0ae8182-d911-4db8-bd04-7458590da666
Ubuntu, mit Linux 5.4.0-65-generic   e0ae8182-d911-4db8-bd04-7458590da666
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


=========================== sda/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e0ae8182-d911-4db8-bd04-7458590da666 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
LABEL=ExterneHDD1 /mnt/ExterneHDD1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=ExterneHDD2 /mnt/ExterneHDD2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=ExterneHDD3 /mnt/ExterneHDD3 auto nosuid,nodev,nofail,x-gvfs-show 0 0


======================= sda/etc/default/grub (filtered) ========================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
GRUB_CMDLINE_LINUX=""


==================== sda: Location of files loaded by Grub =====================


           GiB - GB             File                                 Fragment(s)
   4,726623535 = 5,075173376    boot/grub/grub.cfg                             2
  11,122661591 = 11,942866944   boot/grub/i386-pc/core.img                     1
 162,143695831 = 174,100467712  boot/vmlinuz                                   1
 162,143695831 = 174,100467712  boot/vmlinuz-5.4.0-65-generic                  1
 162,143695831 = 174,100467712  boot/vmlinuz.old                               1
 189,314186096 = 203,274559488  boot/initrd.img                                1
 189,314186096 = 203,274559488  boot/initrd.img-5.4.0-65-generic               1
 189,314186096 = 203,274559488  boot/initrd.img.old                            1


====================== sda: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Sep  8  2020 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Sep  8  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jul 17  2018 30_os-prober
-rwxr-xr-x 1 root root  1424 Sep  8  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 17  2018 40_custom
-rwxr-xr-x 1 root root   216 Jul 17  2018 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by SeijiSensei on 2022-07-05
That shows a boot sector on /dev/sdb. That's usually the second hard drive identified at boot. Go into your system's BIOS setup and see if you can change the order of the drives. Depending on the BIOS firmware you could have many options to try. Try turning off the other drive (what Linux sees as /dev/sda), reversing the order of boot, or other tricks. You might also be able to hit an Fn key to bring up boot options. If so, choose to boot from the older drive.

---

### Post by fallen-witcher84 on 2022-07-05
I managed that the drive boots up.
Can someone take a look at the repair log
```

rebootboot-repair-4ppa200                                              [20220705_1849]


============================= Boot Repair Summary ==============================










sda may have broken partition table.
sda may have broken partition table.
sda (sda) has unknown type. Bitte melden Sie diese Nachricht an boot.repair@gmail.com


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sdb, and make it boot on sdb2.
Additional repair will be performed: unhide-bootmenu-10s






============================== Restore MBR of sdb ==============================


dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sdb
parted /dev/sdb set 2 boot on
Informationen: Möglicherweise müssen Sie /etc/fstab anpassen.




                                                                          
parted /dev/sdb set 1 boot off
Informationen: Möglicherweise müssen Sie /etc/fstab anpassen.




                                                                          
SET@_label0.set_text('''Startmenü anzeigen. Das kann einige Minuten dauern …''')


Bootsektor wurde erfolgreich repariert.


Sie können Ihren Rechner nun neu starten.




============================ Boot Info After Repair ============================


 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grub.efi 
                       /boot/grub/i386-pc/core.img


sdb2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda: ___________________________________________________________________________


    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 17710424 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 20.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img




================================ 1 OS detected =================================


OS#1:   Das aktuell benutzte Betriebssystem - Ubuntu 20.04.3 LTS CurrentSession on sda


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Atom Processor Z36xxx/Z37xxx Series Graphics & Display from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-65-generic root=UUID=e0ae8182-d911-4db8-bd04-7458590da666 ro quiet splash intel_idle.max_cstate=1 vt.handoff=7
df -Th / : /dev/sda       ext4  220G     68G  145G   32% /


===================================== UEFI =====================================


BIOS/UEFI firmware: P1.30 from American Megatrends Inc.
The firmware seems EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).




31461cb628fb15ca0acc5fc545f664ba   sdb1/BOOT/grub.efi
31461cb628fb15ca0acc5fc545f664ba   sdb1/BOOT/BOOTIA32.efi
83e48a4cbff23773a648f612d4000b32   sdb1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sdb	: notGPT,	no-BIOSboot,	has---ESP, 	usb-disk,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sdb1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


sdb1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sdb1	: not--sepboot,	no-kernel,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb


fdisk -l (filtered): ___________________________________________________________


Disk sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk identifier: 0x00000000
Disk sdb: 28.67 GiB, 30765219840 bytes, 60088320 sectors
Disk identifier: 0x6b953a68
      Boot Start    End Sectors  Size Id Type
sdb1        6144  73728   67585   33M  b W95 FAT32
sdb2  *    75776 618496  542721  265M  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:240GB:scsi:512:512:msdos:ATA CT240BX500SSD1:;
sdb:30.8GB:scsi:512:512:msdos:SanDisk' Cruzer Fit:;
1:3146kB:37.7MB:34.6MB:fat32::boot;
2:38.8MB:317MB:278MB:fat32::lba;


Free space >10MiB: ______________________________________________________________


sda: 0.00MiB:228937MiB:228937MiB
sdb: 302MiB:29340MiB:29038MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL    PARTLABEL
sda    ext4     e0ae8182-d911-4db8-bd04-7458590da666                                               
sdb                                                                                                
&#9500;&#9472;sdb1 vfat     B5B2-9BB7                            6b953a68-01                          SG2DBOOT 
&#9492;&#9472;sdb2 vfat     B575-ABAB                            6b953a68-02                          SG2DISOS 


Mount points (filtered): _______________________________________________________


             Avail Use% Mounted on
/dev/sda    144.5G  31% /
/dev/sdb1    15.7M  52% /media/htpc/SG2DBOOT
/dev/sdb2   264.4M   0% /media/htpc/SG2DISOS


Mount options (filtered): ______________________________________________________


/dev/sda    ext4            rw,relatime,errors=remount-ro
/dev/sdb1   vfat            rw,nosuid,nodev,relatime,uid=1000,gid=100,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
/dev/sdb2   vfat            rw,nosuid,nodev,relatime,uid=1000,gid=100,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro


====================== sdb1/boot/grub/grub.cfg (filtered) ======================




==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/grub/i386-pc/core.img                     1


====================== sda/boot/grub/grub.cfg (filtered) =======================


Ubuntu   e0ae8182-d911-4db8-bd04-7458590da666
Ubuntu, mit Linux 5.4.0-65-generic   e0ae8182-d911-4db8-bd04-7458590da666
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


=========================== sda/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=e0ae8182-d911-4db8-bd04-7458590da666 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
LABEL=ExterneHDD1 /mnt/ExterneHDD1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=ExterneHDD2 /mnt/ExterneHDD2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=ExterneHDD3 /mnt/ExterneHDD3 auto nosuid,nodev,nofail,x-gvfs-show 0 0


======================= sda/etc/default/grub (filtered) ========================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
GRUB_CMDLINE_LINUX=""


==================== sda: Location of files loaded by Grub =====================


           GiB - GB             File                                 Fragment(s)
   7.973030090 = 8.560975872    boot/grub/grub.cfg                             2
   8.445011139 = 9.067761664    boot/grub/i386-pc/core.img                     1
 162.143695831 = 174.100467712  boot/vmlinuz                                   1
 162.143695831 = 174.100467712  boot/vmlinuz-5.4.0-65-generic                  1
 162.143695831 = 174.100467712  boot/vmlinuz.old                               1
 189.314186096 = 203.274559488  boot/initrd.img                                1
 189.314186096 = 203.274559488  boot/initrd.img-5.4.0-65-generic               1
 189.314186096 = 203.274559488  boot/initrd.img.old                            1


====================== sda: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18151 Aug 12  2021 10_linux
-rwxr-xr-x 1 root root 42359 Sep  8  2020 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Sep  8  2020 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jul 17  2018 30_os-prober
-rwxr-xr-x 1 root root  1424 Sep  8  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 17  2018 40_custom
-rwxr-xr-x 1 root root   216 Jul 17  2018 41_custom

```

---

### Post by yancek on 2022-07-06
> sda may have broken partition table.

That looks like a very serious problem except for the word 'may'.  Your boot repair output doesn't seem to show any Grub code in the MBR for sda.  There is no EFI partition on that drive so you have a Legacy install rather than EFI.  Did you just back up and restore the Ubuntu partition rather than the entire drive?   You need to boot the USB in Legacy mode and reinstall Grub on sda if you haven't done that and set  the BIOS firmware to boot in Legacy mode on sda..

---

