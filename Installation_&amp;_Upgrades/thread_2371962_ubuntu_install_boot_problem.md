---
title: "ubuntu install boot problem"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by lidor08 on 2017-09-20
Hi everyone , i installed ubuntu 17.0 on ssd with windows 10 dual-boot , after a while i decide to downgrade to ubuntu 16.04 so i [COLOR=#333333][FONT=&quot]erase the partitioin of ubuntu 
and try to install ubuntu 16.04 on usb drive again but now when i trying to boot it's [/FONT][/COLOR][COLOR=#333333][FONT=&quot]stuck [/FONT][/COLOR][COLOR=#333333][FONT=&quot]on grub promat , how can i fix it?

[/FONT][/COLOR]

---

### Post by kc1di on 2017-09-20
Hello lidor08 and Welcome to Ubuntu Forums,

you can try boot-repair found[ here.]("https://help.ubuntu.com/community/Boot-Repair") It may solve the problem for you  pay close attention to the web address it gives you and post it here if it does not work.

---

### Post by lidor08 on 2017-09-21
I try to use boot-repair but it does not fix it , here is the file result [https://ufile.io/ftz0x](https://ufile.io/ftz0x)

---

### Post by lidor08 on 2017-09-21
result:
```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]



============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 32792 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sda1 ends after the last sector of /dev/sda


GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         264,192 1,953,523,711 1,953,259,520 Data partition (Windows/Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048    15,633,407    15,631,360   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/nvme0n1p1   C2BE-4C23                              vfat       SYSTEM_DRV
/dev/nvme0n1p3   40FEBEBCFEBEA994                       ntfs       Windows
/dev/nvme0n1p4   6288BF6388BF33FF                       ntfs       WINRE_DRV
/dev/sda2        0AD4CADAD4CAC763                       ntfs       LENOVO
/dev/sdb1        A0B2-43D1                              vfat       BOOT-REPAIR
/dev/zram0       22e5e609-4da0-4df6-88d1-551c6756c5a0   swap       
/dev/zram1       095cf343-e64d-4504-a639-a95369eb2ca7   swap       
/dev/zram2       0ee174fe-d521-490a-99b9-0adc723f2057   swap       
/dev/zram3       fe8b64fe-a82c-47e0-8757-f02fc216fd9d   swap       
/dev/zram4       1166b11d-9c83-456e-b1d7-07c8755b416b   swap       
/dev/zram5       b9fd2829-80cc-4508-85cd-e46dfeedb087   swap       
/dev/zram6       6106eeec-4665-4a2d-99ad-6a52e2987944   swap       
/dev/zram7       4575d25e-0c1f-4ffe-b7d2-60ea5a880c8e   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Sep 21 16:28 ata-WDC_WD10SPCX-24HWST1_WD-WX21A179LCR4 -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 21 16:27 ata-WDC_WD10SPCX-24HWST1_WD-WX21A179LCR4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 21 16:28 ata-WDC_WD10SPCX-24HWST1_WD-WX21A179LCR4-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Sep 21 16:28 usb-SanDisk_Cruzer_Orbit_4C530005920210119093-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Sep 21 16:27 usb-SanDisk_Cruzer_Orbit_4C530005920210119093-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Sep 21 16:28 wwn-0x50014ee6b20e56d4 -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 21 16:27 wwn-0x50014ee6b20e56d4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 21 16:28 wwn-0x50014ee6b20e56d4-part2 -> ../../sda2


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/nvme0n1p3   /media/lubuntu/Windows   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/lubuntu/LENOVO    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sdb1/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


============================== sdb1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/2078/mounts) leaked on lvs invocation. Parent PID 17865: bash
File descriptor 63 (pipe:[18339]) leaked on lvs invocation. Parent PID 17865: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-09-21__16h27 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2078/mounts) leaked on lvs invocation. Parent PID 4691: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




=================== os-prober:
/dev/nvme0n1p1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/nvme0n1p1: LABEL="SYSTEM_DRV" UUID="C2BE-4C23" TYPE="vfat"
/dev/nvme0n1p3: LABEL="Windows" UUID="40FEBEBCFEBEA994" TYPE="ntfs"
/dev/nvme0n1p4: LABEL="WINRE_DRV" UUID="6288BF6388BF33FF" TYPE="ntfs"
/dev/sda2: LABEL="LENOVO" UUID="0AD4CADAD4CAC763" TYPE="ntfs"
/dev/sdb1: LABEL="BOOT-REPAIR" UUID="A0B2-43D1" TYPE="vfat"
/dev/zram0: UUID="22e5e609-4da0-4df6-88d1-551c6756c5a0" TYPE="swap"
/dev/zram1: UUID="095cf343-e64d-4504-a639-a95369eb2ca7" TYPE="swap"
/dev/zram2: UUID="0ee174fe-d521-490a-99b9-0adc723f2057" TYPE="swap"
/dev/zram3: UUID="fe8b64fe-a82c-47e0-8757-f02fc216fd9d" TYPE="swap"
/dev/zram4: UUID="1166b11d-9c83-456e-b1d7-07c8755b416b" TYPE="swap"
/dev/zram5: UUID="b9fd2829-80cc-4508-85cd-e46dfeedb087" TYPE="swap"
/dev/zram6: UUID="6106eeec-4665-4a2d-99ad-6a52e2987944" TYPE="swap"
/dev/zram7: UUID="4575d25e-0c1f-4ffe-b7d2-60ea5a880c8e" TYPE="swap"




1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


Windows not detected by os-prober on nvme0n1p3.


WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util sfdisk doesn't support GPT. Use GNU Parted.




WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.




WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.




WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== No kernel in /mnt/boot-sav/nvme0n1p1/boot:
BOOT.SDI




Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi


efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,0000,0002,2003,2001,2002
Boot0000* Windows Boot Manager    HD(1,800,82000,ffed039e-4a1e-4a9b-9857-b46ae2d2a326)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* ubuntu    HD(1,800,82000,ffed039e-4a1e-4a9b-9857-b46ae2d2a326)File(EFIubuntushimx64.efi)
Boot0002* Linpus lite    HD(1,800,ee8400,0011a853)File(EFIBootgrubx64.efi)RC
Boot0003* EFI Network 0 for IPv4 (54-E1-AD-43-5E-9E)     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(54e1ad435e9e,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0005* EFI Network 0 for IPv6 (54-E1-AD-43-5E-9E)     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(54e1ad435e9e,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0006* Windows Boot Manager    HD(2,96800,32000,3a9ac3fd-daaf-46db-bec7-7cbeb802e3ad)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...2................
Boot0007* Windows Boot Manager    HD(1,800,82000,ffed039e-4a1e-4a9b-9857-b46ae2d2a326)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...&................
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])




=================== PARTITIONS & DISKS:
nvme0n1p1    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/nvme0n1p1.
nvme0n1p3    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/nvme0n1p3.
nvme0n1p4    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p4.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.


nvme0n1    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes




=================== parted -l:


Model: ATA WDC WD10SPCX-24H (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata




Model: SanDisk Cruzer Orbit (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  8004MB  8003MB  primary  fat32        boot, lba






                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label


Model: Unknown (unknown)
Disk /dev/nvme0n1: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                          Flags
1      1049kB  274MB   273MB   fat32        EFI system partition          boot
2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
3      290MB   67.4GB  67.1GB  ntfs         Basic data partition          msftdata
4      127GB   128GB   1049MB  ntfs         Basic data partition          hidden, diag


=================== parted -lm:


BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10SPCX-24H;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:1000GB:1000GB:ntfs:Basic data partition:msftdata;


BYT;
/dev/sdb:8004MB:scsi:512:512:msdos:SanDisk Cruzer Orbit;
1:1049kB:8004MB:8003MB:fat32::boot, lba;




                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label


BYT;
/dev/nvme0n1:128GB:unknown:512:512:gpt:Unknown;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:67.4GB:67.1GB:ntfs:Basic data partition:msftdata;
4:127GB:128GB:1049MB:ntfs:Basic data partition:hidden, diag;




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type vfat (rw)
/dev/nvme0n1p3 on /mnt/boot-sav/nvme0n1p3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 23 4c be c2 4e  4f 20 4e 41 4d 45 20 20  |..)#L..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/nvme0n1p3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 27 d1 07 00 00 00 00  |.........'......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  94 a9 be fe bc be fe 40  |...............@|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/nvme0n1p4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 80 c8 0e  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 1f 00 00 00 00 00  |.........?......|
00000030  55 4d 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |UM..............|
00000040  f6 00 00 00 01 00 00 00  ff 33 bf 88 63 bf 88 62  |.........3..c..b|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 6c 74 00 00 00 00  |........._lt....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  63 c7 ca d4 da ca d4 0a  |........c.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.8G  6.3M  7.8G   1% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  1.2M  1.6G   1% /run
/dev/sdb1      vfat       7.5G  614M  6.9G   9% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.8G  8.0K  7.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.8G     0  7.8G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/nvme0n1p1 vfat       256M   37M  220M  15% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3 fuseblk     63G   50G   13G  80% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4 fuseblk   1000M  389M  612M  39% /mnt/boot-sav/nvme0n1p4
/dev/sda2      fuseblk    932G  4.0G  928G   1% /mnt/boot-sav/sda2


=================== fdisk -l:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x899e01b4


Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0011a853


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15633407     7815680    c  W95 FAT32 (LBA)




No OS or WinEFI system


=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems  fix-windows-boot




Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




fsck -fyM /dev/nvme0n1p1
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
/dev/nvme0n1p1: 277 files, 9872/65536 clusters


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




fsck -fyM /dev/nvme0n1p3
fsck from util-linux 2.20.1


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




fsck -fyM /dev/nvme0n1p4
fsck from util-linux 2.20.1
fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for /dev/nvme0n1p4


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




fsck -fyM /dev/sda2
fsck from util-linux 2.20.1
Quantity of real Windows: 1


Boot successfully repaired.


You can now reboot your computer.



```

---

### Post by oldfred on 2017-09-21
Please use code tags. It is the # icon in Forum's advanced editor.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 

What brand/model system?
Many with SSD have had to update both UEFI and SSD's firmware.
and many with Intel SRT which is seen as RAID have to change to AHCI in UEFI settings. Best to add Windows driver first or immediately boot Windows in recovery mode to add AHCI driver.

Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208) 

 Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 
           ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)

---

