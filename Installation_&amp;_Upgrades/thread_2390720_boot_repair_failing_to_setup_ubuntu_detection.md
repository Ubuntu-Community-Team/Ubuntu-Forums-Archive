---
title: "boot repair failing to setup ubuntu detection"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by shome on 2018-05-01
PLZ IGNOER THIS POST. I REALIZED THAT MY HDD WAS NOT CONNECTED PROPERLY

i have cloned an ubuntu 14.04 partition to a partition in a separate drive. Then I have added a swap partition too. The drive doesnt have any other OS. Then I tried to use boot repair to get the grub working.

I booted from a pendrive which had boot repair. I got message about unmounting all partitions before boot repiar could work. I clicked ok and went ahead. Boot repair gave message that boot repair had successfully been done. When I rebooted from the hard drive i get message:

pxe-e7b: missing mftp server IP address
Pxe-mof: exiting intel boot agent
reboot and select proper boot device

My system: i7 with nvidia gtx titanx, 32 gb ram

the log from boot repair is as below:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       3518803967 sectors, but according to the info from 
                       fdisk, it has 4592545791 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1356262 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4000.8 GB, 4000787029504 bytes
256 heads, 63 sectors/track, 484501 cylinders, total 7814037167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         264,192 4,592,809,983 4,592,545,792 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15479597056 bytes
255 heads, 63 sectors/track, 1881 cylinders, total 30233588 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    30,232,575    30,230,528   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        9C88673E886715D4                       ntfs       Seagate Backup Plus Drive
/dev/sdb1        304C-5A5A                              vfat       
/dev/zram0       f9b18d85-48cd-47a0-9de3-eceaa2f8345e   swap       
/dev/zram1       203b8bae-7c22-42bd-8cb9-9b574786926d   swap       
/dev/zram2       4c17cc75-f450-4f39-9f9a-ce61edf2b563   swap       
/dev/zram3       5445aeb9-27f7-4bd7-b6c6-68951cf919cc   swap       
/dev/zram4       1e29c3e4-0c11-41f6-9013-f3b7d6ba10e2   swap       
/dev/zram5       0985d06b-0cc4-45b8-8a65-e2d191e7c09f   swap       
/dev/zram6       a7477522-7143-4dad-8632-b607c48d9ac0   swap       
/dev/zram7       49981972-4e2f-4d98-a0e7-7f441854a9fc   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  1 18:57 ata-ST4000LM024-2AN17V_WCK1KV6F -> ../../sda
lrwxrwxrwx 1 root root 10 May  1 18:57 ata-ST4000LM024-2AN17V_WCK1KV6F-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  1 19:01 ata-ST4000LM024-2AN17V_WCK1KV6F-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 May  1 18:57 usb-Kingston_DataTraveler_G3_001CC0EC34C9FC71471924B1-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  1 18:57 usb-Kingston_DataTraveler_G3_001CC0EC34C9FC71471924B1-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  1 18:57 wwn-0x5000c500ab374cb7 -> ../../sda
lrwxrwxrwx 1 root root 10 May  1 18:57 wwn-0x5000c500ab374cb7-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  1 19:01 wwn-0x5000c500ab374cb7-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
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
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^64bit session (failsafe)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2021/mounts) leaked on lvs invocation. Parent PID 8229: bash
File descriptor 63 (pipe:[26536]) leaked on lvs invocation. Parent PID 8229: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2018-05-01__18h57 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2021/mounts) leaked on lvs invocation. Parent PID 4593: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash -- BOOT_IMAGE=/casper/vmlinuz.efi
Unmount sda2 from /media/lubuntu/Seagate Backup Plus Drive to avoid space incompatibilities

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda2: LABEL="Seagate Backup Plus Drive" UUID="9C88673E886715D4" TYPE="ntfs"
/dev/sdb1: UUID="304C-5A5A" TYPE="vfat"
/dev/zram0: UUID="f9b18d85-48cd-47a0-9de3-eceaa2f8345e" TYPE="swap"
/dev/zram1: UUID="203b8bae-7c22-42bd-8cb9-9b574786926d" TYPE="swap"
/dev/zram2: UUID="4c17cc75-f450-4f39-9f9a-ce61edf2b563" TYPE="swap"
/dev/zram3: UUID="5445aeb9-27f7-4bd7-b6c6-68951cf919cc" TYPE="swap"
/dev/zram4: UUID="1e29c3e4-0c11-41f6-9013-f3b7d6ba10e2" TYPE="swap"
/dev/zram5: UUID="0985d06b-0cc4-45b8-8a65-e2d191e7c09f" TYPE="swap"
/dev/zram6: UUID="a7477522-7143-4dad-8632-b607c48d9ac0" TYPE="swap"
/dev/zram7: UUID="49981972-4e2f-4d98-a0e7-7f441854a9fc" TYPE="swap"


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.

sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes


=================== parted -l:

Model: Seagate BUP BL (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   4001GB  4001GB  ntfs         Basic data partition          msftdata


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  15.5GB  15.5GB  primary  fat32        boot



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


                                                                          
Error: /dev/zram4: unrecognised disk label


                                                                          
Error: /dev/zram5: unrecognised disk label


                                                                          
Error: /dev/zram6: unrecognised disk label


                                                                          
Error: /dev/zram7: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:4001GB:scsi:512:4096:gpt:Seagate BUP BL;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:4001GB:4001GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:Kingston DataTraveler G3;
1:1049kB:15.5GB:15.5GB:fat32::boot;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


                                                                          
Error: /dev/zram4: unrecognised disk label


                                                                          
Error: /dev/zram5: unrecognised disk label


                                                                          
Error: /dev/zram6: unrecognised disk label


                                                                          
Error: /dev/zram7: unrecognised disk label


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
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net watchdog watchdog0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff af bc d1 01 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d4 15 67 88 3e 67 88 9c  |..........g.>g..|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs   16G  5.2M   16G   1% /
udev           devtmpfs    16G   12K   16G   1% /dev
tmpfs          tmpfs      3.2G  1.1M  3.2G   1% /run
/dev/sdb1      vfat        15G  648M   14G   5% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs       16G  8.0K   16G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs       16G     0   16G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda2      fuseblk    3.7T  1.2T  2.6T  31% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 4000.8 GB, 4000787029504 bytes
256 heads, 63 sectors/track, 484501 cylinders, total 7814037167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa1f04d93

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.5 GB, 15479597056 bytes
255 heads, 63 sectors/track, 1881 cylinders, total 30233588 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da976

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30232575    15115264    b  W95 FAT32


No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda2
fsck from util-linux 2.20.1

Boot successfully repaired.

You can now reboot your computer.
```

---

