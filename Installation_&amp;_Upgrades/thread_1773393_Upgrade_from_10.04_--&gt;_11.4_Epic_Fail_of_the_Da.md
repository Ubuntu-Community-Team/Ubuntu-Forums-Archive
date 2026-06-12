---
title: "Upgrade from 10.04 --&gt; 11.4 Epic Fail of the Day"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Destructo47 on 2011-06-02
I'm not happy with myself for disturbing a perfectly good Lucid install.

     I downloaded the iso image for 32-bit Natty via torrent. Burned it to a Memorex cd, and it installs fine at first. *However*, it did really screwed up. When I saw that it was best to go up one  version at a time, I wasn't really expecting results this horrendous if  I did (this saves time because my bandwidth is slower than a clogged  toilet). I directly upgraded via the live cd, and issues weren't  immediately apparent. More towards the end of the install, it warned me  that some programs would have to be installed manually. *Not a problem*, I thought. Boy, was I wrong.

     Turns out that one of those programs was the Wicd network client.  When I booted off the HD, it gave me a Unity notice telling me I don't  have the minimum requirements for it (Radeon 9250 Pro doesn't support  OpenGL 2.0 or above), and that I needed to select Ubuntu classic from  the options menu on the login screen. It seemed to do that  automatically, since my account loaded up a bit slow, but other than  that no problems.

     Looking through the applications menu, it looked like my computer  had been massacred. The normally 16 entry long list for Sound &  Video apps was reduced to 4. I tried connecting to the Internet with  Network Manager, but I seemed to be getting the "Network Manager Hates  Wireless" bug that I've seen floating around lately. I booted into the  Natty cd again, and made a Synaptic script for Wicd and some other apps I  wanted back. Saved it to a flash drive, and rebooted normally. The  'Boot from CD:" text appeared, but then was quickly followed by the  <grub-rescue> prompt. I don't know any commands for this  particular prompt, so I did a hard reset with the live cd in again.  Looking in GParted, the whole 292.33 GB of the ext4 partition that held  all of my data, the root folder, etc., was marked as "Unknown" under the  filesystem column.

     The rest of the hard drive is an extended partition with a  Linux-swap partition (5.76 GB), and 2.49 MB worth of unallocated space  (also there but not shown is the 1 KB partition table). I remember  splitting the main partition in 2 earlier, because I thought I would  need to do a fresh install, then copy files. That probably would have  been a better idea. My total data usage is easily over 50 GB, and I  don't have a flash drive that big. The hard drive is pretty new, not  even a year old. What can I do to install Natty without losing all of my  1's and 0's? I can't resize the partition with the unknown filesystem,  and there isn't enough room on the drive left over for a fresh install,  unless I can remove the extended partition.

I apologize for the wall of text above, but I would be forever grateful  to anyone who can save my computer from my stupidity. I have too much  saved to wipe it, and anyone I hire to fix it probably would end up  doing that anyways. :cry:

---

### Post by Hedgehog1 on 2011-06-02
Upgraders remorse? :(

Lets figure out what partitions have what data and what your options are.

From Ubuntu (or the LiveCD/LiveUSB, select 'TRY') please:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

**p.s. Do you want to return to 10.04.02 LTS?**

---

### Post by Destructo47 on 2011-06-02
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   452,438,015   452,437,953  83 Linux
/dev/sda2         613,056,512   625,141,759    12,085,248   5 Extended
/dev/sda5         613,060,608   625,141,759    12,081,152  82 Linux swap / Solaris
/dev/sda3         452,438,016   613,056,511   160,618,496  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        49a247f8-b5b3-4935-b255-4766319275ec   ext4       
/dev/sda3        be6c083b-f338-49db-85ca-6cf288190d69   ext4       
/dev/sda5        9c1c2fd1-5485-4907-9c13-61aa6b1ad8ae   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=49a247f8-b5b3-4935-b255-4766319275ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 49a247f8-b5b3-4935-b255-4766319275ec
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=49a247f8-b5b3-4935-b255-4766319275ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd7c946f-b80c-463c-b952-2f4af7e786d8 none            swap    sw              0       0
#
/dev/sda3 /home ext4 nodev,nosuid 0 2
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.810630322 = 0.870407680    boot/grub/core.img                             1
   0.805808544 = 0.865230336    boot/grub/grub.cfg                             1
   0.530433178 = 0.569548288    boot/initrd.img-2.6.31-14-generic              2
   0.640265942 = 0.687480320    boot/initrd.img-2.6.32-30-generic              1
  37.132308483 = 39.870512640   boot/initrd.img-2.6.32-31-generic              2
  10.043265820 = 10.783874560   boot/initrd.img-2.6.38-8-generic               2
   0.503654003 = 0.540794368    boot/vmlinuz-2.6.31-14-generic                 2
   0.742080212 = 0.796802560    boot/vmlinuz-2.6.32-30-generic                 2
   3.620986462 = 3.888004608    boot/vmlinuz-2.6.32-31-generic                 1
   1.366740704 = 1.467526656    boot/vmlinuz-2.6.38-8-generic                  1
  10.043265820 = 10.783874560   initrd.img                                     2
   1.366740704 = 1.467526656    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  23 21 2f 62 69 6e 2f 73  68 0a 77 67 65 74 20 2d  |#!/bin/sh.wget -|
00000010  63 20 68 74 74 70 3a 2f  2f 61 72 63 68 69 76 65  |c http://archive|
00000020  2e 75 62 75 6e 74 75 2e  63 6f 6d 2f 75 62 75 6e  |.ubuntu.com/ubun|
00000030  74 75 2f 70 6f 6f 6c 2f  6d 61 69 6e 2f 6b 2f 6b  |tu/pool/main/k/k|
00000040  64 65 34 6c 69 62 73 2f  6b 64 65 6c 69 62 73 35  |de4libs/kdelibs5|
00000050  2d 64 61 74 61 5f 34 2e  36 2e 32 2d 30 75 62 75  |-data_4.6.2-0ubu|
00000060  6e 74 75 34 5f 61 6c 6c  2e 64 65 62 0a 77 67 65  |ntu4_all.deb.wge|
00000070  74 20 2d 63 20 68 74 74  70 3a 2f 2f 61 72 63 68  |t -c http://arch|
00000080  69 76 65 2e 75 62 75 6e  74 75 2e 63 6f 6d 2f 75  |ive.ubuntu.com/u|
00000090  62 75 6e 74 75 2f 70 6f  6f 6c 2f 6d 61 69 6e 2f  |buntu/pool/main/|
000000a0  67 2f 67 63 63 2d 34 2e  35 2f 6c 69 62 67 66 6f  |g/gcc-4.5/libgfo|
000000b0  72 74 72 61 6e 33 5f 34  2e 35 2e 32 2d 38 75 62  |rtran3_4.5.2-8ub|
000000c0  75 6e 74 75 34 5f 69 33  38 36 2e 64 65 62 0a 77  |untu4_i386.deb.w|
000000d0  67 65 74 20 2d 63 20 68  74 74 70 3a 2f 2f 61 72  |get -c http://ar|
000000e0  63 68 69 76 65 2e 75 62  75 6e 74 75 2e 63 6f 6d  |chive.ubuntu.com|
000000f0  2f 75 62 75 6e 74 75 2f  70 6f 6f 6c 2f 6d 61 69  |/ubuntu/pool/mai|
00000100  6e 2f 6c 69 62 78 2f 6c  69 62 78 63 62 2f 6c 69  |n/libx/libxcb/li|
00000110  62 78 63 62 2d 72 61 6e  64 72 30 5f 31 2e 37 2d  |bxcb-randr0_1.7-|
00000120  32 75 62 75 6e 74 75 32  5f 69 33 38 36 2e 64 65  |2ubuntu2_i386.de|
00000130  62 0a 77 67 65 74 20 2d  63 20 68 74 74 70 3a 2f  |b.wget -c http:/|
00000140  2f 61 72 63 68 69 76 65  2e 75 62 75 6e 74 75 2e  |/archive.ubuntu.|
00000150  63 6f 6d 2f 75 62 75 6e  74 75 2f 70 6f 6f 6c 2f  |com/ubuntu/pool/|
00000160  6d 61 69 6e 2f 6c 69 62  78 2f 6c 69 62 78 63 62  |main/libx/libxcb|
00000170  2f 6c 69 62 78 63 62 2d  78 76 30 5f 31 2e 37 2d  |/libxcb-xv0_1.7-|
00000180  32 75 62 75 6e 74 75 32  5f 69 33 38 36 2e 64 65  |2ubuntu2_i386.de|
00000190  62 0a 77 67 65 74 20 2d  63 20 68 74 74 70 3a 2f  |b.wget -c http:/|
000001a0  2f 61 72 63 68 69 76 65  2e 75 62 75 6e 74 75 2e  |/archive.ubuntu.|
000001b0  63 6f 6d 2f 75 62 75 6e  74 75 2f 70 6f 6f 6c 2f  |com/ubuntu/pool/|
000001c0  6d 61 69 6e 2f 74 2f 74  7a 64 61 74 61 2f 74 7a  |main/t/tzdata/tz|
000001d0  64 61 74 61 5f 32 30 31  31 67 2d 30 75 62 75 6e  |data_2011g-0ubun|
000001e0  74 75 30 2e 31 31 2e 30  34 5f 61 6c 6c 2e 64 65  |tu0.11.04_all.de|
000001f0  62 0a 77 67 65 74 20 2d  63 20 68 74 74 70 3a 2f  |b.wget -c http:/|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Last night after my last post I used fsck which seemed to fix /dev/sda1. Next after that I wanted to move the /home directory to its own partition to avoid this mess in the future. However, I still get the grub rescue prompt when booting from the HD. I'm also guessing that part of the problem lies in the fact that /dev/sda1 has an unkown boot sector type.

P.S. Yes, I would prefer Lucid at this point since Natty decided to not cooperate. If I can get it fixed, then I'd stay how it is.

---

### Post by Hedgehog1 on 2011-06-03
The idea of moving your data into it's own '/home' partition is a good one.

Your first post indicated that your video card will not run Unity, and your choice if you stay at the Natty level is Ubuntu classic.

I would like to suggest a course of action that will leave your options open to return to 10.04 LTS, or stay at Natty in Classic.

To begin, we need to get Natty booting so you can move your data to either an external drive or to it's own '/home' partition.

Please boot off the **Natty** LiveCD/LiveUSB, select 'TRY' and then issue these two commands to refresh grub2.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

With any luck, this should get you booting into Ubuntu.  If this does not get you running, you can use the LiveCD/LiveUSB to copy your data to an external device.

Now for the hard choice: Attempt a repair, or save off your data and create a clean install.

I would suggest saving your data to an external hard drive, and then making a clean install on this drive with the following layout:

[B]/dev/sda1 EXT4 '/' (root) 30 gigs
/dev/sda2 EXT4 '/home' All space not used by root and swap
/dev/sda3 Swap - Size of your RAM plus 10%[/B]

If an external backup device is not an option, it is possible (but risky) to change partitions and move data a little at a time.

Do you have access to an external backup device for your data?


***The Hedge***

:KS

---

### Post by Destructo47 on 2011-06-04
I'll try to update grub. I have an equivalent nvidia card that has full OpenGL support, but I need to get some thermal grease for the GPU on it, because I moved the heatsink too much whilst wiping dust off. I don't have large enough external storage sources, but my hard drive is large enough that I can repartition without conflict. If I were to repartition, I would need to make / more than 30 gigs, simply because of programs installed (and yes, I do use most of them). /home has already been copied onto its own partition, but I have yet to remove it from the root folder.

One last thing: Can I install Backtrack Linux in the same root directory, or is it incompatible with Ubuntu? I never see anyone talking about Backtrack, so I'm assuming it's foreign grounds for a lot of Linux users. If I can't, then I don't mind using the live dvd for it.

If you don't know what that is here's that distro's site:
[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

Another last thing: How can I make sure the /home partition is linked to the root partition properly?

EDIT: It boots into Natty fine now, but with some various errors (I am using Ubuntu classic). None of my windows have the maximize, minimize, or close buttons on the top, so I have to manually find the window below, right-click and the close it. There's also the problem that I can't use the internet. Network Manager doesn't like my wireless connection. I have a script to install the Wicd client, but Synaptic isn't detecting that particular file as a download script.

---

### Post by Destructo47 on 2011-06-04
Turns out for the script I forgot to append the .sh to the filename. As I type, the packages are being downloaded, and I can move them over when done. If all goes well, I'll being booting normally for the foreseeable future.

Now it's time to test my quad speaker setup...:popcorn:

---

### Post by Hedgehog1 on 2011-06-04
Happy to hear the good news!

Things are looking up for you (and your PC).


***The Hedge***

:KS

**EDIT:** Backtrack is not really mentioned too much here because the it is frowned upon; however you should not attepmt to share a common '/' (root) partition between any two distros.  Unpredictable (and never nice unpredictable) things will happen.

---

### Post by Destructo47 on 2011-06-04
Thank you for all your help. I'll mark this as solved now.

---

