---
title: "GRUB rescue&gt;"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by brewerswin28 on 2011-06-19
I am an absolute beginner to linux and I am pretty sure i got in way over my head... I thought it would be cool to have two OS's on my PC and decided to install ubuntu.  Instead of installing them side by side on the same main hard drive, i got an external drive and installed it on that drive.  Now, when i start up my PC, i get a "GRUB Rescue" message and i cannot boot windows 7 or ubuntu.  The only thing that i can do is to run ubuntu off of the usb thumb drive that i installed it off of.  I have tried to go into the boot menu at startup and choose either of the drives that come up, but every one of them (with the exception of the usb thumb drive) gives me the error.   Hopefully someone out there knows how to solve this issue with the GRUB bootloader and can help me out.  Thanks ahead of time for any help!!!

---

### Post by Quackers on 2011-06-19
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by brewerswin28 on 2011-06-20
Thanks for the response!  I did what you said and the results text file is as follows:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

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

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 7808 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 2,903,957,594 2,903,750,747   7 NTFS / exFAT / HPFS
/dev/sda3       2,903,963,648 2,930,274,303    26,310,656   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2038 MB, 2038431744 bytes
251 heads, 62 sectors/track, 255 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     3,981,311     3,981,248   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048         4,095         2,048 BIOS Boot partition
/dev/sdc2           4,096 3,887,992,831 3,887,988,736 Data partition (Windows/Linux)
/dev/sdc3   3,887,992,832 3,907,028,991    19,036,160 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5A64D6C264D6A055                       ntfs       SYSTEM
/dev/sda2        08B68F82B68F6ECE                       ntfs       OS
/dev/sda3        6E9234719234403F                       ntfs       HP_RECOVERY
/dev/sdb1        DC21-5C47                              vfat       PENDRIVE
/dev/sdc2        73358383-25fe-4018-9914-dc10eea36824   ext4       
/dev/sdc3        016bc67d-b87f-4255-835e-43f6fbeca6ac   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc2        /media/73358383-25fe-4018-9914-dc10eea36824 ext4       (rw,nosuid,nodev,uhelper=udisks)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=========================== sdc2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,2)'
search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,2)'
search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=73358383-25fe-4018-9914-dc10eea36824 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
    echo    'Loading Linux 2.6.32-32-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=73358383-25fe-4018-9914-dc10eea36824 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,2)'
    search --no-floppy --fs-uuid --set 73358383-25fe-4018-9914-dc10eea36824
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5a64d6c264d6a055
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 6e9234719234403f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc2 during installation
UUID=73358383-25fe-4018-9914-dc10eea36824 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc3 during installation
UUID=016bc67d-b87f-4255-835e-43f6fbeca6ac none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 284.140308380 = 305.093332992  boot/grub/core.img                             1
 954.293483734 = 1024.664825856 boot/grub/grub.cfg                             1
 284.147693634 = 305.101262848  boot/initrd.img-2.6.32-32-generic-pae          1
 284.138645172 = 305.091547136  boot/vmlinuz-2.6.32-32-generic-pae             1
 284.147693634 = 305.101262848  initrd.img                                     1
 284.138645172 = 305.091547136  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg

---

### Post by nzjethro on 2011-06-20
Woah, that looks unattractive. If you run into these issues again, make sure you post the results in code tags, by clicking the # at the top of the reply box, then pasting your reply between the [code][code] tags. This retains all the formatting, and makes it easier to deduce the problem. :)

As for the problem, from what I can see (and I'm still pretty new to this, but I've sorted out my own GRUB issues a few times), you have no boot files on your external HDD (where you installed Ubuntu). What probably happened is that you installed Grub to sda (your primary partition), rather than your external partition.

Never fear, we can solve the problem! To fix it, check out Section 13 of [this]("http://ubuntuforums.org/showthread.php?t=1195275") handy guide. Where it refers to sdXY in the tutorial, substitute your Ubuntu disk for XY (i.e. use sdc). Run through that, and if it doesn't work, note any error messages and post them back here.

---

### Post by brewerswin28 on 2011-06-21
I went to section 13 of that guide as you instructed and i got a few errors when trying to work through it.  I copied the text directly from the terminal for you to see what sort of messages i received.  

```

ubuntu@ubuntu:~$ sudo mount /dev/sdc /mnt
mount: /dev/sdc already mounted or /mnt busy
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount/ dev/sdc1/mnt/boot
sudo: mount/: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/boot
mount: mount point /mnt/boot does not exist

```

---

### Post by YesWeCan on 2011-06-21
Hi brewerswin28,
I can explain what might have happened. Installing Ubuntu to an external HD is exactly the right thing to do. Unfortunately, the Ubuntu Installer defaults to putting the Grub MBR code on /dev/sda (your Windows disk) and it doesn't make this clear or give you any warnings at all. Which is pretty annoying for a lot of people.

You cannot boot Windows because you cannot boot Grub because Grub cannot boot the USB drive. Which is a GPT drive which may be complicating things.

First things first. Restore the standard MBR code to your Windows disk so Windows will boot again. There are two ways:
1) Boot your Windows CD and run a fixmr(?) utility (recommended).
2) Boot USB stick Ubuntu and do
[COLOR="Navy"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]
Ignore any warnings.

Then you should be able to boot Windows again.
While you do that I'll research how to reinstall Grub to your GPT external HD.

---

### Post by YesWeCan on 2011-06-21
BTW, can you boot the external HD directly using the bios? Does it boot?

---

### Post by brewerswin28 on 2011-06-22
thanks a lot!!! :p i was able to start up windows using the code u gave me 
```
[COLOR=#000080]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]
 
```
 
 
Have you found anything yet on how to boot ubuntu from my external hd and install GRUB correctly?  I have been looking as well, but i havent found anything that looks close enough to what i'm trying to do.

---

