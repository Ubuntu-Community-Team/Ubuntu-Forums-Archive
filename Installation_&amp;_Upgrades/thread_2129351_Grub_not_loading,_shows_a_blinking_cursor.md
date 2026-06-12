---
title: "Grub not loading, shows a blinking cursor"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by skyuppecut on 2013-03-26
```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /BOOTSECT.BAK looks at 
                       sector 1873080528 of the same hard drive for core.img. 
                       core.img is at this location and looks in partition 72 
                       for fa1c08ed88ed08ec0fbdf0us.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........u.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 734504 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   976,923,072   976,923,010   7 NTFS / exFAT / HPFS
/dev/sda2         976,924,672 1,591,324,671   614,400,000   7 NTFS / exFAT / HPFS
/dev/sda3       1,591,324,672 1,867,804,671   276,480,000   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2055 MB, 2055207936 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4014078 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     4,014,077     4,014,015   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9C54244054241F8E                       ntfs       Win 7
/dev/sda2        A868B23368B2005C                       ntfs       Win 8
/dev/sda3        5830135E30134284                       ntfs       Stuff
/dev/sdb1        D888-5F62                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit boot=live config   quiet 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label 32bits session 
kernel /live/vmlinuz 
append initrd=/live/initrd.img boot=live config   quiet 
 
label ubnentry2 
menu label 64bits session 
kernel /live/vmlinuz2 
append initrd=/live/initrd2.img boot=live config   quiet 
 
label ubnentry3 
menu label 32bits session (failsafe) 
kernel /live/vmlinuz 
append initrd=/live/initrd.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal 
 
label ubnentry4 
menu label 64bits session (failsafe) 
kernel /live/vmlinuz2 
append initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal 
 
label ubnentry5 
menu label Memory test 
kernel /live/memtest 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5657]) leaked on lvscan invocation. Parent PID 8136: bash
File descriptor 8 (pipe:[5657]) leaked on lvscan invocation. Parent PID 8136: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-03-26__20h23 ===================
boot-repair version : 3.195~ppa11~lucid
boot-sav version : 3.195~ppa11~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version : 3.195~ppa11~lucid
File descriptor 7 (pipe:[5657]) leaked on lvs invocation. Parent PID 3470: /bin/sh
File descriptor 8 (pipe:[5657]) leaked on lvs invocation. Parent PID 3470: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 29nov2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/ubninit boot=live config   quiet BOOT_IMAGE=/ubnkern

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="Win 7" UUID="9C54244054241F8E" TYPE="ntfs"
/dev/sda2: LABEL="Win 8" UUID="A868B23368B2005C" TYPE="ntfs"
/dev/sda3: LABEL="Stuff" UUID="5830135E30134284" TYPE="ntfs"
/dev/sdb1: LABEL="PENDRIVE" UUID="D888-5F62" TYPE="vfat"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000LM010-9YH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  500GB  500GB  primary  ntfs         boot
2      500GB   815GB  315GB  primary  ntfs
3      815GB   956GB  142GB  primary  ntfs


Model: JetFlash TS2GJFV30 (scsi)
Disk /dev/sdb: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  2055MB  2055MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000LM010-9YH1;
1:32.3kB:500GB:500GB:ntfs::boot;
2:500GB:815GB:315GB:ntfs::;
3:815GB:956GB:142GB:ntfs::;

BYT;
/dev/sdb:2055MB:scsi:512:512:msdos:JetFlash TS2GJFV30;
1:32.3kB:2055MB:2055MB:fat32::boot;


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom v4l vga_arbiter video0 xconsole zero
ls /dev/md:

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.3G  7.2M  1.3G   1% /
tmpfs        tmpfs    1.3G     0  1.3G   0% /lib/init/rw
udev         tmpfs    1.3G  184K  1.3G   1% /dev
tmpfs        tmpfs    1.3G     0  1.3G   0% /dev/shm
/dev/sdb1     vfat    2.0G  351M  1.6G  18% /live/image
tmpfs        tmpfs    1.3G  7.2M  1.3G   1% /live/cow
tmpfs        tmpfs    1.3G     0  1.3G   0% /live
tmpfs        tmpfs    1.3G  8.0K  1.3G   1% /tmp
/dev/sda1  fuseblk    466G  102G  365G  22% /mnt/boot-sav/sda1
/dev/sda2  fuseblk    293G   78G  216G  27% /mnt/boot-sav/sda2
/dev/sda3  fuseblk    132G   67G   65G  51% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x75d2b7cc

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60811   488461505    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/sda2           60811       99056   307200000    7  HPFS/NTFS
/dev/sda3           99056      116266   138240000    7  HPFS/NTFS

Disk /dev/sdb: 2055 MB, 2055207936 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000524e7

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250     2007007+   b  W95 FAT32
Partition 1 has different physical/logical endings:
phys=(248, 254, 63) logical=(249, 220, 33)


No change has been performed on your computer. See you soon!

```
My bot report is above..
Please help me what to do..!!!!!
I am a beginner..I deleted the ubuntu partition..!! :(   and regret it now..!!

---

### Post by oldfred on 2013-03-26
Added code tags, Please use code tags on any long post of code or listings. 

With BootInfo you just need to post link to pastebin that Boot-Repair gives.

Boot Repair added syslinux boot loader which works just like Windows to MBR. The only info on grub you still have is /bootsec.bak.

Does it not boot Windows now?

---

### Post by skyuppecut on 2013-03-26
No..
it just shows a blinking cursor on startup.!
when i tried auto repair with win8 boot disk, nothing happened..!

---

### Post by oldfred on 2013-03-26
With Windows auto repair often does not work. You have to use the command line in the repair console.

 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

      
 Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)
f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

   oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

You have two Windows installs and Windows only boots from the one with the boot flag or the active partition.
Make sure boot flag is set for any partition you try to repair.

---

### Post by dsjstc on 2013-09-22
I just spent about two hours trying to diagnose identical symptoms on Saucy.  Ended up re/installing the grub-pc package, and everything immediately started working again.

---

