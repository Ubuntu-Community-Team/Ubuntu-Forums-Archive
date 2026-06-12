---
title: "Lost Write access to one of my Hard Disks."
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2011-11-08
Hello everyone :-)

I have recently upgraded to 11.10.
On my rig there were two HDs.  One 120GB and one 400GB.
I didn't want to format them, so during the installation I formated only the "/" partition and left the "/home" and the 2 HDs unformatted.

The two HDs I mounted them during installation under "/home/.../120GB" and "/home/.../400GB".  Where "..." is my username and it is EXACTLY the same as the one I had on 11.04.

However for some reason I have lost write access to those HDs.  Both disks where mounted correctly and I can see them mounted under my home folder.

I can read from the HDs, but I can't write on them.
1. Can someone please explain to me, why this happened?
2. Is there a way I can fix this?
3. Is there a way to avoid this in the future?  Maybe some special parameter during installation?

Thank you all.

ps.  The title of my thread is wrong.  It should have said W instead of R/W.  Problem is I can't change it.

---

### Post by 23dornot23d on 2011-11-08
If you boot from a LiveCD can you write to either of the hard drives .......

Also can you post the results of the boot info script as it may give people a lot more information to work with please .... follow the instructions in the link,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I personally have only come across the read write problem once ..... and it was due to a
disk being corrupt ......  a disk check is usually initiated though and it should drop into 
maintainance mode to check the filesystem ...... usually says run fsck manually too.

But the more info you can give about the disks the better.

---

### Post by Ifaistos on 2011-11-08
I was under the impression that this would be something very simple, like changing the owner of the hard disks or something.

I thought that for some reason the O/S thinks that I am not allowed to write to the HDs because I am not the owner.

Could it be smt like that?
I know that both HDs work just fine.

Thanks

---

### Post by nothingspecial on 2011-11-08
> **Ifaistos said:**
> 

ps.  The title of my thread is wrong.  It should have said W instead of R/W.  Problem is I can't change it.

Fixed :)

---

### Post by 23dornot23d on 2011-11-08
Just type this in a terminal and give the result please ..... in  lower case (LS / -L) 
as below ......
[B]
ls / -l


it should give a output similar to below ..... please post it ...... ty 

[/B]> 
keith@debianmint ~ $ ls / -l
total 92
drwxr-xr-x   2 root root  4096 Aug 10 03:48 TARGET
drwxr-xr-x   2 root root  4096 Aug 11 17:09 bin
drwxr-xr-x   5 root root  4096 Aug 10 15:25 boot
drwxr-xr-x  15 root root  3680 Nov  8 13:57 dev
drwxr-xr-x 159 root root 12288 Nov  8 13:57 etc
drwxr-xr-x   5 root root  4096 Aug  2 03:09 home
lrwxrwxrwx   1 root root    32 Aug  1 02:21 initrd.img -> /boot/initrd.img-3.0.0-1-686-pae
lrwxrwxrwx   1 root root    33 Jul 31 03:11 initrd.img.old -> /boot/initrd.img-2.6.39-2-686-pae
drwxr-xr-x  19 root root  4096 Aug 11 17:10 lib
drwx------   2 root root  4096 Aug  4  2010 lost+found
drwxr-xr-x  18 root root  4096 Nov  8 13:57 media
drwxr-xr-x   2 root root  4096 Jul 31 20:01 mnt
drwxr-xr-x   5 root root  4096 Jul 31 03:03 opt
dr-xr-xr-x 160 root root     0 Nov  8 13:56 proc



---

### Post by coffeecat on 2011-11-08
@Ifaistos, first...

> **23dornot23d said:**
> Also can you post the results of the boot info script as it may give people a lot more information to work with please .... follow the instructions in the link,

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

+1 to this. Please post the output of the boot script output. It will probably provide all the information needed to diagnose the problem.

However, let me try a long shot. Were these two drives formatted NTFS? Some people are reporting losing the ntfs-3g read-write driver during an upgrade. I believe the underlying reason is a bit more complicated, but if you have lost the ntfs-3g driver, all ntfs partitions will become read-only. Check to see if ntfs-3g is installed and if not install it. If you do need to install ntfs-3g, it will remove ntfsprogs. That's OK. The version of ntfs-3g in 11.10 now includes all the functionality of ntfsprogs.

---

### Post by Ifaistos on 2011-11-08
This is for the 400GB


total 96
drwxr-xr-x   2 root root  4096 2011-10-28 19:27 bin
drwxr-xr-x   3 root root  4096 2011-10-28 19:28 boot
drwxr-xr-x   2 root root  4096 2011-10-28 16:18 cdrom
drwxr-xr-x  14 root root  4560 2011-11-07 19:28 dev
drwxr-xr-x 141 root root 12288 2011-11-07 19:28 etc
drwxr-xr-x   8 root root  4096 2011-10-09 10:31 home
lrwxrwxrwx   1 root root    32 2011-10-28 16:24 initrd.img -> boot/initrd.img-3.0.0-12-generic
drwxr-xr-x  21 root root  4096 2011-10-28 20:53 lib
drwxr-xr-x   4 root root  4096 2011-10-28 20:49 lib32
drwxr-xr-x   2 root root  4096 2011-10-12 17:27 lib64
drwx------   2 root root 16384 2011-10-28 16:16 lost+found
drwxr-xr-x   4 root root  4096 2011-11-07 19:28 media
drwxr-xr-x   2 root root  4096 2011-10-09 10:31 mnt
drwxr-xr-x   3 root root  4096 2011-10-28 19:20 opt
dr-xr-xr-x 192 root root     0 2011-11-05 07:31 proc
drwx------   6 root root  4096 2011-11-05 14:40 root
drwxr-xr-x  20 root root   760 2011-11-05 07:32 run
drwxr-xr-x   2 root root  4096 2011-10-28 19:28 sbin
drwxr-xr-x   2 root root  4096 2011-06-21 21:45 selinux
drwxr-xr-x   2 root root  4096 2011-10-12 17:26 srv
drwxr-xr-x  13 root root     0 2011-11-05 07:31 sys
drwxrwxrwt  17 root root  4096 2011-11-08 16:17 tmp
drwxr-xr-x  11 root root  4096 2011-10-28 16:45 usr
drwxr-xr-x  13 root root  4096 2011-11-05 00:38 var
lrwxrwxrwx   1 root root    29 2011-10-28 16:24 vmlinuz -> boot/vmlinuz-3.0.0-12-generic

And this is for the 120GB


total 96
drwxr-xr-x   2 root root  4096 2011-10-28 19:27 bin
drwxr-xr-x   3 root root  4096 2011-10-28 19:28 boot
drwxr-xr-x   2 root root  4096 2011-10-28 16:18 cdrom
drwxr-xr-x  14 root root  4560 2011-11-07 19:28 dev
drwxr-xr-x 141 root root 12288 2011-11-07 19:28 etc
drwxr-xr-x   8 root root  4096 2011-10-09 10:31 home
lrwxrwxrwx   1 root root    32 2011-10-28 16:24 initrd.img -> boot/initrd.img-3.0.0-12-generic
drwxr-xr-x  21 root root  4096 2011-10-28 20:53 lib
drwxr-xr-x   4 root root  4096 2011-10-28 20:49 lib32
drwxr-xr-x   2 root root  4096 2011-10-12 17:27 lib64
drwx------   2 root root 16384 2011-10-28 16:16 lost+found
drwxr-xr-x   4 root root  4096 2011-11-07 19:28 media
drwxr-xr-x   2 root root  4096 2011-10-09 10:31 mnt
drwxr-xr-x   3 root root  4096 2011-10-28 19:20 opt
dr-xr-xr-x 192 root root     0 2011-11-05 07:31 proc
drwx------   6 root root  4096 2011-11-05 14:40 root
drwxr-xr-x  20 root root   760 2011-11-05 07:32 run
drwxr-xr-x   2 root root  4096 2011-10-28 19:28 sbin
drwxr-xr-x   2 root root  4096 2011-06-21 21:45 selinux
drwxr-xr-x   2 root root  4096 2011-10-12 17:26 srv
drwxr-xr-x  13 root root     0 2011-11-05 07:31 sys
drwxrwxrwt  17 root root  4096 2011-11-08 16:39 tmp
drwxr-xr-x  11 root root  4096 2011-10-28 16:45 usr
drwxr-xr-x  13 root root  4096 2011-11-05 00:38 var
lrwxrwxrwx   1 root root    29 2011-10-28 16:24 vmlinuz -> boot/vmlinuz-3.0.0-12-generic

---

### Post by Ifaistos on 2011-11-08
> **coffeecat said:**
> @Ifaistos, first...



+1 to this. Please post the output of the boot script output. It will probably provide all the information needed to diagnose the problem.

However, let me try a long shot. Were these two drives formatted NTFS? Some people are reporting losing the ntfs-3g read-write driver during an upgrade. I believe the underlying reason is a bit more complicated, but if you have lost the ntfs-3g driver, all ntfs partitions will become read-only. Check to see if ntfs-3g is installed and if not install it. If you do need to install ntfs-3g, it will remove ntfsprogs. That's OK. The version of ntfs-3g in 11.10 now includes all the functionality of ntfsprogs.

Hello coffeecat!

I think that you are right on the spot!
400GB is a NTFS drive and the 120GB is a drive formated by Ubuntu.  So I decided to check your theory.

I can't W on 400GB drive, but I can W on the 120GB!!

I will give it a try and let you know.
I just wanted to ask though... 
The procedure I followed, (which I describe above) it should have gone smoothly...right?

If it wasn't for this bug, I should have any problems... right?

---

### Post by coffeecat on 2011-11-08
> **Ifaistos said:**
> Hello coffeecat!

I think that you are right on the spot!
400GB is a NTFS drive and the 120GB is a drive formated by Ubuntu.  So I decided to check your theory.

I can't W on 400GB drive, but I can W on the 120GB!!

Well, I'm not so sure. :) In your previous post, your ls output for the two drives reveals lost+found folders in each. You don't find those in NTFS filesystems, only Linux ones.

We need the boot script output.

---

### Post by Hakunka-Matata on 2011-11-08
[Ifaistos]("http://ubuntuforums.org/member.php?u=45182"):

+ 1 on the boot_info script.  Here's a really crude script file you can run to make it all happen, except the actual posting of the RESULTS.txt file [B]contents.

```
sudo bash makeresults.sh
```[/B]

---

### Post by Ifaistos on 2011-11-08
Hello coffeecat :-)

I did what you said, and it was exactly like that.
I was missing the ntfs-3g and it was installed.  It did remove ntfsprogs.

Anyway, it is done!  I have regained access to the 400GB NTFS drive.

So you could say that the the problem is solved, but I will continue this thread since I want to make sure that everything is fine.

---

### Post by Ifaistos on 2011-11-08
Is this what you wanted Hakunka?


Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........Y.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1430808 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sde1 has 
                       629153584 sectors, but according to the info from 
                       fdisk, it has 781417601 sectors.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000 MB, 1000341504 bytes
31 heads, 62 sectors/track, 1016 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     1,952,751     1,952,690   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   117,194,174   117,194,112  83 Linux
/dev/sdd2         117,194,175   482,431,949   365,237,775  83 Linux
/dev/sdd3         482,431,950   488,392,064     5,960,115  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63   781,417,664   781,417,602   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63   234,436,544   234,436,482  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sdc1        2E5D-8A7F                              vfat       
/dev/sdd1        ee5dbc82-eba1-4e09-bacd-4cc4847c1260   ext4       
/dev/sdd2        f058ff8c-dea2-4487-bf2c-66246faf9253   ext4       
/dev/sdd3        13fccc89-1c14-433b-b96c-239a759c3b61   swap       
/dev/sde1        EACCD32ECCD2F433                       ntfs       400 GB
/dev/sdf1        a5c8e332-4be3-4d15-90ad-de5dd67a5ffb   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/2E5D-8A7F         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdd1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd2        /home                    ext4       (rw,commit=0)
/dev/sde1        /home/evans/400Gb        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdf1        /home/evans/120Gb        ext4       (rw,commit=0)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 ro recovery nomodeset 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=f058ff8c-dea2-4487-bf2c-66246faf9253 /home           ext4    defaults        0       2
# /home/evans/120Gb was on /dev/sdc1 during installation
UUID=a5c8e332-4be3-4d15-90ad-de5dd67a5ffb /home/evans/120Gb ext4    defaults        0       2
# /home/evans/400Gb was on /dev/sdb1 during installation
UUID=EACCD32ECCD2F433 /home/evans/400Gb ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by Hakunka-Matata on 2011-11-08
> **Ifaistos said:**
> Thank you Hakunka for the script :-)
These are the results.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........Y.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1430808 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sde1 has 
                       629153584 sectors, but according to the info from 
                       fdisk, it has 781417601 sectors.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000 MB, 1000341504 bytes
31 heads, 62 sectors/track, 1016 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     1,952,751     1,952,690   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   117,194,174   117,194,112  83 Linux
/dev/sdd2         117,194,175   482,431,949   365,237,775  83 Linux
/dev/sdd3         482,431,950   488,392,064     5,960,115  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63   781,417,664   781,417,602   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63   234,436,544   234,436,482  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sdc1        2E5D-8A7F                              vfat       
/dev/sdd1        ee5dbc82-eba1-4e09-bacd-4cc4847c1260   ext4       
/dev/sdd2        f058ff8c-dea2-4487-bf2c-66246faf9253   ext4       
/dev/sdd3        13fccc89-1c14-433b-b96c-239a759c3b61   swap       
/dev/sde1        EACCD32ECCD2F433                       ntfs       400 GB
/dev/sdf1        a5c8e332-4be3-4d15-90ad-de5dd67a5ffb   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/2E5D-8A7F         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdd1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd2        /home                    ext4       (rw,commit=0)
/dev/sde1        /home/evans/400Gb        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdf1        /home/evans/120Gb        ext4       (rw,commit=0)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 ro recovery nomodeset 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ee5dbc82-eba1-4e09-bacd-4cc4847c1260
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ee5dbc82-eba1-4e09-bacd-4cc4847c1260 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=f058ff8c-dea2-4487-bf2c-66246faf9253 /home           ext4    defaults        0       2
# /home/evans/120Gb was on /dev/sdc1 during installation
UUID=a5c8e332-4be3-4d15-90ad-de5dd67a5ffb /home/evans/120Gb ext4    defaults        0       2
# /home/evans/400Gb was on /dev/sdb1 during installation
UUID=EACCD32ECCD2F433 /home/evans/400Gb ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```
You're welcome, thanks for posting the script.  I've "quoted" your last reply and [B]added code tags to it.  This is how it should look.  Please edit your post and add the code tags.


[/B]

---

### Post by Ifaistos on 2011-11-08
I am attaching also two pictures.
This is the situation with my HDs.  I don't know why there are 2x120GB and 2x400GB.  The difference now is that the 400GB image is not locked.

I have also experienced smt else since the update, that may be related to this ... or maybe not..

I see that my HD access is almost constant.
In the beginning I thought that the memory was loaded and had to access the swap file.  However when I closed a couple of programs and memory was freed, it still did the same.

I see that my HD access led is being continuously (almost constantly) lit.
I am already searching for a couple of Geil PC3200 chips to increase my memory to 4GB.  I have installed the 64bit version so I will be able to access it all.

However I think that the constant accessing to the HD should be caused by smt else and not memory inadequacy. I think that 11.10 is much more demanding on my rig, and I have experienced significant decrease in the performance of my PC.

I will test it again when I find the memory and upgrade it to 4GB.  However I would like to explore the possibility that smt else is responsible for the deterioration of performance.  Any ideas?

---

### Post by Hakunka-Matata on 2011-11-08
sure the extra icons are not links?

please post output of ```
sudo fdisk -l && sudo sfdisk -luS"
```

---

### Post by Ifaistos on 2011-11-08
Disk /dev/sdc: 1000 MB, 1000341504 bytes
31 heads, 62 sectors/track, 1016 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed0fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     1952751      976345    c  W95 FAT32 (LBA)

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005db12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   117194174    58597056   83  Linux
/dev/sdd2       117194175   482431949   182618887+  83  Linux
/dev/sdd3       482431950   488392064     2980057+  82  Linux swap / Solaris

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34344e31

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   781417664   390708801    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e447c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   234436544   117218241   83  Linux

Disk /dev/sdc: 1016 cylinders, 31 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *        62   1952751    1952690   c  W95 FAT32 (LBA)
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1   *        63 117194174  117194112  83  Linux
/dev/sdd2     117194175 482431949  365237775  83  Linux
/dev/sdd3     482431950 488392064    5960115  82  Linux swap / Solaris
/dev/sdd4             0         -          0   0  Empty

Disk /dev/sde: 48641 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1            63 781417664  781417602   7  HPFS/NTFS/exFAT
/dev/sde2             0         -          0   0  Empty
/dev/sde3             0         -          0   0  Empty
/dev/sde4             0         -          0   0  Empty

Disk /dev/sdf: 14593 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdf1            63 234436544  234436482  83  Linux
/dev/sdf2             0         -          0   0  Empty
/dev/sdf3             0         -          0   0  Empty
/dev/sdf4             0         -          0   0  Empty

---

### Post by Ifaistos on 2011-11-08
> **Hakunka-Matata said:**
> sure the extra icons are not links?

please post output of ```
sudo fdisk -l && sudo sfdisk -luS"
```

How can I tell this?
I never created links to the drives.
If they are links.. can I simply delete them?

---

### Post by Hakunka-Matata on 2011-11-08
After blowing up the graphic and seeing **padlocks, **it most likely means the folder(s) were created with **root **as owner, not a problem.

Right click on the Icon(s), and click **permissions, **you'll understand then probably  

Re: deleting links:  Yes, you would be deleting nothing more than the link.

---

### Post by Ifaistos on 2011-11-08
Ok deleted them!!

I have no idea why they were created ...

I will mark this thread as solved and continue here...

[http://ubuntuforums.org/showthread.php?p=11438631#post11438631](http://ubuntuforums.org/showthread.php?p=11438631#post11438631)

regarding the constant HD access.

THANK YOU EVERYONE !!!

---

