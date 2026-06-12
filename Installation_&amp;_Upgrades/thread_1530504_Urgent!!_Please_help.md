---
title: "Urgent!! Please help"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Jonny87 on 2010-07-13
**Ubuntu 10:04**
I've installed another OS and when I tried to restore the grub using the live cd,
```
sudo grub-install --root-directory=/mnt/root /dev/sda
```I get the the following error;
```
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```I've done this grub-install method several times before with no problems at all. This is the first time I've had an issue.

PLEASE! How can I fix this with out re-installing my Ubuntu partition. I haven't backed it up yet as I've just not long ago re-installed it and still setting things up.

---

### Post by oldfred on 2010-07-13
You have to tell it which partition to find grub/Ubuntu by mounting it first:

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Jonny87 on 2010-07-13
> **oldfred said:**
> You have to tell it which partition to find grub/Ubuntu by mounting it first:

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Sorry should hve mentioned tjhat I had mounted the sda5 partition, under /mnt/root.
Here's the whole process;

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/root
ubuntu@ubuntu:~$ cd /mnt/root/home
ubuntu@ubuntu:/mnt/root/home$ ls
hannie  jonny
ubuntu@ubuntu:/mnt/root/home$ cd ~
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/root /dev/sda
/usr/sbin/grub-probe: error: cannot seek `/dev/sda'.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

```
ubuntu@ubuntu:~$ cd /mnt/root/home
ubuntu@ubuntu:/mnt/root/home$ ls
hannie  jonny
```
This bit was me double checking that I had the right partition mounted.

---

### Post by Jonny87 on 2010-07-13
If it helps any here is my HDD setup;

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc8f11f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30579   245624793+   5  Extended
/dev/sda2           30580       38416    62950702+   7  HPFS/NTFS
/dev/sda3           38417       38914     3993600   82  Linux swap / Solaris
/dev/sda5               1       10193    81873920   83  Linux
/dev/sda6           10194       20386    81875241   83  Linux
/dev/sda7           20387       30579    81875241   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000875d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b482ee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          64      512000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdc2              64        4871    38606848   8e  Linux LVM

Disk /dev/sdd: 32.3 GB, 32326663680 bytes
255 heads, 63 sectors/track, 3930 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

```

Please I need to get this things going again.

---

### Post by oldfred on 2010-07-13
Post the results.txt so we can see all the details:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Jonny87 on 2010-07-14
I went in to Gparted to try ckeck the partitions and perhaps delete the  Opensuse partition but nothing on the drive showed up. it has an error  saying "Invalid partition table - recursive partition on /dev/sda". but I  can still mount patitions and see the files.

Is there a way to fix this with out loosing it all? It would have to  happen on the day that I was going to back everything up wouldn't it.

Please help.

---

### Post by oldfred on 2010-07-14
First Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

I have not used it, but many have solved various partitions table issues with testdisk.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Jonny87 on 2010-07-14
The RESULTS.txt 

                > Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 179782744 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   491,251,634   491,249,587   5 Extended
/dev/sda5               2,048   163,749,887   163,747,840  83 Linux
/dev/sda6         163,750,608   327,501,089   163,750,482  83 Linux
/dev/sda7         327,501,153   491,251,634   163,750,482  83 Linux
/dev/sda2         491,251,635   617,153,039   125,901,405   7 HPFS/NTFS
/dev/sda3         617,154,560   625,141,759     7,987,200  82 Linux swap / Solaris

the logical partition /dev/sda5 is not contained in the extended partition /dev/sda1

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        B42C76902C764CFC                       ntfs                                     
/dev/sda3                                               swap                                     
/dev/sda5        e45a0119-6a1d-4dcd-94e7-707a2818c97a   ext3                                     
/dev/sda6        614db568-763e-470f-8612-a62341bd66cf   ext3                                     
/dev/sda7        5d1b8edb-3e56-47e1-815e-3ad523783694   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        348c516a-3283-46fe-adf6-a8589bd557b3   ext4       Library                       
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Library           ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
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
search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e45a0119-6a1d-4dcd-94e7-707a2818c97a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e45a0119-6a1d-4dcd-94e7-707a2818c97a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e45a0119-6a1d-4dcd-94e7-707a2818c97a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e45a0119-6a1d-4dcd-94e7-707a2818c97a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e45a0119-6a1d-4dcd-94e7-707a2818c97a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b42c76902c764cfc
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

# <file system>                 <mount point>   <type>  <options>                   <dump>  <pass>
proc                            /proc           proc    nodev,noexec,nosuid             0       0
/dev/sda5                       /               ext3    errors=remount-ro             0       1

# swap was on /dev/sda3 during installation
UUID=d073aaa4-f29c-4925-a660-ad9834f8c6af     none            swap    sw                          0       0

/dev/fd0                        /media/floppy0  auto    rw,user,noauto,exec,utf8         0       0

#Mounting jonny's home folders.
UUID=348c516a-3283-46fe-adf6-a8589bd557b3    /media/Library        ext4    user,defaults,            0    0
/media/Library/Home/jonny/Documents        /home/jonny/Documents    none    bind                0    0
/media/Library/Home/jonny/Downloads        /home/jonny/Downloads    none    bind                0    0
/media/Library/Home/jonny/Music            /home/jonny/Music    none    bind                0    0
/media/Library/Home/jonny/Pictures        /home/jonny/Pictures    none    bind                0    0
/media/Library/Home/jonny/websites        /home/jonny/Websites    none    bind                0    0
/media/Library/Home/shared/Videos        /home/jonny/Videos    none    bind                0    0

#Mounting hannie's home folders.
UUID=348c516a-3283-46fe-adf6-a8589bd557b3    /media/Library        ext4    user,defaults,            0    0
/media/Library/Home/hannie/Documents        /home/hannie/Documents    none    bind                0    0
/media/Library/Home/hannie/Downloads        /home/hannie/Downloads    none    bind                0    0
/media/Library/Home/hannie/Music        /home/hannie/Music    none    bind                0    0
/media/Library/Home/hannie/Pictures        /home/hannie/Pictures    none    bind                0    0
/media/Library/Home/shared/Videos        /home/hannie/Videos    none    bind                0    0

=================== sda5: Location of files loaded by Grub: ===================


   8.1GB: boot/grub/grub.cfg
   8.0GB: boot/initrd.img-2.6.32-23-generic
   8.1GB: boot/vmlinuz-2.6.32-23-generic
   8.0GB: initrd.img
   8.1GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Tue Jul 13 21:00:48 NZST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-WDC_WD3200AAKS-00VYA0_WD-WCARW1210434-part6 resume=/dev/disk/by-id/ata-WDC_WD3200AAKS-00VYA0_WD-WCARW1210434-part3 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.5-0.1-default

###Don't change this comment - YaST2 identifier: Original name:  Debian GNU/Linux, kernel 2.6.26-2-686 (/dev/sda7)###
title  Debian GNU/Linux, kernel 2.6.26-2-686 (/dev/sda7)
    root (hd0,6)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: Linux other 1###
title Linux other 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: Linux other 2###
title Linux other 2
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: Linux other 3###
title Linux other 3
    rootnoverify (hd0,4)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    map (hd3) (hd0)
    map (hd0) (hd3)
    rootnoverify (hd3,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-WDC_WD3200AAKS-00VYA0_WD-WCARW1210434-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.5-0.1-default

=============================== sda6/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD3200AAKS-00VYA0_WD-WCARW1210434-part3 swap                 swap       defaults              0 0
/dev/vg_jonnydesktop/lv_swap swap                 swap       defaults              0 0
/dev/disk/by-id/ata-WDC_WD3200AAKS-00VYA0_WD-WCARW1210434-part6 /                    ext3       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda6: Location of files loaded by Grub: ===================


  92.1GB: boot/grub/menu.lst
  92.0GB: boot/grub/stage2
  92.1GB: boot/initrd
  92.1GB: boot/initrd-2.6.31.5-0.1-default
  92.0GB: boot/vmlinuz
  92.0GB: boot/vmlinuz-2.6.31.5-0.1-default

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd1,6)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/sda7 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd1,6)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/sda7 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        'Kubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=d3cf113f-8771-41d5-a544-fc643b179b3c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        'Kubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=d3cf113f-8771-41d5-a544-fc643b179b3c ro single 
initrd        /boot/initrd.img-2.6.32-23-generic
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    errors=remount-ro 0       1
/dev/mapper/vg_jonnydesktop-lv_swap none            swap    sw              0       0
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda7: Location of files loaded by Grub: ===================


 182.0GB: boot/grub/menu.lst
 182.0GB: boot/grub/stage2
 182.1GB: boot/initrd.img-2.6.26-2-686
 182.0GB: boot/initrd.img-2.6.26-2-686.bak
 182.0GB: boot/vmlinuz-2.6.26-2-686
 182.1GB: initrd.img
 182.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by Jonny87 on 2010-07-14
running testdisk now.

it up to;
> Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection


not sure what i should choose.

---

### Post by oldfred on 2010-07-14
I have never used it but if you have standard MBR partitions (not gpt or Mac efi) you select intel.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

since the errors seem to be on the NTFS you may also run the chkdsk from windows.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

