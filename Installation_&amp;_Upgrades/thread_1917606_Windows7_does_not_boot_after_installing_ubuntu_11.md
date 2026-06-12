---
title: "Windows7 does not boot after installing ubuntu 11"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by snimavat on 2012-01-30
I had an issue of windows not booting after dual booting with ubuntu 11, I can see the windows 7 entry in boot menu, but clicking on it would show the boot menu again after a splash, then i tried windows recovery bootrec /fixmbr and bootrec /fixboot options, but none of them worked and it every caused the ubuntu to stop working, Then I tried testdisk utility, that fixed ubuntu and i was able to load ubuntu, and then I modified the boot/grub/custom.cfg and now i can boot both windows and ubuntu, but now windows has dependency on ubuntu so i can not remove ubuntu if ever i have to. Does any one has any idea about how do I fix it cleanly and restore my boot stuff to the stable state. 

Here's all the details 

[http://askubuntu.com/questions/99584/windows-7-wont-boot-after-installing-ubuntu-11](http://askubuntu.com/questions/99584/windows-7-wont-boot-after-installing-ubuntu-11)

Note : I still have a windows 7 entry in bootmenu (In addition to the one I add manually to /boot/grub/custom.cfg), clicking on it does not boot windows, I get a blank screen with blinking cursor.

My question is
- How do I fix the windows bootloader - so that I dont need the /boot/grub/custom.cfg and the default "windows 7" entry in bootmenu works.  So that I dont have dependency on ubuntu and my windows would work if ever I have to remove ubuntu.

---

### Post by pawhtiobo on 2012-01-30
Hi :)

Just use the Windows 7 DVD, boot and fix the startup, it should work for Windows 7, but if you have a dual boot you need the grub boot loader, i dont know another way to do so, one way is to have separated HDD's and you can choose from BIOS the HDD to boot from.

See ya...

---

### Post by snimavat on 2012-01-30
"Fix start up issue" from win7 DVD does not resolve issue - Neither bootrec /fixmbr or bootrec /fixboot

---

### Post by raja.genupula on 2012-01-30
[http://ubuntuforums.org/showthread.php?t=1915350&page=2](http://ubuntuforums.org/showthread.php?t=1915350&page=2)

try this with mentioned settings in bios .

if its not worked then please post the output of bootinfoscript(look at my signature)

---

### Post by snimavat on 2012-01-30
I have just one HDD -

Here's my boot info

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 928345056 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   835,794,798   835,792,751   7 NTFS / exFAT / HPFS
/dev/sda2       1,226,758,144 1,436,471,295   209,713,152   7 NTFS / exFAT / HPFS
/dev/sda3       1,436,473,344 1,465,145,343    28,672,000   7 NTFS / exFAT / HPFS
/dev/sda4         835,794,942 1,226,758,143   390,963,202   5 Extended
/dev/sda5         835,794,944 1,210,200,063   374,405,120  83 Linux
/dev/sda6       1,210,202,112 1,226,758,143    16,556,032  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FAF0F57DF0F54085                       ntfs       OSDisk
/dev/sda2        20B87D6EB87D4378                       ntfs       work
/dev/sda3        CA56F69A56F6868B                       ntfs       Recovery
/dev/sda5        6a578263-e032-41d0-b3dd-48bc4117eb3e   ext4       
/dev/sda6        52ff7de4-2d64-4305-b178-f778cf3e0900   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/OSDisk            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a578263-e032-41d0-b3dd-48bc4117eb3e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=6a578263-e032-41d0-b3dd-48bc4117eb3e ro recovery nomodeset 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 6a578263-e032-41d0-b3dd-48bc4117eb3e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root FAF0F57DF0F54085
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6a578263-e032-41d0-b3dd-48bc4117eb3e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=52ff7de4-2d64-4305-b178-f778cf3e0900 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 442.669490814 = 475.312746496  boot/grub/core.img                             1
 442.669425964 = 475.312676864  boot/grub/grub.cfg                             1
 400.793060303 = 430.348271616  boot/initrd.img-3.0.0-12-generic               2
 442.676876068 = 475.320676352  boot/vmlinuz-3.0.0-12-generic                  1
 400.793060303 = 430.348271616  initrd.img                                     2
 442.676876068 = 475.320676352  vmlinuz                                        1

=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".



```

---

### Post by carl4926 on 2012-01-30
You would need to delete the logical and extended partitions
Resize sda1 to take back the space
Use the win7 dvd to repair the MBR

> Win7 Boot repair:
Boot off the windows 7 installation DVD
Proceed to the screen "Windows 7 / Install Now" BUT DO NOT click to install
Select to "Repair your computer"
Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next
Select "command prompt"
enter this command: Bootrec.exe /FixBoot
enter this command: Bootrec.exe /FixMbr
enter this command: exit
Click to Restart 

---

### Post by oldfred on 2012-01-30
Window fixboot may not work as it has to see a NTFS partition. While partiton table says sda1 is, your install of grub2's boot loader to the PBR - partition boot sector has corrupted Windows. You can recover it with testdisk if the backup is ok. 

> sda1: ______________________________________

    File system:       ntfs
    [COLOR=Red]Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 928345056 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block[/COLOR].
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

### Post by snimavat on 2012-01-31
> **oldfred said:**
> Window fixboot may not work as it has to see a NTFS partition. While partiton table says sda1 is, your install of grub2's boot loader to the PBR - partition boot sector has corrupted Windows. You can recover it with testdisk if the backup is ok. 



Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

I have already tried testdisk and it has not resolved the issue. However it fixed the grub and bootmenu which was otherwise broken when I did bootrec /fixmbr - that details is [here]("http://askubuntu.com/questions/99584/windows-7-wont-boot-after-installing-ubuntu-11")

---

