---
title: "BOOTMGR missing in Windows 7 dual-boot"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by bigred1 on 2011-03-30
I have a single harddisk partitioned with Ubuntu Maverick  and Windows 7 installations. I installed Windows first and then Ubuntu, after resizing partitions and adding a new one for Ubuntu.

Win7 did not appear in the Grub2 boot menu. I added it (sda3), but on rebooting, I get the message *"BOOTMGR is missing/Press Ctrl+Alt_Del to restart"*. 

I understand that Win7 might have put its boot manager in another partition, and sda1 had FAT. 

I added sda1 as another grub2 entry, but when I try that, I get the error message *"Windows Boot Manager/ Windows failed to start. A recent hardware or software change might be the cause... Status 0xc0000225/ Info: The boot selection failed because a required device is inaccessible."*

Attached are fdisk and parted outputs; and the grub2 files I created.

How do I get Windows 7 to boot up?

---

### Post by oldfred on 2011-03-30
Post this and be sure to use code tags to make it easy for everyone to read.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by bigred1 on 2011-03-31
Here is the output of the script:



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /COMMAND.COM

sda2: _________________________________________________________________________

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

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       2050047 sectors, but according to the info from fdisk, 
                       it has 2271279 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    85,211,650    85,211,588   c W95 FAT32 (LBA)
/dev/sda2          85,213,182   734,349,311   649,136,130   f W95 Ext d (LBA)
/dev/sda5         701,016,064   732,860,415    31,844,352  83 Linux
/dev/sda6         732,862,464   734,349,311     1,486,848  82 Linux swap / Solaris
/dev/sda7         672,909,312   701,014,015    28,104,704  83 Linux
/dev/sda8          85,213,184   660,621,311   575,408,128  83 Linux
/dev/sda9         660,623,360   672,899,071    12,275,712  82 Linux swap / Solaris
/dev/sda3         734,349,312   974,501,887   240,152,576   7 HPFS/NTFS
/dev/sda4         974,501,888   976,773,167     2,271,280  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        305D-1CF9                              vfat                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        4856F6F856F6E59A                       ntfs                                     
/dev/sda4        686CF0836CF04CF6                       ntfs       LENOVO_PART                   
/dev/sda5        8766495c-bdef-4e73-bbb7-8cedffc965e0   ext4                                     
/dev/sda6        e609de19-5441-422a-ae86-06bc9da2554f   swap                                     
/dev/sda7        8651fcf9-61d0-437a-b3eb-0b84646b8504   ext2                                     
/dev/sda8        e02d9afe-2c70-41c7-8108-4ea3c49ff627   ext4                                     
/dev/sda9        21388adf-48b7-4d29-9f03-8079289fedfb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Disc              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8766495c-bdef-4e73-bbb7-8cedffc965e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8766495c-bdef-4e73-bbb7-8cedffc965e0 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 305d-1cf9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 686cf0836cf04cf6
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
# / was on /dev/sda6 during installation
UUID=8766495c-bdef-4e73-bbb7-8cedffc965e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e609de19-5441-422a-ae86-06bc9da2554f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 370.3GB: boot/grub/core.img
 361.3GB: boot/grub/grub.cfg
 361.4GB: boot/initrd.img-2.6.35-22-generic
 359.6GB: boot/vmlinuz-2.6.35-22-generic
 361.4GB: initrd.img
 359.6GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e02d9afe-2c70-41c7-8108-4ea3c49ff627 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e02d9afe-2c70-41c7-8108-4ea3c49ff627 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e02d9afe-2c70-41c7-8108-4ea3c49ff627 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e02d9afe-2c70-41c7-8108-4ea3c49ff627 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/12_windowsB ###
menuentry "Windows 7B" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/12_windowsB ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set e02d9afe-2c70-41c7-8108-4ea3c49ff627
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 305d-1cf9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 686cf0836cf04cf6
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=8766495c-bdef-4e73-bbb7-8cedffc965e0 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8766495c-bdef-4e73-bbb7-8cedffc965e0
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=8766495c-bdef-4e73-bbb7-8cedffc965e0 ro single
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
UUID=e02d9afe-2c70-41c7-8108-4ea3c49ff627 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=21388adf-48b7-4d29-9f03-8079289fedfb none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 108.1GB: boot/grub/core.img
 108.2GB: boot/grub/grub.cfg
  44.7GB: boot/initrd.img-2.6.35-22-generic
 319.4GB: boot/initrd.img-2.6.35-28-generic
 108.1GB: boot/vmlinuz-2.6.35-22-generic
 108.1GB: boot/vmlinuz-2.6.35-28-generic
 319.4GB: initrd.img
  44.7GB: initrd.img.old
 108.1GB: vmlinuz
 108.1GB: vmlinuz.old
```

---

### Post by Hedgehog1 on 2011-03-31
bigred1,

You have a mish-mash of various Ubuntu installs:

/dev/sda1    W95 FAT32 (LBA)
/dev/sda2    Extended Partition (Contains sda5-sda9)
[COLOR="Red"][B]__/dev/sda5    Linux < Abandoned > 
__/dev/sda6    Linux swap / Solaris < Abandoned >
__/dev/sda7    Linux < Abandoned >[/B][/COLOR]
[B]__/dev/sda8    Linux < In Use >
__/dev/sda9    Linux swap / Solaris < In Use >[/B]
/dev/sda3    HPFS/NTFS
/dev/sda4    Compaq diagnostic

Partitions sda5-sda7 do not appear to be used at this time.

Also, your boot menu does have: "Windows Vista (loader) (on /dev/sda4)" in it - but you have so many kernals listed that you may need to scroll down to find the "Windows Vista (loader) (on /dev/sda4)" entry.

I would suggest:

1) Remove any hand entries you made in grub
2) Using gparted delete sda5, sd6 & sda7
3) Update the grub menu, it should get shorter:

```
sudo update-grub
```

4) Removing all but the 2 most recent kernels
5) 2) Update the grub menu, it should get even shorter:

```
sudo update-grub
```

You can then expand /dev/sda8 to use all the left over space in the /dev/sda2 extended partiton.

***The Hedge***

:KS

---

### Post by oldfred on 2011-03-31
+1 on everything from The Hedge

Grub's os-prober or Vista mis report main install & recovery. Even though it says Vista on sda4, it is your recovery.

You main Vista install in sda1 looks correct except it starts at sector 63. New installs of windows since Vista and Linux recently all start at 2048. Did you use an older copy of gparted to move/resize the Vista partition? That sometimes moved that start from 2048 to 63 and confuses Vista as boot sector has to have same info as to start sector. If that is the case you just need to run Winodws repairs on the Vista partition sda1. If you run the auto repairs it may install its boot loader to the MBR, then you would be able to test that it works directly but also then have to reinstall grub2.

More info on running Vista/7 repairs if need be.
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bigred1 on 2011-04-01
Thank you oldfred and Hedgehog1. The Repair function  in the Windows 7 installation DVD fixed the problem immediately, without changing my grub2 setup. After this, I can book Windows 7 from the entry (hd0,1) . This is apparently the first partition, the one which Windows7 favors for booting, even though the third partition is where Windows 7 actually resides.

As to the bunch of useless partitions: Yes, there are too many. They don't do any harm other than cluttering up the disk (what's 50 GB here or there in today's world).  But I will clean them up.

The machine came with FreeDOS, Lenovo's equivalent of "No Operating System," as well as a Windows Vista repair partition; there are also 2 partitions there from a failed Ubuntu installation. 

There is also  W95 FAT32 (LBA). I don't know what that is for, but it is serving for now to boot, so I suppose I will keep it.

As to the extra kernels: I'll clean up the Grub2 menu.

---

### Post by Hedgehog1 on 2011-04-01
Glad you are operational again.

As long as you are functional - that is what matters. Clean up is nice, as time permits. :D

***The Hedge***

:KS

---

