---
title: "How Keep Grub2 access to 10.04 after installing 10.10?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by hg21 on 2010-10-22
For some time now I have kept 2 partitions for (K)ubuntu versions so I can go back if the new one is troublesome.

So, I have a common /boot partition, 2 partitions for (K)ubuntu versions and a common data partition which both versions can access.

After installing 10.10 I lost the grub connection to the earlier version. This did not happen in the past. So far I've failed to get it back by various attempts to do so.  

Did I make a mistake in allowing the /boot partition to be formatted during install of 10.10 (can't remember what I did before) or has the /etc/grub.d/os_prober in 10.10 failed in some way?

Fortunately up to now 10.10 has been OK.

---

### Post by Rubi1200 on 2010-10-22
Hi,
could you please post the results of the boot-script linked at the bottom of my post.

The results will give us a better overview of your setup and make offering solutions easier.

Please wrap the text with the # tag when posting back.

Thanks.

---

### Post by hg21 on 2010-10-25
> **Rubi1200 said:**
> Hi,
could you please post the results of the boot-script linked at the bottom of my post.

The results will give us a better overview of your setup and make offering solutions easier.

Please wrap the text with the # tag when posting back.

Thanks.

Thanks for your reply. A very useful looking script. 

For an unrelated reason I changed my set-up before reading your reply and now have 10.10 on 2 different partitions. However there is still a problem.  Although both instances of 10.10 appear in grub2 menu I only get to the version on sda8 whichever I choose.  For some reason the osprober menu entry has picked up the root uuid (a623ce95-67f6-4bb8-9681-5edaf2b97538) of sda8 for the version which it says is on sda5!!

My problem may relate to my having the same kernel image for both instances of 10.10 in the /boot partition although I can't see why it should.  (I had that same situation in the case I first described with 10.04 and 10.10.)

here are the script results:-
########################################################
                 Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          19,533,822 1,953,523,711 1,933,989,890   5 Extended
/dev/sda5          19,533,824   214,843,391   195,309,568  83 Linux
/dev/sda6         800,782,336 1,191,405,567   390,623,232  83 Linux
/dev/sda7       1,191,407,616 1,758,212,095   566,804,480  83 Linux
/dev/sda8       1,758,214,144 1,953,523,711   195,309,568  83 Linux
/dev/sda9         214,845,440   605,462,527   390,617,088  83 Linux
/dev/sda10        605,464,576   800,774,143   195,309,568  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        037be166-c1b1-40e1-8088-580edc42f0cd   ext3                                     
/dev/sda10       8ce4c9d7-6052-4e46-9548-3f5afb602a0c   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        14679316-f160-4ae9-a704-a8ea25312fc9   ext4                                     
/dev/sda6        853fdd54-05e4-4eaa-808c-7a32c2f7f30e   ext4                                     
/dev/sda7        d6550473-0b1b-45e6-a62d-d6a45309cb3f   ext4                                     
/dev/sda8        a623ce95-67f6-4bb8-9681-5edaf2b97538   ext4                                     
/dev/sda9        6ca74700-0f76-4be5-9b29-568117e0f8d3   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /boot                    ext3       (rw,commit=0)
/dev/sda6        /DATA                    ext4       (rw,commit=0)
/dev/sda7        /ENTERTAINMENT           ext4       (rw,commit=0)
/dev/sda9        /COMMON                  ext4       (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set a623ce95-67f6-4bb8-9681-5edaf2b97538
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        linux   /vmlinuz-2.6.35-22-generic root=UUID=a623ce95-67f6-4bb8-9681-5edaf2b97538 ro   quiet splash
        initrd  /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        echo    'Loading Linux 2.6.35-22-generic ...'
        linux   /vmlinuz-2.6.35-22-generic root=UUID=a623ce95-67f6-4bb8-9681-5edaf2b97538 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        linux16 /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        linux /vmlinuz-2.6.35-22-generic root=UUID=a623ce95-67f6-4bb8-9681-5edaf2b97538 ro quiet splash
        initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set 037be166-c1b1-40e1-8088-580edc42f0cd
        linux /vmlinuz-2.6.35-22-generic root=UUID=a623ce95-67f6-4bb8-9681-5edaf2b97538 ro single
        initrd /initrd.img-2.6.35-22-generic
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

=================== sda1: Location of files loaded by Grub: ===================


   6.8GB: grub/core.img
   6.7GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=14679316-f160-4ae9-a704-a8ea25312fc9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=037be166-c1b1-40e1-8088-580edc42f0cd /boot           ext3    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=8ce4c9d7-6052-4e46-9548-3f5afb602a0c none            swap    sw              0       0
/dev/sda6 /DATA ext4 defaults        0       2
/dev/sda7 /ENTERTAINMENT ext4 defaults        0       2
/dev/sda9 /COMMON ext4 defaults        0       2


=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a623ce95-67f6-4bb8-9681-5edaf2b97538 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=037be166-c1b1-40e1-8088-580edc42f0cd /boot           ext3    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=8ce4c9d7-6052-4e46-9548-3f5afb602a0c none            swap    sw              0       0
/dev/sda6 /DATA ext4 defaults        0       2
/dev/sda7 /ENTERTAINMENT ext4 defaults        0       2
/dev/sda9 /COMMON ext4 defaults        0       2


=================== sda8: Location of files loaded by Grub: ===================


 900.2GB: initrd.img
 900.2GB: vmlinuz
(END) 
###################################################################

---

### Post by oldfred on 2010-10-26
I do not recommend separate /boot except for a few special cases. Old systems with 137GB BIOS boot limits, servers, RAID, or LVM may need /boot.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I do not see how you could have one boot partition with two installs before. You must have edited grub to set root to be different partitions with the same boot. Everyone with separate /boots uses a unique one for each system. It may have worked in your case if the versions were totally identical.

If you want to attempt to continue you will have to turn off osprober and move your second entry into 40_custom and edit it to the correct partition. Not sure if it will work long term. My fear is updates will get out of sync even though kernel and initrd should be separate from rest of system.

---

