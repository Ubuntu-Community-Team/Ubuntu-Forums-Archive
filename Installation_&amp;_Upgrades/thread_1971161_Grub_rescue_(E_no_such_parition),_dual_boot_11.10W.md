---
title: "Grub rescue (E: no such parition), dual boot 11.10/Win7, all partitions are missing."
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by 1grouchy on 2012-05-02
I have a problem with potential loss of very important data for me, so please help me if you can.

After reistalling Ubuntu 11.10 I got this message:
No such partition.

I messed up a MBR while reinstalling Ubuntu 11.10. Think that I was install bootloader on wrong partition and now Ubuntu Live CD and Windows installation DVD see my HDD as unparition space and offer me format. All my partitions are missing!!!

I search for solution for three days now to recover my data from HDD, and in one moment with Ubuntu live USB I manage to mount all partition (there is a 6 of them - Win and Ubuntu).

Think that I was install grub-pc (from one thread but I can't find it now), run some command and then all my partitions was able to see in nautilus.

After a reboot, all partitions are missing again, and now I can't find thread thats help me.

Is there anyone who can help me to solve this problem?

Thanks in advance.

---

### Post by kc1di on 2012-05-02
> **1grouchy said:**
> I have a problem with potential loss of very important data for me, so please help me if you can.

After reistalling Ubuntu 11.10 I got this message:
No such partition.

I messed up a MBR while reinstalling Ubuntu 11.10. Think that I was install bootloader on wrong partition and now Ubuntu Live CD and Windows installation DVD see my HDD as unparition space and offer me format. All my partitions are missing!!!

I search for solution for three days now to recover my data from HDD, and in one moment with Ubuntu live USB I manage to mount all partition (there is a 6 of them - Win and Ubuntu).

Think that I was install grub-pc (from one thread but I can't find it now), run some command and then all my partitions was able to see in nautilus.

After a reboot, all partitions are missing again, and now I can't find thread thats help me.

Is there anyone who can help me to solve this problem?

Thanks in advance.

Please see this page download and burn a cd of boot repair.
follow instructions and I think you beable to get your system back. 

The old adage BACK UP BEFORE Install would have been good though :)

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by darkod on 2012-05-02
Leave boot-repair for later, if you are really in trouble with the partition table it will do no good.

First, boot into ubuntu live mode and post the result of:
sudo fdisk -l (small L)

Then we will see what is best.

---

### Post by 1grouchy on 2012-05-02
I try that already my friend, but to manage that Ubuntu must see my HDD first. Boot-Repair tool should be my second step, after I manage to see partitions in nautilus again as I mentioned in previous post.
I try something with grub-pc, with install it and some command and that worked, but now I can't remember what I was done in that moment. I'm trying to fix this for days now, my brain is overheating now. :confused:

HAHAHAHAHA....

I can't belive what is happening now. I downloaded Boot Info Script to post Results of output here, as I click to find him in nautilus, in left panel I can see again all my partitions. What is going on here, ubuntu play games with me?!?!?!

 I try Boot-Repair now again but he detected my 64bit system and don't want to perform any actions, just stop with info messages:
64bits detected. Please use this software in a 64bits session. This will enable this feature.
and
Something like, bla bla, see ya soon.

Now I'm stuck again, I can't reboot and start 64bit Live version because I will lose partitions again. Oh Ubuntu, you...!

---

### Post by 1grouchy on 2012-05-02
@Darko

Now I can see my partitions, this is outputs to preview:


[COLOR=Gray]-------------------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a695750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   215543807   107668480    7  HPFS/NTFS/exFAT
/dev/sda3       596602880   625141759    14269440   83  Linux
/dev/sda4       215544166   596602879   190529357    f  W95 Ext'd (LBA)
/dev/sda5       215544168   539960714   162208273+   7  HPFS/NTFS/exFAT
/dev/sda6       539961344   588789759    24414208   83  Linux
/dev/sda7       588791808   596602879     3905536   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     7831551     3911744    c  W95 FAT32 (LBA)
-------------------------------------------------------------------------------------------------------------------------[/COLOR]

and from Boot Info Script
[COLOR=Gray]-------------------------------------------------------------------------------------------------------------------------
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 610300528 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/boot/grub on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:  Syslinux looks at sector 1469344 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   215,543,807   215,336,960   7 NTFS / exFAT / HPFS
/dev/sda3         596,602,880   625,141,759    28,538,880  83 Linux
/dev/sda4         215,544,166   596,602,879   381,058,714   f W95 Extended (LBA)
/dev/sda5         215,544,168   539,960,714   324,416,547   7 NTFS / exFAT / HPFS
/dev/sda6         539,961,344   588,789,759    48,828,416  83 Linux
/dev/sda7         588,791,808   596,602,879     7,811,072  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        22761E73761E4845                       ntfs       System Reserved
/dev/sda2        9C0CF8AE0CF88514                       ntfs       
/dev/sda3        5350eeb4-4388-4759-b749-73717281b983   ext4       
/dev/sda5        01CA8DB0E6FB7480                       ntfs       DataStoraga
/dev/sda6        5c38be76-a499-459b-ac6e-af030f470459   ext4       
/dev/sda7        8d157018-0bcc-4347-ab73-68c5128d94b4   swap       
/dev/sdc1        B4C8-43A2                              vfat       KINGSTON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/DataStoraga       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5350eeb4-4388-4759-b749-73717281b983 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5350eeb4-4388-4759-b749-73717281b983 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 5350eeb4-4388-4759-b749-73717281b983
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 22761E73761E4845
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=5350eeb4-4388-4759-b749-73717281b983 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5c38be76-a499-459b-ac6e-af030f470459 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=8d157018-0bcc-4347-ab73-68c5128d94b4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 291.013996124 = 312.473899008  boot/grub/core.img                             1
 296.704563141 = 318.584098816  boot/grub/grub.cfg                             1
 286.112411499 = 307.210862592  boot/initrd.img-3.0.0-12-generic               2
 286.852279663 = 308.005289984  boot/vmlinuz-3.0.0-12-generic                  1
 286.112411499 = 307.210862592  initrd.img                                     2
 286.852279663 = 308.005289984  vmlinuz                                        1

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 23 34 56 13 00 fe  |..........#4V...|
000001d0  ff ff 05 fe ff ff 25 34  56 13 75 12 e9 02 00 00  |......%4V.u.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
[/COLOR][COLOR=Gray]-------------------------------------------------------------------------------------------------------------------------[/COLOR]

Regards!

---

### Post by 1grouchy on 2012-05-02
I can see now from Script output that I was really mess up with boot loader when I was reinstalling Ubuntu, Grub 2 is installed on sda1 and sda3 but I don't know how to fix that. :(

---

### Post by darkod on 2012-05-02
The results look fine.

You can open /dev/sda1 and remove the /grldr files. They are not needed there.

The grub2 on the MBR looks installed correctly, but just in case you can do in live mode:
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That will reinstall it.

Don't worry about the grub2 installed on the /dev/sda3 partition. For ubuntu, it doesn't present an issue. It would, if it was installed as a boot sector on a windows partition.

PS. If the disk seems to be "missing" from time to time, you should run a SMART test on it. You can do it from ubuntu or probably with some windows tools too.

---

### Post by 1grouchy on 2012-05-02
I write this from my regular OS now!!!
Grub is back again! 

Thank you Darko, God bless you! :)

---

### Post by darkod on 2012-05-02
You are welcome. :)

Please mark the thread as Solved. You can do that in Thread Tools above the first post. Only you can do that because it's your thread.

---

