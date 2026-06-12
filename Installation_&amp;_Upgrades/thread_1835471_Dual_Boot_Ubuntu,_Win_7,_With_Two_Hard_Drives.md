---
title: "Dual Boot Ubuntu, Win 7, With Two Hard Drives"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by dr_shred on 2011-08-29
I have a an hp desktop with two 250G HDs
with Win 7. When I try to install ubuntu it hangs up on
restart if I use the default settings which, I believe
installs ubuntu to sb1, i.e. the second HD.

I've done a lot of research in various forums on how to
install different partitions, but there doesn't appear to be
a definitive description on how to do this without, as some
suggest, disconnecting one of the HDs.

I've tried creating the /. boot, swap and /home or /data
partitions manually on sb1, but it always boots Win 7.

This is not a trivial task by any means and it would be
awesome for a detailed set of instructions to do this.

The current status is:

I'm able to boot from the ubuntu image cd

The installer installs ubuntui but on restart it hangs. I
think it installs it on the second 250G drive.

The manual partition manager comes up just fine, but it
doesn't allow me to place the required directories - /,
/boot, swap and /home on sa1, where, I assume, the win 7
boot sector is.

I have run

sudo fdisk -lu
sudo blkid
boot_info_script.sh

but can't decipher where the problem is.  Any help would
be greatly appreciated

Here are the screen dumps of the commands

sudo fdisk -lu

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6611f26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   953497599   476645376    7  HPFS/NTFS
/dev/sda3       953497600   976771071    11636736    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x307193bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488386559   244192256    7  HPFS/NTFS
/dev/sdb2       488388606   976771071   244191233    5  Extended
/dev/sdb5       968579072   976771071     4096000   82  Linux swap / Solaris
/dev/sdb6       488388608   960382975   235997184   83  Linux
/dev/sdb7       960385024   968574975     4094976   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1004 MB, 1004011520 bytes
248 heads, 32 sectors/track, 247 cylinders, total 1960960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     1960959      980464    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 247, 32) logical=(247, 23, 32)

```

sudo blkid

```

sudo blkid

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="961C03E41C03BDED" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="F2487D6F487D3387" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="2C0A19E30A19AB3A" TYPE="ntfs" 
/dev/sdb1: LABEL="DATA_DRIVE_1" UUID="F6AC0FEBAC0FA4E9" TYPE="ntfs" 
/dev/sdb5: UUID="585f74b9-bd9f-4c32-8b9d-3a6759dbc864" TYPE="swap" 
/dev/sdb6: UUID="3cce2773-3d49-4ebe-8aa7-58a37c45ecac" TYPE="ext4" 
/dev/sdb7: UUID="9da01abf-b670-4852-aa15-7d67cbe59765" TYPE="swap" 

```

RESULTS.txt

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Xfce Edition
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   953,497,599   953,290,752   7 NTFS / exFAT / HPFS
/dev/sda3         953,497,600   976,771,071    23,273,472   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   488,386,559   488,384,512   7 NTFS / exFAT / HPFS
/dev/sdb2         488,388,606   976,771,071   488,382,466   5 Extended
/dev/sdb5         968,579,072   976,771,071     8,192,000  82 Linux swap / Solaris
/dev/sdb6         488,388,608   960,382,975   471,994,368  83 Linux
/dev/sdb7         960,385,024   968,574,975     8,189,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        961C03E41C03BDED                       ntfs       SYSTEM
/dev/sda2        F2487D6F487D3387                       ntfs       OS
/dev/sda3        2C0A19E30A19AB3A                       ntfs       HP_RECOVERY
/dev/sdb1        F6AC0FEBAC0FA4E9                       ntfs       DATA_DRIVE_1
/dev/sdb5        585f74b9-bd9f-4c32-8b9d-3a6759dbc864   swap       
/dev/sdb6        3cce2773-3d49-4ebe-8aa7-58a37c45ecac   ext4       
/dev/sdb7        9da01abf-b670-4852-aa15-7d67cbe59765   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set 961c03e41c03bded
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set 2c0a19e30a19ab3a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sdb6    /    ext4    rw,errors=remount-ro    0    0
/dev/sdb1    /home    ntfs    rw,errors=remount-ro    0    0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.023502350 = 473.545379840  boot/grub/core.img                             1
 449.016834259 = 482.128154624  boot/grub/grub.cfg                             1
 441.022006989 = 473.543774208  boot/initrd.img-2.6.32-5-amd64                 1
 441.010738373 = 473.531674624  boot/vmlinuz-2.6.32-5-amd64                    1
 441.022006989 = 473.543774208  initrd.img                                     1
 441.010738373 = 473.531674624  vmlinuz                                        1

```

---

### Post by YesWeCan on 2011-08-29
Your install looks ok at first glance.
If you boot the sda drive it boots into Windows ok and if you boot the sdb drive it just hangs, is that right?

How does it hang, as it were? What exactly do you see on the screen? Do you get a grub rescue prompt or something else?

How old is your HP computer?

---

### Post by Mark Phelps on 2011-08-29
Since this appears to be Mint, have you checked in with the Mint forums to see what they have to say?

---

### Post by oldfred on 2011-08-29
With MBR(msdos) partitioning, do not mix up a windows hidden boot/recovery partition with an Ubuntu /boot partition. That cannot be the same and in fact most installation of Ubuntu files into windows damages Windows. 

You do not show a /boot partition and for most desktops you do not need one. Just /(root) and swap is the standard install but we often recommend a separate /home. If all your data will be in a shared data partition you may not need the separate partition for /home as it is tiny and very easy to backup before a new reinstall. 

Have you tried booting from sdb? And what error messages or screens do you get?

---

### Post by dr_shred on 2011-08-29
> **oldfred said:**
> With MBR(msdos) partitioning, do not mix up a windows hidden boot/recovery partition with an Ubuntu /boot partition. That cannot be the same and in fact most installation of Ubuntu files into windows damages Windows. 

You do not show a /boot partition and for most desktops you do not need one. Just /(root) and swap is the standard install but we often recommend a separate /home. If all your data will be in a shared data partition you may not need the separate partition for /home as it is tiny and very easy to backup before a new reinstall. 

Have you tried booting from sdb? And what error messages or screens do you get?

Here's what I tried
reinstalled ubuntu
remove disk, cr
get nothing, no errors printed to the screen as before, hung up
toggle power, which boots win7
insert ubuntu cd
boot ubuntu
run boot_info_script.sh
restart

tries to boot ubuntu with the following
printed to the screen and it hangs
(obviously, this is not in its entirety since
I had to copy it by hand)

```

...
CR
...
BUG unable to handle kernal paging request
...
RIP ...
RSP ...
RAX ...
RBP ...
...
Call Trace: ...
...
Code: ...
...
RIP ...
RSP ...
CR2: 00000000babd7e60
(this is where it hangs)

```toggle power
boots to win7

Reply to [YesWeCan]("http://ubuntuforums.org/member.php?u=934104")

```

If you boot the sda drive it boots into Windows ok and if you boot the sdb drive it just hangs, is that right?

-- The only way I can boot sdb it as described above: install ubuntu and restart, but it hangs.

How does it hang, as it were? What exactly do you see on the screen? Do you get a grub rescue prompt or something else?

-- See above.

How old is your HP computer?

-- About two weeks old

```reply to [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399")

```

Since this appears to be Mint, have you checked in with the Mint forums to see what they have to say?

-- Actually, it's both ubuntu and mint.  I may have done a dumb thing and installed
mint after ubuntu didn't work.  Ubuntu did the same this as described above before
I installed mint.

```reply to [oldfred]("http://ubuntuforums.org/member.php?u=852711")
```

With MBR(msdos) partitioning, do not mix up a windows hidden  boot/recovery partition with an Ubuntu /boot partition. That cannot be  the same and in fact most installation of Ubuntu files into windows  damages Windows. 

You do not show a /boot partition and for most desktops you do not need  one. Just /(root) and swap is the standard install but we often  recommend a separate /home. If all your data will be in a shared data  partition you may not need the separate partition for /home as it is  tiny and very easy to backup before a new reinstall. 

-- The first time I installed ubuntu, I accepted the default, which installed it on sdb1

Have you tried booting from sdb? And what error messages or screens do you get?

-- I don't know how to do this.  I did try modifying the bios boot order but I couldn't
put the second hd ahead of the first.

```Here is the current boot_info_script.sh
output

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Xfce Edition
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   953,497,599   953,290,752   7 NTFS / exFAT / HPFS
/dev/sda3         953,497,600   976,771,071    23,273,472   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   244,194,303   244,192,256   7 NTFS / exFAT / HPFS
/dev/sdb2         244,195,326   976,771,071   732,575,746   5 Extended
/dev/sdb5         968,579,072   976,771,071     8,192,000  82 Linux swap / Solaris
/dev/sdb6         488,388,608   960,382,975   471,994,368  83 Linux
/dev/sdb7         960,385,024   968,574,975     8,189,952  82 Linux swap / Solaris
/dev/sdb8         244,195,328   480,192,511   235,997,184  83 Linux
/dev/sdb9         480,194,560   488,376,319     8,181,760  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        961C03E41C03BDED                       ntfs       SYSTEM
/dev/sda2        F2487D6F487D3387                       ntfs       OS
/dev/sda3        2C0A19E30A19AB3A                       ntfs       HP_RECOVERY
/dev/sdb1        F6AC0FEBAC0FA4E9                       ntfs       DATA_DRIVE_1
/dev/sdb5        585f74b9-bd9f-4c32-8b9d-3a6759dbc864   swap       
/dev/sdb6        3cce2773-3d49-4ebe-8aa7-58a37c45ecac   ext4       
/dev/sdb7        9da01abf-b670-4852-aa15-7d67cbe59765   swap       
/dev/sdb8        de159de5-d983-4492-a797-057c2ffbf74f   ext4       
/dev/sdb9        ef0a21b2-e921-440f-aca2-3f5452e04ca0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set 961c03e41c03bded
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set 2c0a19e30a19ab3a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sdb6    /    ext4    rw,errors=remount-ro    0    0
/dev/sdb1    /home    ntfs    rw,errors=remount-ro    0    0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 441.023502350 = 473.545379840  boot/grub/core.img                             1
 449.016834259 = 482.128154624  boot/grub/grub.cfg                             1
 441.022006989 = 473.543774208  boot/initrd.img-2.6.32-5-amd64                 1
 441.010738373 = 473.531674624  boot/vmlinuz-2.6.32-5-amd64                    1
 441.022006989 = 473.543774208  initrd.img                                     1
 441.010738373 = 473.531674624  vmlinuz                                        1

=========================== sdb8/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos8)'
search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=de159de5-d983-4492-a797-057c2ffbf74f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=de159de5-d983-4492-a797-057c2ffbf74f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root de159de5-d983-4492-a797-057c2ffbf74f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 961C03E41C03BDED
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 2C0A19E30A19AB3A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro quiet
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root 3cce2773-3d49-4ebe-8aa7-58a37c45ecac
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=3cce2773-3d49-4ebe-8aa7-58a37c45ecac ro single
    initrd /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=de159de5-d983-4492-a797-057c2ffbf74f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=ef0a21b2-e921-440f-aca2-3f5452e04ca0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 201.024383545 = 215.848288256  boot/grub/grub.cfg                             1
 117.605468750 = 126.277910528  boot/initrd.img-2.6.38-8-generic               2
 212.628009796 = 228.307587072  boot/vmlinuz-2.6.38-8-generic                  1
 117.605468750 = 126.277910528  initrd.img                                     2
 212.628009796 = 228.307587072  vmlinuz                                        1

```

---

### Post by oldfred on 2011-08-29
All Linux system partitions have to use Linux formating not Windows. Windows does not support permissions & ownership which are fundemental to Linux.

/dev/sdb1    /home   [COLOR=Red] ntfs[/COLOR]    rw,errors=remount-ro    0    0

This may be why you cannot boot, and I did not think installer even let you do this.

---

### Post by Hakunka-Matata on 2011-08-30
/dev/sdb1    /home   [COLOR=Red] ntfs[/COLOR]    rw,errors=remount-ro    0    0

GOOD Find, oldfred, I read through that RESULTS.txt file a number of times and did not see that, and I thought I had patience.

---

### Post by dr_shred on 2011-08-31
> **oldfred said:**
> All Linux system partitions have to use Linux formating not Windows. Windows does not support permissions & ownership which are fundemental to Linux.

/dev/sdb1    /home   [COLOR=Red] ntfs[/COLOR]    rw,errors=remount-ro    0    0

This may be why you cannot boot, and I did not think installer even let you do this.

So what can I do to fix it?

I was thinking about deleting the sdb partitions alltogether and starting from scratch with a manual installation.  I downloaded the gparted tool and will start experimenting with that.

What I don't understand is:

Why doesn't the ubuntu installer simply put the correct partitions on sda like it would if there was only one hard drive?

If ubuntu is installed on sdb, with win 7 on sda, does this create confusion for the boot loader?

If I do a manual install, do I do it on sda or sdb?

---

### Post by oldfred on 2011-08-31
If you understand partitions a little I always suggest partitioning in advance. Then do manual install so you can also choose which drive's MBR to install the grub2 boot loader into. Then set BIOS to boot that drive. Some also suggest unplugging the Windows drive so then you do not have to worry about grub installing to the wrong place.

You are showing multiple Linux & swap partitions, so have you tried to use automatic install multiple times? After partitions are created it is better to reuse the partitions, but you have to use manual install. Delete the multiple Linux partitions and create one set of / (root), /home, & swap partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Herman has lots of detail if you are interested.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by YesWeCan on 2011-09-01
It looks to me like your Ubuntu installation is fine. But the Grub in sdb's MBR area is associated with your Mint OS rather than Ubuntu. So I think if you just reinstall Grub to reference Ubuntu it will boot Ubuntu ok.

boot Ubuntu live CD
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

When you boot sdb you will get a grub menu with choice of Ubuntu and Mint. Mint probably wont boot until you sort a couple of things out in its fstab file. One is removing the mounting of sdb1 as /home for reasons already stated. You can still mount sdb1 but at some other, benign mount point. Also, the entries for root and swap will be better off using UUID numbers (which can be found from the blkid list).


If I were you I'd keep my sda drive Windows only. Don't start mixing Linux and Windows on the same drive. Don't install grub to sda.

---

### Post by dr_shred on 2011-09-05
> **YesWeCan said:**
> It looks to me like your Ubuntu installation is fine. But the Grub in sdb's MBR area is associated with your Mint OS rather than Ubuntu. So I think if you just reinstall Grub to reference Ubuntu it will boot Ubuntu ok.

boot Ubuntu live CD
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

When you boot sdb you will get a grub menu with choice of Ubuntu and Mint. Mint probably wont boot until you sort a couple of things out in its fstab file. One is removing the mounting of sdb1 as /home for reasons already stated. You can still mount sdb1 but at some other, benign mount point. Also, the entries for root and swap will be better off using UUID numbers (which can be found from the blkid list).


If I were you I'd keep my sda drive Windows only. Don't start mixing Linux and Windows on the same drive. Don't install grub to sda.

Did as you suggested, so now, the menu with the
different oses comes up and I can boot ubuntu and
win 7.  Haven't tried mint yet.

So it looks like it's working!

Oh, one more thing:  I had to disable the sata0 drive, the win 7 drive, from the
boot order in the bios, otherwise, ubuntu hung up like before.  This, I think,
simply removes the windows loader on sata0 in favor of grub on sata1.
Grubs detects all the operating systems installed, including mint and they
all boot just fine.

Many thanks

---

### Post by Mark Phelps on 2011-09-05
> **dr_shred said:**
> Oh, one more thing:  I had to disable the sata0 drive, the win 7 drive, from the
boot order in the bios, otherwise, ubuntu hung up like before.  This, I think,
simply removes the windows loader on sata0 in favor of grub on sata1.

Why not just CHANGE the boot order of your hard drives in the BIOS?  Most modern BIOS's have two entries:
1) Order of devices (i.e., CDROM, Hard Drive, etc)
2) Order of Hard Drives.

Change the second so that your Ubuntu drive is at the top of the list (normally done by tabbing to the drive and hitting the "+" key to move it to the top of the list). Then, when you reboot, it will use that instead of the Windows drive.

---

### Post by dr_shred on 2011-09-06
> **Mark Phelps said:**
> Why not just CHANGE the boot order of your hard drives in the BIOS?  Most modern BIOS's have two entries:
1) Order of devices (i.e., CDROM, Hard Drive, etc)
2) Order of Hard Drives.

Change the second so that your Ubuntu drive is at the top of the list (normally done by tabbing to the drive and hitting the "+" key to move it to the top of the list). Then, when you reboot, it will use that instead of the Windows drive.

I tried that but I couldn't get it to work.  I'll give it another shot.

---

### Post by dr_shred on 2011-09-06
> **Mark Phelps said:**
> Why not just CHANGE the boot order of your hard drives in the BIOS?  Most modern BIOS's have two entries:
1) Order of devices (i.e., CDROM, Hard Drive, etc)
2) Order of Hard Drives.

Change the second so that your Ubuntu drive is at the top of the list (normally done by tabbing to the drive and hitting the "+" key to move it to the top of the list). Then, when you reboot, it will use that instead of the Windows drive.

O.K.  I tried it again and it worked, i.e. both hds are enabled and sata1 precedes sata0 in the
boot order.  I may have had a brief moment of mental abstraction, perhaps due to the primitive
gui of the bios.

Many Thanks to

[YesWeCan]("http://ubuntuforums.org/member.php?u=934104")
[Mark Phelps]("http://ubuntuforums.org/member.php?u=311399")
[oldfred]("http://ubuntuforums.org/member.php?u=852711")
[Hakunka-Matata]("http://ubuntuforums.org/member.php?u=735950")

Sincerely,

dr_shred

---

### Post by drkPu1se on 2011-09-06
> **oldfred said:**
> If you understand partitions a little I always suggest partitioning in advance. Then do manual install so you can also choose which drive's MBR to install the grub2 boot loader into. Then set BIOS to boot that drive. Some also suggest unplugging the Windows drive so then you do not have to worry about grub installing to the wrong place.

You are showing multiple Linux & swap partitions, so have you tried to use automatic install multiple times? After partitions are created it is better to reuse the partitions, but you have to use manual install. Delete the multiple Linux partitions and create one set of / (root), /home, & swap partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Herman has lots of detail if you are interested.
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I've been using ubuntu for about 9 months now and never knew what the use for swap was except that it is needed for installation. I have Natty installed with Unity removed. Everything is peachy keen except where it excels in graphics because it is a gaming rig, it is rather slow generally. Sure 1 gig of ram is horrible when you want to play games, but atm I cant afford more and when I run windows and play video games it balls out rocks. I know that it doesnt take much ram to run a game and its alot about the graphics card but my rig takes about 3-5 minutes to load Chromium. once thats done it goes okay. well back to swap. ive always used no more than 512 mb for swap space. if im gathering this correctly should i increase this space used? and will this cure some of the general slowness? i do plan on adding more ram later on down the road when i receive another job.

---

### Post by YesWeCan on 2011-09-06
It looks to me like you have loads of swap space. You have 3 partitions of 4GB each.

If you boot your OS and run
[COLOR="DarkSlateBlue"]swapon -s[/COLOR]

It will tell you the amount of swap space available in kB.

---

