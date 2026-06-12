---
title: "grub and windows7"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by vinise on 2010-11-22
Hy every one

i've just install ubuntu 10.10 but grub did not see my windows 7 :(

windows is install on hd0/sda5

i've tried to add an entry on grub.cfg but without success... windows is not booting

```
menuentry "windows 7"{
        insmod ntfs
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set b25e0ffc5e0fb7dd
        chainloader +1
}

```any help will be pleased

---

### Post by wilee-nilee on 2010-11-22
Post the bootscript in my signature. In the reply click on the # and paste all the text from the generated file from running the script in between.

---

### Post by vinise on 2010-11-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2000. But according to the info from fdisk, 
                       sda6 starts at sector 516087808.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    29,296,639    29,294,592  83 Linux
/dev/sda4          29,298,686   976,771,071   947,472,386   f W95 Ext d (LBA)
/dev/sda5          32,124,928   516,085,759   483,960,832   7 HPFS/NTFS
/dev/sda6         516,087,808   976,771,071   460,683,264   7 HPFS/NTFS
/dev/sda7          29,298,688    32,124,927     2,826,240  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cb84dcb9-bb2b-4f95-9569-7520e68a84e1   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3426FD0C26FCD03A                       ntfs                                     
/dev/sda6        6A707B89707B5B31                       ntfs       Utility                       
/dev/sda7        625e54c8-8578-44a3-b7a3-2d053e5b5c38   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CA18E0BA18E0A723                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/3426FD0C26FCD03A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
set locale_dir=($root)/boot/grub/locale
set lang=fr
insmod gettext
#if [ "${recordfail}" = 1 ]; then
#  set timeout=-1
#else
#  set timeout=10
#fi
set timeout 30
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
    search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb84dcb9-bb2b-4f95-9569-7520e68a84e1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cb84dcb9-bb2b-4f95-9569-7520e68a84e1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set cb84dcb9-bb2b-4f95-9569-7520e68a84e1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
#if [ "x${timeout}" != "x-1" ]; then
#  if keystatus; then
#    if keystatus --shift; then
#      set timeout=-1
#    else
#      set timeout=0
#    fi
#  else
#    if sleep --interruptible 3 ; then
#      set timeout=0
#    fi
#  fi
#fi
set timeout 30
menuentry "windows 7"{
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b25e0ffc5e0fb7dd
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=625e54c8-8578-44a3-b7a3-2d053e5b5c38 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
  10.9GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
   1.2GB: initrd.img
  10.9GB: vmlinuz
```

---

### Post by carl4926 on 2010-11-22
Install os-prober

Then do

```
sudo os-prober
```

```
sudo update-grub
```

Does that solve it?

---

### Post by wilee-nilee on 2010-11-22
> **carl4926 said:**
> Install os-prober

Then do

```
sudo os-prober
```

```
sudo update-grub
```

Does that solve it?

Did you notice the missing files in the windows partition. And this line in the script.
```
### BEGIN /etc/grub.d/30_os-prober ###

```

---

### Post by carl4926 on 2010-11-22
Yikes!
Does the OP have a windows DVD? I wonder?
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by wilee-nilee on 2010-11-22
First having windows farther into the disc can cause problems, but you are also missing specific boot files, here is your partition with the files added which should be there highlighted.

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

Couple of ways to fix this so lets wait for some more help as there are some awesome users on line as we post.

---

### Post by vinise on 2010-11-22
nothing is working :(

---

### Post by wilee-nilee on 2010-11-22
> **vinise said:**
> nothing is working :(

It helps us in helping you if your are more concise. Such as I have a install dvd, or I have downloaded the recovery, iso, and even have it burned. You will need one or the other basically.

---

### Post by vinise on 2010-11-22
ive tried both my install dvd and the recovery... both are not abble to repair...
i'll reinstall windows... and we'll see after to reinstall grub

---

### Post by wilee-nilee on 2010-11-22
> **vinise said:**
> ive tried both my install dvd and the recovery... both are not abble to repair...
i'll reinstall windows... and we'll see after to reinstall grub

If you can and are backed up wipe Ubuntu and put W7 at the beginning of the disc then Ubuntu after. Also if you are just going to reinstall Windows in the same place make that partition first with gparted=NTFS, otherwise you may loose the Ubuntu.

Edit: with a closer look at the script you also have W7 inside the extended that doesn't work basically, it needs a primary partition outside of the extended.

---

### Post by oldfred on 2010-11-22
wilee-nilee is correct. Windows does not boot directly from a logical partition. You have to have an install of windows in a primary partition that will then boot the install in the logical.

It also looks like you copied your windows from sda1 which would normally start at sector 2048.

    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.

---

### Post by carl4926 on 2010-11-22
It should be possible to make some free space on sdb to backup important files to.
sda is pretty messed up and I'm struggling to see just how you managed to do what you have done.

---

### Post by Quackers on 2010-11-22
Also the boot flag is set on sda1, leading me to suspect that the 2 missing boot files were there at some time.

---

### Post by jacob.david on 2010-11-22
I had a similar issue and I solved it by the following method.
I had windows 7 on sda. I was trying to install Ubuntu on sdb. While installing Ubuntu I chose sdb as "Root partition". Later in the BIOS I choose sdb over sda in the booting sequence. Everything was OK and now I have both working fine.

---

