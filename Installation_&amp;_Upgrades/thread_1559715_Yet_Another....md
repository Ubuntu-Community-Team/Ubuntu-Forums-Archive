---
title: "Yet Another..."
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by _minnE on 2010-08-23
...dual boot problem. I installed Ubuntu and used it for 2 days, but after using Windows 7 just once (I'm assuming it's being bossy) I get another grub issue...

[B]error: unknown filesystem
grub rescue>[/B]

Keep in mind that I'm somewhat of a noob when it comes to GNU/Linux! :P

---

### Post by wilee-nilee on 2010-08-23
> **_minnE said:**
> ...dual boot problem. I installed Ubuntu and used it for 2 days, but after using Windows 7 just once (I'm assuming it's being bossy) I get another grub issue...

[B]error: unknown filesystem
grub rescue>[/B]

Keep in mind that I'm somewhat of a noob when it comes to GNU/Linux! :P

If you have a Dell check this link.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

To reinstall grub2 from a cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

This is assuming that you don't have a wubi install but installed from a live booted Ubuntu cd.

You can also post the bootscript in my sig in code tags as described, for more help.

---

### Post by _minnE on 2010-08-23
After doing step 5 I get an error (non-Dell)... btw, what is bootscript for?

Is it possible to not use grub? 
A long time ago when I first tried  Ubuntu, I used what seemed to be a boot loader from Windows (or so I  think).

---

### Post by _minnE on 2010-08-23
](*,)

---

### Post by oldfred on 2010-08-24
Boot script runs a bunch of command and outputs a nice report of your configuration so we can figure out what might be wrong.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

I do not recommend neosmarts easybcd, but some windows purist prefer it.
[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)
Why not easyBCD
[http://ubuntuforums.org/showthread.php?t=1554155](http://ubuntuforums.org/showthread.php?t=1554155)

---

### Post by _minnE on 2010-08-24
After I do step 5 and enter[B] 

sudo grub-install --root-directory=/mnt/ /dev/sda3[/B] 

I get this:

[B]/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..

/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..

/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

ubuntu@ubuntu:~$

[/B]Btw, thanks to everyone for the help so far, I might do easyBCD but I'm not giving up quite yet :)

---

### Post by wilee-nilee on 2010-08-24
> **_minnE said:**
> After I do step 5 and enter[B] 

sudo grub-install --root-directory=/mnt/ /dev/sda3[/B] 

I get this:

[B]/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..

/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..

/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

ubuntu@ubuntu:~$

[/B]Btw, thanks to everyone for the help so far, I might do easyBCD but I'm not giving up quite yet :)

From this information; trying to install grub to a partition and mention of mystery 5th step I say stop what your doing and **[COLOR="Red"]post the bootscript[/COLOR]**. This may be a easy fix but not without the appropriate information.

---

### Post by _minnE on 2010-08-24
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,387,313,633 1,387,311,586   7 HPFS/NTFS
/dev/sda2       1,387,315,200 1,403,699,199    16,384,000   7 HPFS/NTFS
/dev/sda3       1,403,701,248 1,465,143,295    61,442,048  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   569,539,727   569,539,665   c W95 FAT32 (LBA)
/dev/sdb2         569,540,608   625,137,663    55,597,056   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8153 MB, 8153726976 bytes
33 heads, 16 sectors/track, 30161 cylinders, total 15925248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             80    15,925,247    15,925,168   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7AB0473DB046FF5F                       ntfs                                     
/dev/sda2        28768C2F768BFBB6                       ntfs       _SHARED                       
/dev/sda3        71e37a45-9bf9-4c54-a5c0-2cb9035cadad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AA9D-F0BC                              vfat       _EXSHELL                      
/dev/sdb2        CCBF-AEBB                              vfat       _INSHELL                      
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        9422-78DB                              vfat       UDISK                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /mnt                     ext4       (rw)
/dev/sdd1        /media/UDISK             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/7AB0473DB046FF5F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=71e37a45-9bf9-4c54-a5c0-2cb9035cadad ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=71e37a45-9bf9-4c54-a5c0-2cb9035cadad ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 71e37a45-9bf9-4c54-a5c0-2cb9035cadad
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7ab0473db046ff5f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 720.9GB: boot/grub/core.img
 734.0GB: boot/grub/grub.cfg
 721.1GB: boot/initrd.img-2.6.32-24-generic-pae
 720.9GB: boot/vmlinuz-2.6.32-24-generic-pae
 721.1GB: initrd.img
 720.9GB: vmlinuz

---

### Post by wilee-nilee on 2010-08-24
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #2 for /boot/grub.

As of now the boot loader is looking at the wrong partition. If this is a HP they also have a program like the Dell data safe that causes problems.

To get the boot correct from a live Ubuntu cd in the terminal run.
```
sudo mount /dev/sda3 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Reboot and run
```
sudo update-grub
```
in Ubuntu if it boots.

I would check online with the computer model and this boot problem. It may have just been a anomaly, hard to say. I also notice you have no swap partition did you intend this?

Here is the link for reloading grub2
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by _minnE on 2010-08-24
Do I try to run the last code in Ubuntu on my hard drive or from LiveCD?

---

### Post by wilee-nilee on 2010-08-24
> **_minnE said:**
> Do I try to run the last code in Ubuntu on my hard drive or from LiveCD?

The first 2 are from the live cd, the sudo update-grub is from the hopefully booted Ubuntu.

---

### Post by _minnE on 2010-08-24
It worked this time! Thank you so much for your time and help! :D

---

### Post by wilee-nilee on 2010-08-24
> **_minnE said:**
> It worked this time! Thank you so much for your time and help! :D

Yay that's great, save that link for reloading grub2 in case you have problems again the commands I gave you were from right where it defaults when you open it.

---

