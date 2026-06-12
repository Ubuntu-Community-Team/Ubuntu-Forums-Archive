---
title: "Kernel update error"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by ben92110 on 2011-10-16
I'm pretty new to the linux world.  I've been using ubuntu 11.04 for about 4 months on an older laptop, and learning  a bit, but mostly just typical usage. 
Anyway, I got a new monster desktop for running some mathmatical models, and was hoping to use a linux based fortran compiler for the modeling. 
I just got 11.04 installed and running:  Lenovo ThinkStation D20, dual Xeon E5606 processors, 8GB ram, 2x500GB, 1x3TB hard drives.  Dual boot: Win7 on one 500GB hd, 11.04 on the other 500GB hd, and the 3tb drive for linux storage. 
It went through the normal installer OK, and continues to boot and run fine if I boot with kernel 2.6.38-8.  However, I ran the standard update manager after getting the system running, which installed kernel 2.6.38-11, with no error reported on the screen.  When rebooting after that update, the system hangs with a black screen.  If I try to boot using 2.6.38-11 "recovery mode" then it comes to an error message, saying "/dev/disk/gobbldegook does not exist" then goes into the "initramfs" shell. 
I can still use the option in grub to boot from the older -8 kernel and it seems to work fine, but it's disconcerting that the newer kernel doesn't work.  I was wondering if anyone has seen similar problems before? 
Any suggestions for where to look for any "invisible" errors that I'm having with the old kernel that just aren't as obvious as a black screen but could cause a kernel update to fail?

---

### Post by drs305 on 2011-10-16
You can try to rebuild the initrd.img for the problem kernel.

Boot the -8 kernel, then run this command *:
```
sudo update-initramfs -c -k 2.6.38-11
```
* Change the title to the exact kernel you are using (i.e. include -generic, or however it appears in /boot/grub/grub.cfg or check the file in /boot.

If the command runs without errors,"sudo update-grub" just to ensure it has the correct kernel and initrd names. This shouldn't be necessary, but it guarantees the kernel and initrd.img are in place.

---

### Post by ben92110 on 2011-10-16
Thanks, but no luck.  Still hangs when booting in 2.6.38-11-generic.  
Tried again in recovery mode and the error is:
Gave up waiting for root device.  Common problems:
.....
ALERT! /dev/disk/by-uuid/12cc648....  does not exist.
Dropping to a shell!

Then goes to initramfs shell.

Still works to boot into 2.6.38-8 though.

By the way, is there a command to reboot from within initramfs, or is holding down the power button the only way?

---

### Post by drs305 on 2011-10-16
If it's a initrd image problem I'm not sure what to suggest except perhaps to remove and reinstall that kernel (linux-image-2.6.38-11-generic). I'm assuming you ran the update-initramfs command on "2.6.38-11-generic"

If it's not an image problem, we might learn something from the boot info script. If you will post the contents of RESULTS.txt we can see if there is something in the boot process files (other than the image) that might be causing the issue. 

You can get the boot script from the "BIS" link in my signature line.

---

### Post by ben92110 on 2011-10-16
Sorry this took awhile.  I took a dinner break.

```
        Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/grub on this drive.
 => No known boot loader is installed in the MBR of /dev/sdf.
 => No boot loader is installed in the MBR of /dev/sdg.

sde2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sde3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdf2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdf3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde2    *          4,096       980,991       976,896  83 Linux
/dev/sde3             983,038   938,481,663   937,498,626   5 Extended
/dev/sde5             983,040   938,481,663   937,498,624  83 Linux
/dev/sde4         938,481,664   976,771,071    38,289,408  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,048     2,457,599     2,455,552   7 NTFS / exFAT / HPFS
/dev/sdf2           2,457,600   956,293,119   953,835,520   7 NTFS / exFAT / HPFS
/dev/sdf3         956,293,120   976,771,071    20,477,952   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdg1              34 2,639,305,812 2,639,305,779 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sde2        6f1de656-72d7-4c74-9a20-d9ec2216c6e4   ext4       
/dev/sde4        069a7537-19c9-4741-a8c7-7c805286f916   swap       
/dev/sde5        12cc648c-5bfb-4262-8de9-d7676ed7c15a   ext4       
/dev/sdf1        38AC4A11AC49CA58                       ntfs       SYSTEM_DRV
/dev/sdf2        DAC44E0EC44DED77                       ntfs       Windows7_OS
/dev/sdf3        5C4053104052F06E                       ntfs       Lenovo_Recovery
/dev/sdg1        af63af1f-d4bd-4e80-a6b8-720b0241cbbd   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sde2        /boot                    ext4       (rw,commit=0)
/dev/sde5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdg1        /home                    ext4       (rw,commit=0)


============================= sde2/grub/grub.cfg: ==============================

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
set root='(/dev/sde,msdos5)'
search --no-floppy --fs-uuid --set=root 12cc648c-5bfb-4262-8de9-d7676ed7c15a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos2)'
search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux    /vmlinuz-2.6.38-11-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux    /vmlinuz-2.6.38-8-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdf1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdf,msdos1)'
    search --no-floppy --fs-uuid --set=root 38AC4A11AC49CA58
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdf2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdf,msdos2)'
    search --no-floppy --fs-uuid --set=root DAC44E0EC44DED77
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

=================== sde2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.261668205 = 0.280964096    grub/core.img                                  1
   0.262707710 = 0.282080256    grub/grub.cfg                                  1
   0.063301086 = 0.067969024    initrd.img-2.6.38-11-generic                   3
   0.047636032 = 0.051148800    initrd.img-2.6.38-8-generic                    2
   0.027654648 = 0.029693952    vmlinuz-2.6.38-11-generic                      2
   0.019839287 = 0.021302272    vmlinuz-2.6.38-8-generic                       1

=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sde,msdos5)'
search --no-floppy --fs-uuid --set=root 12cc648c-5bfb-4262-8de9-d7676ed7c15a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos2)'
search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux    /vmlinuz-2.6.38-11-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /vmlinuz-2.6.38-11-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux    /vmlinuz-2.6.38-8-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sde,msdos2)'
    search --no-floppy --fs-uuid --set=root 6f1de656-72d7-4c74-9a20-d9ec2216c6e4
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdf1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdf,msdos1)'
    search --no-floppy --fs-uuid --set=root 38AC4A11AC49CA58
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdf2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdf,msdos2)'
    search --no-floppy --fs-uuid --set=root DAC44E0EC44DED77
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

=============================== sde5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=12cc648c-5bfb-4262-8de9-d7676ed7c15a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sde2 during installation
UUID=6f1de656-72d7-4c74-9a20-d9ec2216c6e4 /boot           ext4    defaults        0       2
# /home was on /dev/sdg1 during installation
UUID=af63af1f-d4bd-4e80-a6b8-720b0241cbbd /home           ext4    defaults        0       2
# swap was on /dev/sde4 during installation
UUID=069a7537-19c9-4741-a8c7-7c805286f916 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.728465080 = 0.782183424    boot/grub/core.img                             1
   0.729504585 = 0.783299584    boot/grub/grub.cfg                             1
   0.530097961 = 0.569188352    boot/initrd.img-2.6.38-11-generic              3
   0.514432907 = 0.552368128    boot/initrd.img-2.6.38-8-generic               2
   0.494451523 = 0.530913280    boot/vmlinuz-2.6.38-11-generic                 2
   0.486636162 = 0.522521600    boot/vmlinuz-2.6.38-8-generic                  1
   0.530097961 = 0.569188352    initrd.img                                     3
   0.514432907 = 0.552368128    initrd.img.old                                 2
   0.494451523 = 0.530913280    vmlinuz                                        2
   0.486636162 = 0.522521600    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdf

00000000  eb 0e 03 00 04 00 4c 02  00 00 00 00 00 00 4e 50  |......L.......NP|
00000010  fa 33 c0 bc 00 66 8e d0  50 07 50 1f fb fc be 09  |.3...f..P.P.....|
00000020  00 89 14 bf 00 08 be 00  7c b9 00 01 f3 a5 50 bf  |........|.....P.|
00000030  34 08 57 cb bb 00 06 be  02 08 0f b6 0c b8 01 02  |4.W.............|
00000040  ba 80 00 cd 13 ba 05 00  bf 00 06 b9 00 02 e8 24  |...............$|
00000050  01 b9 05 00 bb 00 12 be  00 06 03 f1 e8 ff 00 eb  |................|
00000060  0a b3 01 be a7 12 88 1c  e9 89 00 e8 2d 00 3c 01  |............-.<.|
00000070  74 ef e8 52 00 3c 01 74  e8 ba 04 00 bf 00 0a b9  |t..R.<.t........|
00000080  a7 08 e8 f0 00 e8 35 05  e9 88 01 be 05 08 0a 04  |......5.........|
00000090  88 04 b1 01 bb 00 08 e8  b9 00 c3 be 00 06 e8 17  |................|
000000a0  00 be 23 06 80 3c 00 74  0c 3c 00 74 08 b0 02 e8  |..#..<.t.<.t....|
000000b0  d9 ff b0 01 c3 b0 00 c3  b9 00 02 4e 32 c0 8b d9  |...........N2...|
000000c0  8a 10 32 c2 e2 f8 c3 b9  05 00 51 b8 00 02 f7 e1  |..2.......Q.....|
000000d0  05 00 08 8b f0 e8 e0 ff  5e 56 0f b6 8c 05 06 e3  |........^V......|
000000e0  04 38 c1 75 06 59 e2 e2  b0 00 c3 59 b0 01 e8 9a  |.8.u.Y.....Y....|
000000f0  ff b0 01 c3 be 07 08 0f  b6 0c b8 01 02 bb 00 7c  |...............||
00000100  ba 80 00 cd 13 be 00 7c  e8 ad ff be 06 08 0f b6  |.......|........|
00000110  0c e3 1c 38 c1 74 18 b0  04 e8 6f ff be af 07 e8  |...8.t....o.....|
00000120  8c 02 be a7 12 80 3c 01  74 03 e8 0a 01 cd 18 be  |......<.t.......|
00000130  be 09 bf be 7d b9 20 00  f3 a5 ba 04 00 bf 00 7c  |....}. ........||
00000140  b9 be 01 e8 2f 00 be 09  00 8b 14 33 c0 50 bf 00  |..../......3.P..|
00000150  7c 57 cb 32 ed b8 01 03  ba 80 00 cd 13 c3 51 4e  ||W.2..........QN|
00000160  0f b6 0c e3 08 b8 01 02  ba 80 00 cd 13 81 eb 00  |................|
00000170  02 59 e2 ea c3 52 57 51  b8 00 bb cd 1a 72 2b 66  |.Y...RWQ.....r+f|
00000180  83 f8 00 75 25 81 f9 02  01 7c 1f 66 81 fb 54 43  |...u%....|.f..TC|
00000190  50 41 75 16 33 c0 8e c0  66 33 f6 b8 07 bb 66 33  |PAu.3...f3....f3|
000001a0  c9 66 33 d2 59 5f 5a cd  1a c3 59 5f 5a c3 00 00  |.f3.Y_Z...Y_Z...|
000001b0  65 6d 00 00 00 63 7b 9a  3c 1b 6d 56 00 00 80 20  |em...c{.<.mV... |
000001c0  21 00 07 f9 21 98 00 08  00 00 00 78 25 00 00 f9  |!...!......x%...|
000001d0  22 98 07 fe ff ff 00 80  25 00 00 60 da 38 00 fe  |".......%..`.8..|
000001e0  ff ff 07 fe ff ff 00 e0  ff 38 00 78 38 01 00 00  |.........8.x8...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb sdc sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by drs305 on 2011-10-16
Thanks for posting RESULTS.txt

I can't see anything wrong with the initrd addresses. The only thing I can recommend, if you haven't done it, is to uninstall the -11 kernel and reinstall it.

```
uname -r # Confirm you aren't using the -11 kernel.
sudo apt-get update
sudo apt-get purge linux-image-2.6.38-11-generic
sudo apt-get install linux-image-2.6.38-11-generic
```
The update-grub command should run after each of the last two commands, but as I didn't see any issues with your Grub files the menus shouldn't change (even though the initrd image may be updated).

You can search to see if others have had problems with the -10 kernel.
Having the latest kernel is nice, but if everything is working in -8 you may have to just wait for the -12 kernel, should it come along.

---

### Post by ben92110 on 2011-10-16
Thanks for the help.  Uninstalling and reinstalling the kernel still has the same error upon booting into -11. 

I guess for now I'll stick with 2.6.38-8.

---

