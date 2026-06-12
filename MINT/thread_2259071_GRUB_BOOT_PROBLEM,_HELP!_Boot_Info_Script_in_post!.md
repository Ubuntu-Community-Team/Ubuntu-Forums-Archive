---
title: "GRUB BOOT PROBLEM, HELP! Boot Info Script in post!"
date: 2015-01-01
forum: MINT
---

### Post by Joshua__Wimmer on 2015-01-01
Hello, I am fairly new with linux and such and the computer (desktop) I have was running Linux Mint 17 KDE. I have no idea as to what happened or why it happened but after turning the computer off overnight, then turning it on this morning it boots but ends up at the Grub> screen. I did alittle research on grub and all that and found Boot Info Script and followed the directions to get it and now I have no idea really what to do with the info , so i was hoping to post it here and see if i could get some help or interpretation , lol. ```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on boot 
    drive #1 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    71,096,319    71,094,272  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    71,096,319    71,094,272  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        255c095f-9661-4d7b-824c-d205ec0c785c   ext4       Hard Disk 2-36gb
/dev/sdb1        6318eedc-cc84-4380-ae5c-98d441086074   ext4       Memory Bank
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.224693298 = 23.863582720   boot/grub/i386-pc/core.img                     1

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 8 (/proc/2627/mounts) leaked on lvscan invocation. Parent PID 8282: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-01-01__21h12 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/2627/mounts) leaked on lvs invocation. Parent PID 4201: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 24avr2013, raring, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"
/dev/sda1: LABEL="Hard Disk 2-36gb" UUID="255c095f-9661-4d7b-824c-d205ec0c785c" TYPE="ext4"
/dev/sdb1: LABEL="Memory Bank" UUID="6318eedc-cc84-4380-ae5c-98d441086074" TYPE="ext4"

=================== No kernel in /mnt/boot-sav/sda1/boot:
grub


=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sdb1    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: IBM-ESXS MAP3367NP FN (scsi)
Disk /dev/sda: 36.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  36.4GB  36.4GB  primary  ext4         boot


Model: IBM-ESXS MAP3367NP FN (scsi)
Disk /dev/sdb: 36.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  36.4GB  36.4GB  primary  ext4         boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:36.4GB:scsi:512:512:msdos:IBM-ESXS MAP3367NP FN;
1:1049kB:36.4GB:36.4GB:ext4::boot;

BYT;
/dev/sdb:36.4GB:scsi:512:512:msdos:IBM-ESXS MAP3367NP FN;
1:1049kB:36.4GB:36.4GB:ext4::boot;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrom1 cdrw cdrw1 char console core cpu cpu_dma_latency disk dri dvd dvd1 dvdrw1 ecryptfs fb0 fd fd0 full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1009M   21M  989M   2% /
udev           devtmpfs   993M   12K  993M   1% /dev
tmpfs          tmpfs      202M  724K  201M   1% /run
/dev/sr0       iso9660    496M  496M     0 100% /cdrom
/dev/loop0     squashfs   431M  431M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1009M  8.0K 1009M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1009M     0 1009M   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user
/dev/sda1      ext4        34G   33G     0 100% /mnt/boot-sav/sda1
/dev/sdb1      ext4        34G  4.7G   27G  15% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe264e264

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    71096319    35547136   83  Linux

Disk /dev/sdb: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders, total 71096640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012a59

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    71096319    35547136   83  Linux


No OS has been found on this computer.

=================== Recommended repair
Recommended-Repair
This setting will not act on the MBR.



No change has been performed on your computer.

```

---

### Post by grahammechanical on 2015-01-01
I do not support Linux Mint. But Boot Repair gives you a clue

> No OS has been found on this computer.

Regards.

---

### Post by howefield on 2015-01-01
Thread moved to the "*MINT*" section of the forum.

---

