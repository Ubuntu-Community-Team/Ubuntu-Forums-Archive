---
title: "dual boot ubuntu missing - wubi"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by devcool on 2012-11-12
I have dual boot windows 7 and ubuntu 12.04. Now ubuntu is missing after windows checked /tmp for errors. I only get windows and gnu grub options upon reboot. I ran a liveusb and boot-repair and still only getting gnu grub. I am attaching bootscript output. How do I restore my normal ubuntu and restore files and folders?

    ```
Boot Info Script 0.61.full + Boot-Repair extra info 


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /wubildr

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 2998472 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   533,389,311   532,977,664   7 NTFS / exFAT / HPFS
/dev/sda3         533,389,312   594,198,527    60,809,216   f W95 Extended (LBA)
/dev/sda5         533,391,360   594,198,527    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          3,608     3,932,159     3,928,552   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C0C646D2C646C87C                       ntfs       
/dev/sda2        F65048AB50487501                       ntfs       
/dev/sda4        DA6052146051F829                       ntfs       LENOVO_PART
/dev/sda5        DC72893972891982                       ntfs       LENOVO
/dev/sdb1        3F00-E6D7                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/C0C646D2C646C87C  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/LENOVO            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2/Wubi



========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-11__14h20 ===================
boot-repair version : 3.194~ppa53~precise
boot-sav version : 3.194~ppa53~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.194~ppa53~precise
boot-repair is executed in live-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda4:Windows Recovery Environment (loader):Windows1:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="C0C646D2C646C87C" TYPE="ntfs"
/dev/sda2: UUID="F65048AB50487501" TYPE="ntfs"
/dev/sda4: LABEL="LENOVO_PART" UUID="DA6052146051F829" TYPE="ntfs"
/dev/sda5: LABEL="LENOVO" UUID="DC72893972891982" TYPE="ntfs"
/dev/sdb1: SEC_TYPE="msdos" UUID="3F00-E6D7" TYPE="vfat"


1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
There is Wubi inside sda2
=================== UEFI/Legacy mode :
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/C0C646D2C646C87C.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/F65048AB50487501.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/LENOVO.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST320LT020-9YG14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
1      1049kB  211MB  210MB   primary   ntfs         boot
2      211MB   273GB  273GB   primary   ntfs
3      273GB   304GB  31.1GB  extended               lba
5      273GB   304GB  31.1GB  logical   ntfs
4      304GB   320GB  15.8GB  primary   ntfs         diag


Model:   (scsi)
Disk /dev/sdb: 2013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1847kB  2013MB  2011MB  primary  fat16        boot

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:4096:msdos:ATA ST320LT020-9YG14;
1:1049kB:211MB:210MB:ntfs::boot;
2:211MB:273GB:273GB:ntfs::;
3:273GB:304GB:31.1GB:::lba;
5:273GB:304GB:31.1GB:ntfs::;
4:304GB:320GB:15.8GB:ntfs::diag;

BYT;
/dev/sdb:2013MB:scsi:512:512:msdos: ;
1:1847kB:2013MB:2011MB:fat16::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/C0C646D2C646C87C type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/F65048AB50487501 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/LENOVO type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 rts51x0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  108M  1.8G   6% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      774M  868K  773M   1% /run
/dev/sdb1      vfat       1.9G  1.6G  315M  84% /cdrom
/dev/loop0     squashfs   660M  660M     0 100% /rofs
tmpfs          tmpfs      1.9G   48K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G  176K  1.9G   1% /run/shm
/dev/sda1      fuseblk    200M   29M  172M  15% /media/C0C646D2C646C87C
/dev/sda2      fuseblk    255G   37G  218G  15% /media/F65048AB50487501
/dev/sda5      fuseblk     29G  9.8G   20G  34% /media/LENOVO
/dev/sda4      fuseblk     15G  8.5G  6.3G  58% /mnt/boot-sav/sda4

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1a0aba4b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   533389311   266488832    7  HPFS/NTFS/exFAT
/dev/sda3       533389312   594198527    30404608    f  W95 Ext'd (LBA)
/dev/sda4       594198528   625142447    15471960   12  Compaq diagnostics
/dev/sda5       533391360   594198527    30403584    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        3608     3932159     1964276    6  FAT16



=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot


Quantity of real Windows: 1
mount -o loop /media/F65048AB50487501/ubuntu/disks/root.disk /mnt/boot-sav/wubi1
mount: /dev/loop1: can't read superblock
The file browser that just opened will let you access your Wubi (Linux installed into Windows) files. (/mnt/boot-sav/wubi1/home) Please backup your data now! Then close this window.
xdg-open: file '/mnt/boot-sav/wubi1/home' does not exist
umount /mnt/boot-sav/wubi1
umount: /mnt/boot-sav/wubi1: not mounted
fsck -f -y /media/F65048AB50487501/ubuntu/disks/root.disk
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /media/F65048AB50487501/ubuntu/disks/root.disk
Could this be a zero-length partition?
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.

pastebinit  packages needed
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin: No such file or directory
```

---

### Post by Mark Phelps on 2012-11-12
You installed using Wubi.  Wubi doesn't use GRUB; instead, it uses a derivative known as GRUB4DOS.  When you ran boot-repair, you forced GRUB (which you do NOT need and will NOT work with Wubi) into the MBRs of BOTH disks.

Does Win7 still boot OK? IF it does, count yourself lucky and as soon as you can, use the Win7 backup feature to create and burn a Win7 Repair CD.  You will need this to REMOVE GRUB from the MBR of the disk you use to boot Win7.

---

### Post by oldfred on 2012-11-12
Added code tags, highlight like copy and click on # in edit panel to auto add code tags. Added wubi to title as only a few know wubi as it is not a true dual boot.

It looks like Boot-Repair added syslinux boot loader which works just like the Windows boot loader. Does Windows boot?

If wubi does not boot, you may still need to run fsck on the wubi file. 

# from terminal on liveUSB
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by devcool on 2012-11-12
Windows boots just fine and I still get that gnu grub as before. Here is what I get when I run those commands. Also, root.disk is 0kb. I looked in the hidden found folder and did not find a file of the appropriate size.

ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount/dev/sda2/media/win
sudo: mount/dev/sda2/media/win: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/win
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /media/win/ubuntu/disks/root.disk
Could this be a zero-length partition?

---

### Post by cwsnyder on 2012-11-12
It looks as if Windows really 'fixed' your Ubuntu install.  Since WUBI installs in the NTFS partition with Windows, you are at the mercy of Windows utilities.  WUBI is simply a file in Windows.

If you select the GNU GRUB option, does it do more than just lock up the system?

If not, I would say that Windows has basically wiped your install and you need to re-install GRUB.

---

### Post by oldfred on 2012-11-12
Agree with    	cwsnyder.

If Windows chkdsk thought there was an issue somewhere in the root.disk file, it may have moved it to your chkdsk folder and renamed it. One of the disadvantages of wubi. Wubi is good for an extended test but not long term use as it has to depend on the NTFS file system and Windows boot loader.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


---

### Post by devcool on 2012-11-12
If that is the case, then I would not suggest anyone to use Wubi and I would never use it again. Windoze surely did a number:( It is quite disturbing.  These issues are not made clear on the Ubuntu download page where Wubi is apparently officially supported by Ubuntu.

I did not any files of appropriate file size in the found folder. Any other location to look? Is there chkdisk folder. Anything else it could be renamed to. Is it possible things just disappear in Windoze. Any other suggestions. Surely, root.disk or data could be retrievable somehow?

---

### Post by oldfred on 2012-11-12
While wubi is supported it still is relying on Windows which makes it less reliable. Ubuntu has no control over what Windows does.

And it does not matter what system you run, you need good backups. Hard drives fail, users make errors and just general corruption all make backups important.

Do you have a folder or folder like with .chk files?
C:/FOUND.000

Update, more info here on missing  root.disk:

[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by devcool on 2012-11-13
Thanks for the info. There is no file in that folder greater then 1GB. The next step I'll try is to use some recovery software to see if I can locate this root.disk. Is it correct that all the information for the ubuntu install is on this file? I concur with all that you both have said. However, I don't think it is clear on the ubuntu download page that wubi is for evaluation purposes only.

---

