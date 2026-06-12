---
title: "Dual Boot Ubuntu Windows 7 issues"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by Khroft on 2013-02-26
Hello!

I had Windows 7 installed on a new computer. I wanted to install Ubuntu 12.10. I installed it regarding feng shui (as I think) but... GRUB isnt appearing and Windows is starting without any dialogues.

I read that problem might be with BIOS and UEFI. But it seems its is not my case. For example: GParted doesnt show any additional partition on HDD; if I'm trying to boot in UEFI manually - there is a fail something like: "your video card are not able to start in UEFI"; Ubuntu installed automatically/manually without choosing any EFI partition.

I tried to solve it by boot-repair (BR). Unfortunately, it doesnt see any partitions except flash-drive (from this flash it  has started). *sudo fdisk -l *shows only flash drive too. So, BR made conlusion that "No OS has been found on this computer."

Unfortunatelly, I'm not able to connect that computer to internet, so I dont have link with log. I have *.txt. I can put it here if it's necessary. 

Appreciate your help!

---

### Post by oldfred on 2013-02-26
Welcome to the forums.

Moved to your own thread so issues do not get confused in Boot-Repair mega-Thread.

Most Windows 7 systems were installed in BIOS/MBR mode even if BIOS was also UEFI. Then you have the 4 primary partition limit. 

Did you shrink Windows with Windows Disk tools but not create any new partitions with Windows? 

Best to copy BootInfo data. It is very large now as it includes bootinfoscript plus lots of other data. You can manually copy to pastebin from another computer also. If you post here, be sure to use code tags or highlight and click on # in edit panel above message

---

### Post by mtambo on 2013-02-26
.
[]("http://paste.ubuntu.com/5567676/")

---

### Post by Khroft on 2013-02-26
Thank you!

It is my working computer. Windows was instaled by our admins. They made partition for Windows. So there were two partitions then I've started to install Ubuntu:
1. Windows (~100Gb ntfs) 
2. Other disk space (~400Gb ntfs)

I'm not able to re-install Windows. I even dont have root on it. But I need it for some kind of monthly reports.

Please see bootinfo below. As I said, it doesnt see any devices except flash drive. *sudo fdisk -l* doesnt see too:(

    ```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 710432 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4022 MB, 4022337536 bytes
6 heads, 28 sectors/track, 46762 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     7,856,127     7,854,080   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        00A4-3ACC                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default /syslinux/vesamenu.c32
prompt 0
timeout 00
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5297]) leaked on lvscan invocation. Parent PID 6255: bash
File descriptor 8 (pipe:[5297]) leaked on lvscan invocation. Parent PID 6255: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-02-26__14h04 ===================
boot-repair version : 3.195~ppa11~lucid
boot-sav version : 3.195~ppa11~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version : 3.195~ppa11~lucid
File descriptor 7 (pipe:[5297]) leaked on lvs invocation. Parent PID 3598: /bin/sh
File descriptor 8 (pipe:[5297]) leaked on lvs invocation. Parent PID 3598: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 29nov2012, squeeze, Debian, x86_64)
CPU op-mode(s):        32-bit, 64-bit
initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal BOOT_IMAGE=/live/vmlinuz2

=================== os-prober:


=================== blkid:
/dev/sda1: LABEL="MYLINUXLIVE" UUID="00A4-3ACC" TYPE="vfat"
/dev/loop0: TYPE="squashfs"

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sda: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4022MB  4021MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:4022MB:scsi:512:512:msdos:Kingston DataTraveler 2.0;
1:1049kB:4022MB:4021MB:fat32::boot;


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus char console core cpu_dma_latency disk fd full fuse hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 sda sda1 shm snapshot snd sndstat stderr stdin stdout urandom vga_arbiter xconsole zero
ls /dev/md:

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    2.0G  7.2M  2.0G   1% /
tmpfs        tmpfs    2.0G     0  2.0G   0% /lib/init/rw
udev         tmpfs    2.0G  144K  2.0G   1% /dev
tmpfs        tmpfs    2.0G     0  2.0G   0% /dev/shm
/dev/sda1     vfat    3.8G  339M  3.5G   9% /live/image
tmpfs        tmpfs    2.0G  7.2M  2.0G   1% /live/cow
tmpfs        tmpfs    2.0G     0  2.0G   0% /live
tmpfs        tmpfs    2.0G  8.0K  2.0G   1% /tmp

=================== fdisk -l:

Disk /dev/sda: 4022 MB, 4022337536 bytes
6 heads, 28 sectors/track, 46762 cylinders
Units = cylinders of 168 * 512 = 86016 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2a84

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13       46763     3927040    b  W95 FAT32


No OS has been found on this computer.

=================== Recommended repair
Recommended-Repair
This setting will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

Boot successfully repaired.

You can now reboot your computer.

pastebin.com ko (), using paste.ubuntu Please report this message to yannubuntu@gmail.com
```

---

### Post by oldfred on 2013-02-26
Without seeing hard drive(s) it does not tell anything.

Can you get into BIOS as that is often locked out by Admins also.
Does BIOS/UEFI show hard drives still? Did connections come loose?

If this is Company computer are you allowed to install another system on it?

---

### Post by Khroft on 2013-02-26
I'm science worker so I need some kind of special soft. It much more convenient (and cheaper:D) to use free soft. I have permission for installing Ubuntu, but our lazy admins do not want to do it because it is not their typical work.

Yes, I have access to BIOS. It sees HDD. And even Windows boots well. This HDD also available from Ubuntu started from USB drive. The problem is only with Boot-repair.:confused:

---

### Post by harimodel007 on 2013-02-26
try to re install the existing GRUB and then run Root -repair within a live cd.

---

### Post by Khroft on 2013-02-27
I did it! I dont know that was wrong. That was another:

1) First time live-flash started in UEFI mode, despite Windows and Ubuntu were installed in BIOS.
2) For first time I used standart live-flash-maker from Ubuntu official site. For second I used LiLi. 

I suppose, the main reason is in starting live-flash in UEFI mode, but I'm not sure.

---

### Post by oldfred on 2013-02-27
Glad you resolved it.

Many new systems have UEFI/BIOS and  those with Windows 8 pre-installed use the UEFI mode. Only a few other new systems with Windows 7 used UEFI but most were still BIOS.

---

