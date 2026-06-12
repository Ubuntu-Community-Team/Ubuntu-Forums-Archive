---
title: "Batting &quot;0 for 3&quot; with grub rescue"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by Tom Collier on 2011-12-21
I've limped into the forums by Live USB after my eeePC 1000HD has gone all "grub rescue" on me.

Tried the excellent and extraordinarily clear HOWTO to boot and install from the grub rescue prompt by drs305. No errors line after line, but no results at the end of the process, either. 

Tried Boot-Repair from terminal twice. It claimed to have succeeded, but I still get nothing but the "rescue" prompt when I turn on my computer.

eeePC 1000HD with Windows XP on one side, Ubuntu 10.04 LTS on the other, and a middle ground NTSF partition that allowed both to save files to the middle and let me print to a boat-anchor of an old Lexmark that scorned Linux drivers. (Santa is going to fix ALL of that).

Any help (that works) will be so appreciated that I'll dedicate my next contribution to our Food Bank in your honor.......

Here's the output from the boot_info_script summary.

                 ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 15296 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   125,853,209   125,853,147   7 NTFS / exFAT / HPFS
/dev/sda2         125,853,210   180,827,639    54,974,430   7 NTFS / exFAT / HPFS
/dev/sda4         180,827,640   234,372,284    53,544,645   5 Extended
/dev/sda5         180,827,703   232,058,924    51,231,222  83 Linux
/dev/sda6         232,058,988   234,372,284     2,313,297  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       0f4b37af-5782-4b5e-bccf-93858024f3e7   ext3       
/dev/sda1        FEDC6E73DC6E265D                       ntfs       
/dev/sda2        9C1CCA131CC9E7FA                       ntfs       
/dev/sda5        c5ba1651-91e9-4654-bc85-24fa6d14b350   ext4       
/dev/sda6        709169d3-d5a1-4e3f-b1b5-af3dacc76e60   swap       
/dev/sdb1        10D7-92BE                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/0f4b37af-5782-4b5e-bccf-93858024f3e7 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=15 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr = "Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=c5ba1651-91e9-4654-bc85-24fa6d14b350 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    echo    'Loading Linux 2.6.32-37-generic ...'
    linux    /boot/vmlinuz-2.6.32-37-generic root=UUID=c5ba1651-91e9-4654-bc85-24fa6d14b350 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=c5ba1651-91e9-4654-bc85-24fa6d14b350 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-36-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    echo    'Loading Linux 2.6.32-36-generic ...'
    linux    /boot/vmlinuz-2.6.32-36-generic root=UUID=c5ba1651-91e9-4654-bc85-24fa6d14b350 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-36-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5ba1651-91e9-4654-bc85-24fa6d14b350
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set FEDC6E73DC6E265D
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c5ba1651-91e9-4654-bc85-24fa6d14b350 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=709169d3-d5a1-4e3f-b1b5-af3dacc76e60 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  86.384025097 = 92.754140672   boot/grub/core.img                             1
  86.367541790 = 92.736441856   boot/grub/grub.cfg                             1
 107.482818127 = 115.408797184  boot/initrd.img-2.6.32-36-generic              1
 100.404761791 = 107.808792064  boot/initrd.img-2.6.32-37-generic              1
 101.736979961 = 109.239250432  boot/vmlinuz-2.6.32-36-generic                 1
 102.871505260 = 110.457437696  boot/vmlinuz-2.6.32-37-generic                 1
 100.404761791 = 107.808792064  initrd.img                                     1
 107.482818127 = 115.408797184  initrd.img.old                                 1
 102.871505260 = 110.457437696  vmlinuz                                        1
 101.736979961 = 109.239250432  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)


ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-12-21__20h06 ****************
boot-repair version : 3.02-0ppa1~lucid
clean version : 3.02-0ppa1~lucid
internet: connected
clean-gui version : 3.02-0ppa1~lucid
/usr/share/clean/cleancommon-gui.sh: line 160: 25507 Terminated              while true; do
done
python-software-properties version : 0.75.10
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
LIVESESSION is : yes
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
OSPROBER: /dev/sda1:Windows NT/2000/XP:Windows:chain
/dev/sda5:Ubuntu 10.04.3 LTS (10.04):Ubuntu:linux
BLKID: /dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="0f4b37af-5782-4b5e-bccf-93858024f3e7" TYPE="ext3"
/dev/sda1: UUID="FEDC6E73DC6E265D" TYPE="ntfs"
/dev/sda2: UUID="9C1CCA131CC9E7FA" TYPE="ntfs"
/dev/sda5: UUID="c5ba1651-91e9-4654-bc85-24fa6d14b350" TYPE="ext4"
/dev/sda6: UUID="709169d3-d5a1-4e3f-b1b5-af3dacc76e60" TYPE="swap"
/dev/sdb1: UUID="10D7-92BE" TYPE="vfat"
sda1 contains Windows (windows)
sda5 contains Ubuntu 10.04.3 LTS (linux)
1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
mkdir: cannot create directory `/mnt/clean/sda5/var/log': Input/output error
mkdir: cannot create directory `/mnt/clean/sda5/var/log': Input/output error
Total of 2 OS detected on sda disk.
dir: cannot access /mnt/clean/sda5/var/log/clean/mbr_backups: Input/output error
mkdir: cannot create directory `/mnt/clean/sda5/var/log': Input/output error
sda contains minimum one OS
FDISK
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x515dee3b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125853209    62926573+   7  HPFS/NTFS
/dev/sda2       125853210   180827639    27487215    7  HPFS/NTFS
/dev/sda4       180827640   234372284    26772322+   5  Extended
/dev/sda5       180827703   232058924    25615611   83  Linux
/dev/sda6       232058988   234372284     1156648+  82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad890

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x515dee3b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125853209    62926573+   7  HPFS/NTFS
/dev/sda2       125853210   180827639    27487215    7  HPFS/NTFS
/dev/sda4       180827640   234372284    26772322+   5  Extended
/dev/sda5       180827703   232058924    25615611   83  Linux
/dev/sda6       232058988   234372284     1156648+  82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad890

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
sda1 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda1, with-os, no-gpt, no-fstab, .
sda2 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda2, no-os, no-gpt, no-fstab, .
sda5 : sda, not-sepboot, grub, aptget, 32, with boot, /mnt/clean/sda5, with-os, no-gpt, fstab-without-efi, .
PARTED: Model: ATA ST9120817AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  64.4GB  64.4GB  primary   ntfs            boot
2      64.4GB  92.6GB  28.1GB  primary   ntfs
4      92.6GB  120GB   27.4GB  extended
5      92.6GB  119GB   26.2GB  logical   ext4
6      119GB   120GB   1184MB  logical   linux-swap(v1)


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  4007MB  4007MB  primary  fat32        boot, lba
MOUNT aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/loop1 on /media/0f4b37af-5782-4b5e-bccf-93858024f3e7 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/clean/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/clean/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/clean/sda5 type ext4 (rw)
/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev:  agpgart audio block bsg btrfs-control bus char console core cpu_dma_latency disk dri dsp ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log mapper mcelog mem mixer net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda4 sda5 sda6 sdb sdb1 sequencer sequencer2 sg0 sg1 shm snapshot snd sndstat stderr stdin stdout urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.1G  223M  754M  23% /
none      devtmpfs    493M  300K  492M   1% /dev
/dev/sdb1     vfat    3.8G  1.8G  2.1G  46% /cdrom
/dev/loop0
squashfs    672M  672M     0 100% /rofs
none         tmpfs    498M  112K  497M   1% /dev/shm
tmpfs        tmpfs    498M  792K  497M   1% /tmp
none         tmpfs    498M   92K  497M   1% /var/run
none         tmpfs    498M  4.0K  498M   1% /var/lock
none         tmpfs    498M     0  498M   0% /lib/init/rw
/dev/loop1    ext3    1.1G  223M  754M  23% /media/0f4b37af-5782-4b5e-bccf-93858024f3e7
/dev/sda1  fuseblk     61G   24G   37G  40% /mnt/clean/sda1
/dev/sda2  fuseblk     27G  743M   26G   3% /mnt/clean/sda2
/dev/sda5     ext4     25G   16G  7.3G  69% /mnt/clean/sda5
FDISK
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x515dee3b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   125853209    62926573+   7  HPFS/NTFS
/dev/sda2       125853210   180827639    27487215    7  HPFS/NTFS
/dev/sda4       180827640   234372284    26772322+   5  Extended
/dev/sda5       180827703   232058924    25615611   83  Linux
/dev/sda6       232058988   234372284     1156648+  82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad890

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
Logs saved into /mnt/clean/sda1/clean/log/2011-12-21__20h06boot-repair01
mkdir: cannot create directory `/mnt/clean/sda5/var/log': Input/output error
cp: accessing `/mnt/clean/sda5/var/log/clean/log/2011-12-21__20h06boot-repair01': Input/output error
Logs saved into /mnt/clean/sda5/var/log/clean/log/2011-12-21__20h06boot-repair01
combobox_ostoboot_bydefault_fillin
Order Linux according to their /boot type 64
Order Linux according to their /boot type 32
combobox_efi_fillin sda5
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda5
efi_show_hide 3 (no-gpt)
set_radiobutton_place_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda5
efi_show_hide 3 (no-gpt)
************************Before mainwindow appear
FSCK_ACTION no PASTEBIN_ACTION yes
MBR_ACTION reinstall REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB 3 (sda5) PART_TO_REINSTALL_GRUB_PURGE 3 (sda5) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda2) grub-pc ()
/usr/share/clean/bootrepair.sh: line 56: 26135 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda5 (Ubuntu 10.04.3 LTS)
RETOURCOMBO_ostoboot_bydefault : sda5 (Ubuntu 10.04.3 LTS)
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda5
efi_show_hide 3 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda2
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda5
efi_show_hide 3 (no-gpt)
set_radiobutton_place_grub
combobox_separateboot_fillin
separate_bootpart and efi show_hide sda5
efi_show_hide 3 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda2
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda2
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda2
internet: connected
************************Before Repairing
FSCK_ACTION no PASTEBIN_ACTION yes
MBR_ACTION reinstall REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB 3 (sda5) PART_TO_REINSTALL_GRUB_PURGE 3 (sda5) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda2) grub-pc ()
Freed space function
/dev/sda1             62926572  24974528  37952044  40% /mnt/clean/sda1
/dev/sda5             25213284  16315208   7617296  69% /mnt/clean/sda5
Reinstall the GRUB of sda5 into the MBR of sda
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sda5)
dpkg_function
chroot: cannot run command `dpkg': No such file or directory
grub-install (GNU GRUB 1.98-1ubuntu12)
/usr/lib/grub/grub-mkconfig_lib: 1: cannot open s: No such file
/usr/lib/grub/grub-mkconfig_lib: 1: &#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;_Q&#65533;&#65533;cx0L&#65533;&#65533;(c&#65533;&#65533;#&#65533;&#65533;B%&#65533;&#65533;y&#65533;&#65533;: not found
/usr/lib/grub/grub-mkconfig_lib: 1: Syntax error: "|" unexpected
/usr/lib/grub/grub-mkconfig_lib: 1: cannot open s: No such file
/usr/lib/grub/grub-mkconfig_lib: 1: &#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;_Q&#65533;&#65533;cx0L&#65533;&#65533;(c&#65533;&#65533;#&#65533;&#65533;B%&#65533;&#65533;y&#65533;&#65533;: not found
Mount all the partitions for the logs
Unhide boot menu (10 seconds) if Wubi detected
internet: connected
touch: cannot touch `/mnt/clean/sda5/var/log/clean/log/boot-repair': Input/output error
```

---

### Post by bcbc on 2011-12-21
It looks like boot repair isn't able to access /dev/sda5:
> mkdir: cannot create directory `/mnt/clean/sda5/var/log': Input/output error

From the live CD/USB:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

EDIT: I don't think the *--boot-directory=* option is in Lucid. It might be, but use *--root-directory=* instead.

---

### Post by darkod on 2011-12-21
Also, please explain in more detail about the error. Do you have two boot menu screens or only one? Does the error happen regardless whether you select ubuntu or windows? Do you get the boot menu at all?

I have noticed you seem to have a wubi mbr entry in your boot.ini:
```

[boot loader]
timeout=15
[COLOR=Red]default=C:\wubildr.mbr[/COLOR]
[operating systems]
[COLOR=Red]C:\wubildr.mbr = "Ubuntu"[/COLOR]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

But this entry should not affect booting ubuntu. However, after selecting XP from your main grub2 menu, you might be getting "grub rescue" which is coming from the wubi mbr. You obviously don't have a wubi install right now, and grub2 is clearly on the MBR of your hdd. This seems as a left over from earlier wubi install.

---

### Post by Tom Collier on 2011-12-21
Ah! You have jogged my memory...when I was first introduced to Ubuntu (9.xx) I used it through Wubi for almost a year before I converted to a dual boot.

And I remember finally getting irritated that XP booted by default if I left the boot menu to do its thing. So I changed it to Ubuntu by default. But that was so long ago, I don't remember how I did it.  Come to think of it, when I wanted to boot into XP, I always got a double screen and had to tell it twice to get me into XP. Perhaps this is an artifact and I never really

a.) created a true dual boot system, or
b.) installed Grub on the Ubuntu side (/dev/sda5)??

The error in detail:

I used to get a Grub menu when I turned on my computer. Now I get: some text about limited editing capacity and using the TAB key one way or another, and a prompt at the bottom of the page that reads ">rescue".  That's it.

EDIT: if I install Grub to  /dev/sda5 as bcbc suggests upthread, will it preserve my dual boot?

---

### Post by darkod on 2011-12-22
The commands bcbc suggested will not install grub2 on the /dev/sda5 partition. Because you will be running them from live mode, from the cd (usb), you have to let it know where is your root partition.
That's why with the first command you are mounting your root partition which is /dev/sda5 to the mount point /mnt. That is what the 5 means.
The second command installs grub2 to /dev/sda (the MBR of the disk) with the parameter specifying the root directory, mounted at /mnt.

I would try those commands first, because even though the script says grub2 is installed on the MBR, something might be wrong. Just boot into live mode with cd or usb and run those commands to reinstall grub2 to the MBR. Reboot and see if it helped.

---

### Post by Tom Collier on 2011-12-22
Here's what that did command did.....

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
cp: cannot stat `/mnt/boot/grub/sfs.mod': Input/output error
ubuntu@ubuntu:~$ 
```

---

### Post by darkod on 2011-12-22
I have no idea about that error, and short google search doesn't give anything conclusive. Lets try to completely remove and reinstall grub2. For that you need to chroot into your root partition which needs a few more commands than just mount.

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

To completely remove and reinstall grub2, and recreate the config files:

```
apt-get --purge remove grub-pc
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit the chroot and unmount:

```
exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

Reboot and see if that helped.

---

### Post by Tom Collier on 2011-12-22
Here's what the "apt-get" command line in the second block generated:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get --purge remove grub-pc
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@ubuntu:/# 
```

I really appreciate your walking me through this....

---

### Post by darkod on 2011-12-22
Uh, this is beyond me unfortunately. Give it a shot without the two apt-get commands in the second block. Lets hope that just the mkconfig, update and install might help somehow.
I was hoping for a clean install of grub2 but it seems there are some issues.

---

### Post by N00b-un-2 on 2011-12-22
oy... yet another Wubi headache.  Word for the wise DO NOT USE WUBI!  Set up a real dual boot and you'll be a lot happier in the end.
It looks like your live USB may be borked.  Try creating a new live USB or CD.  Then boot into it and create your chroot the same way you did only omit
```
sudo mount --bind /sys /mnt/sys
``` 
When I have to restore GRUB after messing around with another OS and my MBR gets overwritten, I create my chroot with /proc and /dev only and haven't blown up my computer yet :wink:
After you chroot int /mnt, issue the commands 
```
sudo grub-install /dev/sda
sudo update-grub
```

This will install GRUB to the MBR of your hard drive, overwriting whatever else is installed to it and it will update it.  exit out of your chroot, unmount your drive and reboot.  Grub --should-- be working.

---

### Post by bcbc on 2011-12-22
Try fsck'ing /dev/sda5. Even though it's mounting okay, there's something messed up:
```
sudo umount /dev/sda5
sudo fsck -fv /dev/sda5

```

(Make sure it's unmounted. -f force it even if it appears clean. -v verbose output. You can add -y (attempt to fix) as well (otherwise it will prompt you).

You should probably take a data backup beforehand.

---

### Post by Tom Collier on 2011-12-23
Solved ... (which, I suppose is what you call it when you obliterate the original problem, rather than address it command by command in the terminal.)

10.04 Live USB did not display the existence (!) of certain folders that showed up using the *ls* command and full path at the grub *rescue* prompt. Not talking about hidden files, here. These files did show up in Lucid Puppy, so I used Lucid Puppy Live USB to transfer a few of these undetected (NOT hidden...*undetected*...I know the difference) files that I wanted to save but were not in my backup.

I downloaded and burned a new, fresh checksummed iso of 10.04.3 LTS, and did a clean, single OS reinstall.

Back in business and weaned from Windows 'cause Santa is gonna solve the wireless print-from-Linux problem that kept the dual boot system around in the first  place.

Thanks for all your assistance! This is one of the most helpful forums in the Intertubes. 

Politically correct Holiday Greetings of your choice, or "Happy All Of The Above."

---

### Post by N00b-un-2 on 2011-12-27
just out of curiosity, what type of printer do you have and what do you mean by "wireless"?  If you have a bluetooth printer, you're options may be limited.  On the other hand most wifi capable printers support multiple print protocols.  Try configuring your printer using ipp, lpr/lpd instead of samba.  Samba relies on on a host system that the printer is attached physically to in order to work, whereas lpr and ipp configure your printer as a standalone print server.

---

