---
title: "Extra File System With Uninstalled (?) Meerkat"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by davesinger on 2011-04-21
I had a problem trying to install, then uninstall, drivers for my ATI video controller on my new HP Desktop. (I wasn't able to get dual monitors running with one VGA and one DVI-D, then lost all video...but that's for another forum).
Anyway, long story short, I ended up reinstalling Meerkat 10.10 aside the original Windows 7 but the process seems to have left the original file system (2.6.35-28) intact in (I think) /dev/sda5 wile installing the new (actually 2.6.35-22 as the CD I used was a couple of weeks old).
So now on the 1 Terrabite HDD I have a File System and a second 466 GB File System as well as Windows 7.  When the computer boots the grub boot menu reads:

Ubuntu with Linux 2.6.35-22- generic
Ubuntu with Linux 2.6.35-22- generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)
Ubuntu with Linux 2.6.35-28- generic (on /dev/sda5)
Ubuntu with Linux 2.6.35-28- generic (recovery mode) on /dev/sda5)
Ubuntu with Linux 2.6.35-28- generic (on /dev/sda5)
Ubuntu with Linux 2.6.35-28- generic (recovery mode) (on /dev/sda5)

I tried to clear the grub boot menu by removing 2.6.3528 using the Synaptic Package Manager, but it indicates that the packages are not installed (but I see the files in the 466 GB File System!) and even if install and uninstall 2.6.35-28 the grub boot menu doesn't clear the unwanted entries.  I also can't erase the folders and files on 2.6.35-28 because I am not on as root (I'm not yet comfortable with sudo commands if I don't know what I am doing) and am not sure  if formatting it (a right click option) is safe.

So, the questions:
How can I remove the 2.6.35-28 files in the 466 GB File System?
How can I remove 2.6.35-28 from the grub boot menu?
Can I format the 466 GB File Systems safely?  By right click and select format?
Any good use for the 466 GB File System?  As an extra drive?  Can I expand one of the other sectors to include it?

Thanks for any help.

---

### Post by Hedgehog1 on 2011-04-21
If you would do this from the Ubuntu you plan to keep:


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


We can walk you through the steps...


***The Hedge***

:KS

---

### Post by Dutch70 on 2011-04-21
Edit: Well, looks like my buddy Hedge beat me to the punch :)
The boot script will give all of the info I asked for and then some. 
I just hoped it wasn't needed.

Post a screenshot of your partitions in gparted using the paper clip in the tool bar of your next post. 

Also post the output of...
```
sudo fdisk -l
```
That is a lower case L in the command.

Do not post a pic of that. Copy & paste the info between [CODE][ /CODE] tags using the # symbol in the toolbar. This keeps the formatting correct.

---

### Post by Hedgehog1 on 2011-04-21
> **Dutch70 said:**
> Edit: Well, looks like my buddy Hedge beat me to the punch :)

HE HE!  Hedgehog fingers are small - but that makes them ***FAST!!!***

***The 'typo-matic' Hedge***

:KS

---

### Post by davesinger on 2011-04-22
Okay, I downloaded the file and got both text files.  Let's see if I can post them.  First is RESULTS.txt
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

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

/dev/sda1    *          2,048       221,183       219,136   7 HPFS/NTFS
/dev/sda2             224,910   493,111,764   492,886,855   7 HPFS/NTFS
/dev/sda3       1,928,218,624 1,953,523,119    25,304,496   7 HPFS/NTFS
/dev/sda4         493,113,342 1,928,218,623 1,435,105,282   5 Extended
/dev/sda5         988,801,024 1,899,898,879   911,097,856  83 Linux
/dev/sda6       1,899,900,928 1,928,218,623    28,317,696  82 Linux swap / Solaris
/dev/sda7         493,113,344   968,630,271   475,516,928  83 Linux
/dev/sda8         968,632,320   988,801,023    20,168,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E4422E35422E0D3C                       ntfs       SYSTEM                        
/dev/sda2        D00C2F240C2F04D6                       ntfs       OS                            
/dev/sda3        DEFE5D83FE5D553D                       ntfs       HP_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        131e7c16-0de2-4c3d-9fc3-1a350b2696b6   ext4                                     
/dev/sda6        6700afb2-4cab-40dc-bb99-52d320dd7c17   swap                                     
/dev/sda7        9b98fc05-9c4b-42e7-8438-5a24459eff3c   ext4                                     
/dev/sda8        ebeb05a6-5db6-451c-b459-bf69d04e3d8a   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e4422e35422e0d3c
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d00c2f240c2f04d6
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set defe5d83fe5d553d
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
UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6700afb2-4cab-40dc-bb99-52d320dd7c17 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 807.0GB: boot/grub/core.img
 558.0GB: boot/grub/grub.cfg
 513.5GB: boot/initrd.img-2.6.35-22-generic
 523.1GB: boot/initrd.img-2.6.35-28-generic
 807.0GB: boot/vmlinuz-2.6.35-22-generic
 544.2GB: boot/vmlinuz-2.6.35-28-generic
 523.1GB: initrd.img
 513.5GB: initrd.img.old
 544.2GB: vmlinuz
 807.0GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9b98fc05-9c4b-42e7-8438-5a24459eff3c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9b98fc05-9c4b-42e7-8438-5a24459eff3c ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9b98fc05-9c4b-42e7-8438-5a24459eff3c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e4422e35422e0d3c
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d00c2f240c2f04d6
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set defe5d83fe5d553d
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 131e7c16-0de2-4c3d-9fc3-1a350b2696b6
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=131e7c16-0de2-4c3d-9fc3-1a350b2696b6 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=9b98fc05-9c4b-42e7-8438-5a24459eff3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ebeb05a6-5db6-451c-b459-bf69d04e3d8a none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 291.2GB: boot/grub/core.img
 274.1GB: boot/grub/grub.cfg
 253.4GB: boot/initrd.img-2.6.35-22-generic
 291.2GB: boot/vmlinuz-2.6.35-22-generic
 253.4GB: initrd.img
 291.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Then the results of sudo fdisk -l

```
david@david-HP-Pavilion-P6000-Series:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x552ca64f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          14      109568    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              15       30695   246443427+   7  HPFS/NTFS
/dev/sda3          120027      121602    12652248    7  HPFS/NTFS
/dev/sda4           30695      120027   717552641    5  Extended
/dev/sda5           61551      118264   455548928   83  Linux
/dev/sda6          118264      120027    14158848   82  Linux swap / Solaris
/dev/sda7           30695       60295   237758464   83  Linux
/dev/sda8           60295       61551    10084352   82  Linux swap / Solaris

Partition table entries are not in disk order
david@david-HP-Pavilion-P6000-Series:~$ 
```

Thanks in advance for your help!

---

### Post by Dutch70 on 2011-04-22
Yepp, looks like you've installed Ubuntu twice.
```
/dev/sda4         493,113,342 1,928,218,623 1,435,105,282   5 Extended
/dev/sda5         988,801,024 1,899,898,879   911,097,856  83 Linux
/dev/sda6       1,899,900,928 1,928,218,623    28,317,696  82 Linux swap / Solaris
/dev/sda7         493,113,344   968,630,271   475,516,928  83 Linux
/dev/sda8         968,632,320   988,801,023    20,168,704  82 Linux swap / Solaris
```

Post a pic of Gparted **with the paper clip in the toolbar** and we'll be able to help you get it straightened out.

Looks like you'll have to delete sda5 & sda6, but I can tell more from a screenshot of Gparted.

---

### Post by davesinger on 2011-04-22
Here it is.  Learning new things today.

---

### Post by Dutch70 on 2011-04-22
How much physical RAM do you have, your swap partition only needs to be equal to your RAM, slightly larger if you want.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

Edit2: This is assuming you want to keep your latest install. :)
And of course back ups kind of go without saying nowadays.

It's fairly easy to create a swap partition, so I think you would be better off to delete sda5, sda6 & sda8. Then extend sda7 to fill all but the amount of space you want to use for swap. Then create the swap partition. I believe you can create swap first if you shrink it from the left side. That may be easier for you to get it to the size you want.

Once you get your new swap partition created you'll need to edit fstab with your new UUID, we'll help you with that when you get to it.

Edit: You can't modify partitions while they are mounted, you may need to do this from the live cd/usb, or you may be able to do it by right clicking your mounted swap partition in gparted & select "swapoff".

Alternatively you can just delete sda5 & sda8. Then shrink sda6 to the size you want it. You'll still have to change the UUID in fstab. Also, keep in mind that the partition numbers (as in sdaX) will change as you delete them. ie..if you delete sda5, sda8 will become sda7. I think I said that right...lol.

---

### Post by davesinger on 2011-04-22
Okay, time to PANIC.  I hope not, I'll just stay calm.

Using GParted I deleted sda8 first. You were right, I had to right click and select swapoff first.  I could not delete sda6 or sda5 right then - I got a message saying that higher numbered drives must be unmounted first.  So after completing the deletion, I exited and booted from my live CD.  From there I was able to delete sda6 and sda5 (Just in case, I had made a note of the sizes so I know I got the right ones). Then I exited GParted and shut down.

I then rebooted, or rather tried to reboot.  No grub menu, just an error message - "error: no such partition" and a prompt "grub rescue>"

I'm now back on the live CD. What do I do now?  Would it be easier to just delete all of the non-NTFS partitions and start over or am I not lost yet?

I made a print screen of the GParted screen here.

---

### Post by Dutch70 on 2011-04-22
LOL, you're not lost yet bro. Stay calm. Run the following command & paste the contents of gedit into your next post. Between code tags please.
```
gksudo gedit /etc/fstab
```

Also, open gparted, right click on what sda5 & select infomation, copy and paste the UUID into your next post also.

Edit: I probably asked for this before I needed it, go on to my next post.

---

### Post by Dutch70 on 2011-04-22
To get your system booting again. From the live cd/usb run the following commands.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by davesinger on 2011-04-22
Not much to show, here it is.

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

Let's see if I'm learning anything here.  I see the / that was in sda7 (now sda5) is missing and I see no swap partition.  Anything important in those observations?

---

### Post by Dutch70 on 2011-04-22
> **davesinger said:**
> Not much to show, here it is.

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

Let's see if I'm learning anything here.  I see the / that was in sda7 (now sda5) is missing and I see no swap partition.  Anything important in those observations?

Yes, we're going to have to recreate your swap partition and edit fstab, just breathe deeply & take it one step at a time. :) Even if we hit a bit of a road block, we've got back up!!! 

I realize it's a tedious procedure if you've never done it before, but after you do it once, you'll realize it's not that bad at all. Of course, anytime you're messing with partitions, things can go wrong. They usually don't.

---

### Post by davesinger on 2011-04-22
Moving along.  That fixed the boot loader (phew), now there is the matter of the swap partition.

The link Hedgehog1 sent essentially said this:

```
In terminal:
sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512
sudo chmod 600 /mnt/512Mb.swap
Then:
sudo mkswap /mnt/512Mb.swap
Then:
sudo swapon /mnt/512Mb.swap
Then:
gksudo gedit /etc/fstab
Opens gedit - Add this line at the end of the file:
/mnt/512Mb.swap  none  swap  sw  0 0
And save. After the next reboot the swap will be used automatically. 
```

I have 5 Gigs ram so I am guessing that instead if 512MB I would enter either 11264MB or 11GB and instead of count=512 it would be count=11265.  That is if I have done my math correctly.  

Then the grub boot menu.

---

### Post by davesinger on 2011-04-22
And filling up that unallocated space.  I guess I'll want to combine the unallocated space that was sda5, sda6, and sda8 after using some for the swap partition.  Some other time I can learn to reassign it to windows use.

---

### Post by Dutch70 on 2011-04-22
you would want 5GB + about 10% if you want to be sure you can hibernate successfully. It's actually not a necessity at all if you don't want to hibernate, but it's a good idea. 

It's not double the size of RAM, unless you have very little RAM...as in 512MB. 

After you create that you have a lot of options, so let's do that first.

---

### Post by davesinger on 2011-04-22
So I want, say 6 GB to use round numbers and be extra safe.  I can afford it. 
"/mnt/512Mb.swap" appears to be a file name?  So I'm guessing that the 512Mb part is arbitrary?  Could I use "/mnt/6Mb.swap"?  How about the "bs=1M" and "count=512" (and "600") parts of the sudo command?

---

### Post by Dutch70 on 2011-04-22
6GB is fine, I have no idea what the rest of your post means.

---

### Post by davesinger on 2011-04-22
I mean "/mnt/6Gb.swap" as the arbitrary file name.  If I understand it that is.

---

### Post by Dutch70 on 2011-04-22
I'm not familiar with anything like that. Never even heard of it. Unless who/where ever you got that from responds. I'd just forget it.

---

### Post by davesinger on 2011-04-22
Okay, I went back and read the link detailing how to set up a swap file...
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
It only tells how to set up a 512 Mb file, so I attempted to extrapolate the information for a 6 gig swap file.
Rather than naming the file "/mnt/512Mb.swap" I named it "/mnt/6Gb.swap"
Rather than "count=512" I entered "count=6144" (6144Mb = 6GB) 
After completing the process I rebooted and ran GParted.  It doesn't show a swap file, did I create it incorrectly?

It's getting late, so I'll worry about the unallocated space and grub boot menu later.

---

