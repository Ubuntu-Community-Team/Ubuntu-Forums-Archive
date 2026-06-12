---
title: "W7/Ubuntu 11.04 dual boot"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by Coffeh! on 2011-08-26
I recently switched from Windows to ubuntu, and I loved it. The only problem is getting games to work on Ubuntu. Even with wine, there are some games I want to play that I can't get to work. So I researched the dual boot thing, the only problem is my hard drive is only 275 GB, and with 2 OS, games, and music  its going to be drained pretty quickly. So I was wondering if I could keep my current hard drive as ubuntu, but just add another hard drive to install windows onto? (I think they're SATA hard drives)
Thanks

---

### Post by Vietred on 2011-08-26
Yes, of course you can. But you may have to make Windows HDD as master and Ubuntu HDD as slave so Windows won't complain. Just install Windows in the new HDD then re-install grub for dual boot later.

---

### Post by Coffeh! on 2011-08-26
Ok, sounds good, thanks. But i'm just curious, in what way does windows "complain" if I don't reinstall grub o.o

---

### Post by oldfred on 2011-08-26
If you have PATA/IDE your BIOS may only boot from sda or the primary master. If SATA you can set boot drive in BIOS and windows prefers to be sda or a lower port number. If installed to sdb, it may put its boot loader and smal system boot/recover partition on sda. So best to disconnect Ubuntu drive, install windows, reinstall Ubuntu drive and set it to boot in BIOS. Ubuntu should boot ok as it uses UUIDs not device like /dev/sda1 anymore to boot or grub also has search by UUID.
Then run this and it should find windows and let you boot either drive.
sudo update-grub 

If you end up installing Ubuntu after windows:
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Always backup your data before making any system changes. And it is best to have a Ubuntu liveCD and windows repairCD of the current versions of every system installed.

---

### Post by dr_shred on 2011-08-26
I have a similar problem: an hp desktop with two 250G HDs with Win 7.  When I try to install
ubuntu it hangs up on restart if I used the default settings which, I believe installs ubuntu to
sb1, i.e. the second HD.

I've done a lot of research in various forums on how to install different partitions, but there
doesn't appear to be a definitive description on how to do this without, as you suggest,
disconnecting one of the HDs.

I've tried creating the /. boot, swap and /home or /data partitions manually on sb1, but it always
boots Win 7.

This is not a trivial task by any means and it would be awesome for a detailed set
of instructions to do this.

---

### Post by Hakunka-Matata on 2011-08-26
> **dr_shred said:**
> I have a similar problem: an hp desktop with two 250G HDs with Win 7.  When I try to install
ubuntu it hangs up on restart if I used the default settings which, I believe installs ubuntu to
sb1, i.e. the second HD.

I've done a lot of research in various forums on how to install different partitions, but there
doesn't appear to be a definitive description on how to do this without, as you suggest,
disconnecting one of the HDs.

I've tried creating the /. boot, swap and /home or /data partitions manually on sb1, but it always
boots Win 7.

This is not a trivial task by any means and it would be awesome for a detailed set
of instructions to do this.

It would be a good idea to start your own thread, that'll get you help faster, and it's sorta [I]the thing to do.

[/I]That being said, what are your conditions:  It looks like you are able to boot to a liveCD?  True?

[LIST]
[*]install ubuntu to it's own partition, i.e. NOT a Wubi install?
[*]do you have a liveCD or USB already burned?
[*]Can you boot using the liveCD?
[/LIST]
Oh, and welcome to the forums.

---

### Post by Coffeh! on 2011-08-27
First of, thanks for all the helpful replies =D
So going of off what oldfred said, basically I can just disconnect my ubuntu drive and replug it in and set it to bios, and there will be no problems? (Sorry for asking twice, just want to clarify as I'm kinda new to the whole ubuntu thing)

---

### Post by Mark Phelps on 2011-08-27
> **Coffeh! said:**
> First of, thanks for all the helpful replies =D
So going of off what oldfred said, basically I can just disconnect my ubuntu drive and replug it in and set it to bios, and there will be no problems? (Sorry for asking twice, just want to clarify as I'm kinda new to the whole ubuntu thing)

NO ... that's not what oldfred said ...

He said to disconnect your Ubuntu drive, THEN reinstall Windows on the other drive (the one remaining connected), THEN reconnect the Ubuntu drive -- but boot from the Ubuntu drive, NOT from the Windows drive, THEN run "sudo update-grub" from a terminal inside Ubuntu.

Obviously, more is involved than just unplugging and replugging drives.

---

### Post by oldfred on 2011-08-27
If your BIOS lets you choose boot drive that is the safest way. Disconnect windows drive and install to Ubuntu drive and reconnect windows drive. Then sudo update-grub will find windows and add it to menu.

Only if you use manual install do you get a choice on where to install grub2's boot loader otherwise it defaults to sda which for most with two drives do not want.

---

### Post by Coffeh! on 2011-08-27
> **Mark Phelps said:**
> NO ... that's not what oldfred said ...

He said to disconnect your Ubuntu drive, THEN reinstall Windows on the other drive (the one remaining connected), THEN reconnect the Ubuntu drive -- but boot from the Ubuntu drive, NOT from the Windows drive, THEN run "sudo update-grub" from a terminal inside Ubuntu.

Obviously, more is involved than just unplugging and replugging drives.

Ah I see. Sorry about my post, it wasn't complete. Basically I'm getting a new HDD that isnt connected to my cpu yet without an os currently on it. But I get what I have to do now. Thanks for the help, I'll go ahead and mark "solved"

---

### Post by dr_shred on 2011-08-27
Yes, I'm able to boot from the ubuntu image cd

The installer installs ubuntui but on restart it hangs.  I think it installs it on
the second 250G drive.

If you mean by liveCD, the cd with the .iso file burned into it yes

Yes, I can boot from the liveCD if it refers as mentioned above.

The manual partition manager comes up just fine, but it doesn't
allow me to place the required directories - /, /boot, swap and /home
on sa1, where, I assume, the win 7 boot sector is.

I don't think you can set up a separate ubuntu boot sector on sb1
that the bios will detect, can you?

---

### Post by Hakunka-Matata on 2011-08-27
> **dr_shred said:**
> Yes, I'm able to boot from the ubuntu image cd

The installer installs ubuntui but on restart it hangs.  I think it installs it on
the second 250G drive.

If you mean by liveCD, the cd with the .iso file burned into it yes

Yes, I can boot from the liveCD if it refers as mentioned above.

The manual partition manager comes up just fine, but it doesn't
allow me to place the required directories - /, /boot, swap and /home
on sa1, where, I assume, the win 7 boot sector is.

I don't think you can set up a separate ubuntu boot sector on sb1
that the bios will detect, can you?


[LIST]
[*]Boot to ubuntu liveCD, choose "try ubuntu without installing"
[*]open a Terninal window and input
[*]```
sudo fdisk -lu
```
[*]post the output
[/LIST]
So we can see how your disks are partitioned now,

---

### Post by oldfred on 2011-08-27
You definitely do not install any parts to Ubuntu into Windows partitions, or you damage windows. A windows boot partition is just for Windows. Again if you BIOS lets you choose drives you disconnect one or the other to install so nothing is on the other drive. Only if you BIOS only lets you boot from sda, then you have to install grub2's boot loader to the MBR, not to any partition.

You do not need and should not have a /boot partition for Ubuntu. Just leave the /boot as a folder inside the / (root) partition. Having a separate /home does offer some advantages.

---

### Post by dr_shred on 2011-08-28
> **Hakunka-Matata said:**
> 
[LIST]
[*]Boot to ubuntu liveCD, choose "try ubuntu without installing"
[*]open a Terninal window and input
[*]```
sudo fdisk -lu
```
[*]post the output
[/LIST]
So we can see how your disks are partitioned now,

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

---

### Post by Hakunka-Matata on 2011-08-28
> **dr_shred said:**
> I have a similar problem: an hp desktop with two 250G HDs with Win 7.  When I try to install
ubuntu it hangs up on restart if I used the default settings which, I believe installs ubuntu to
sb1, i.e. the second HD.

I've done a lot of research in various forums on how to install different partitions, but there
doesn't appear to be a definitive description on how to do this without, as you suggest,
disconnecting one of the HDs.

I've tried creating the /. boot, swap and /home or /data partitions manually on sb1, but it always
boots Win 7.

This is not a trivial task by any means and it would be awesome for a detailed set
of instructions to do this.

You don't need to create any more partitions at this time, you already have all the necessary partitions on **sdb:  **You may already have ubuntu installed, but you can't get to it because the bootloader is not installed, or configured correctly, or you may have to change the 'boot first' option in BIOS.  
[B] 
sdb2: Extended ~125GiB[/B]
logical partitions inside of **sdb2**: (Your Linux/Ubuntu partitions)[INDENT][B]sdb5: Linux swap - ~ 2GiB
sdb6: Linux System - ~ 120GiB
sdb7: [/B][B]Linux swap - ~ 2GiB

[/B][/INDENT]next, please:
Post the output of ```
sudo blkid
```Enclose the output between Code tags, so it maintains it's format, much easier to read that way.
#highlight/select the output, then click on the Code tag format icon '**#'**

---

### Post by dr_shred on 2011-08-28
> **Hakunka-Matata said:**
> You don't need to create any more partitions at this time, you already have all the necessary partitions on **sdb:  **You may already have ubuntu installed, but you can't get to it because the bootloader is not installed, or configured correctly, or you may have to change the 'boot first' option in BIOS.  
[B] 
sdb2: Extended ~125GiB[/B]
logical partitions inside of **sdb2**: (Your Linux/Ubuntu partitions)[INDENT][B]sdb5: Linux swap - ~ 2GiB
sdb6: Linux System - ~ 120GiB
sdb7: [/B][B]Linux swap - ~ 2GiB

[/B][/INDENT]next, please:
Post the output of ```
sudo blkid
```Enclose the output between Code tags, so it maintains it's format, much easier to read that way.
#highlight/select the output, then click on the Code tag format icon '**#'**

```
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

---

### Post by Hakunka-Matata on 2011-08-28
OK, that looks good.  There is an extra swap partition on sdb, but that's not a problem.  Next, please download and run boot_info_script.  The link is in my signature.  Read the "How to instructions" on their website and post the resulting RESULTS.txt file between code tags in a reply.  After the RESULTS.txt file is created open it with a double click, hightlight the ENTIRE file, copy it.  Then past that into the reply.  Highlight it again, then click on the # icon, to enclose it in code tags.

We'll see if you have Grub2 installed, etc. etc. etc.

---

### Post by dr_shred on 2011-08-28
> **Hakunka-Matata said:**
> OK, that looks good.  There is an extra swap partition on sdb, but that's not a problem.  Next, please download and run boot_info_script.  The link is in my signature.  Read the "How to instructions" on their website and post the resulting RESULTS.txt file between code tags in a reply.  After the RESULTS.txt file is created open it with a double click, hightlight the ENTIRE file, copy it.  Then past that into the reply.  Highlight it again, then click on the # icon, to enclose it in code tags.

We'll see if you have Grub2 installed, etc. etc. etc.

boot_info_script.sh command line
```

ubuntu@ubuntu:~$ sudo bash boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdb7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/".

ubuntu@ubuntu:~$

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

### Post by Hakunka-Matata on 2011-08-28
OK dr_shred;  The RESULTS.txt file is posted correctly and it's easy to navigate that way.  Thanks. We've learned a few things today and I'm probably close to the limit of my abilities to help beyond here. RESULTS.txt is confusing to me, too much stuff I don't understand well enough in this particular one.  I see in sdb6 that "Linux Mint Xfce Edition" is listed.  I don't really want to advise you to do anything more at this point, except that you might want to try changing your BIOS boot option to boot from the second hard drive.  That might boot Linux Mint, if that's what you want?

You'll get better help now if you start a new thread, call it Window7 - Linux dual boot.  If you want to use Ubuntu it will have to be installed, it is not installed now according to the information in RESULTS.txt.  What do you think?  btw, give yourself some credit for learning how to navigate this forum and post results, screenshots, etc.  That helps.

In your first post on the new thread if that's what you do, include the RESULTS.txt information.

---

### Post by Hakunka-Matata on 2011-08-28
dr_shred;
excuse me, I had you confused with another thread I'm working.  If some or most of my reply doesn't make sense, that's the reason.  sorry.

---

### Post by dr_shred on 2011-08-29
> **Hakunka-Matata said:**
> OK dr_shred;  The RESULTS.txt file is posted correctly and it's easy to navigate that way.  Thanks. We've learned a few things today and I'm probably close to the limit of my abilities to help beyond here. RESULTS.txt is confusing to me, too much stuff I don't understand well enough in this particular one.  I see in sdb6 that "Linux Mint Xfce Edition" is listed.  I don't really want to advise you to do anything more at this point, except that you might want to try changing your BIOS boot option to boot from the second hard drive.  That might boot Linux Mint, if that's what you want?

You'll get better help now if you start a new thread, call it Window7 - Linux dual boot.  If you want to use Ubuntu it will have to be installed, it is not installed now according to the information in RESULTS.txt.  What do you think?  btw, give yourself some credit for learning how to navigate this forum and post results, screenshots, etc.  That helps.

In your first post on the new thread if that's what you do, include the RESULTS.txt information.

Your help is greatly appreciated.

Mille Grazie!

dr_shred

---

