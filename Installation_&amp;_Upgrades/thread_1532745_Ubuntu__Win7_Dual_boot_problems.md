---
title: "Ubuntu / Win7 Dual boot problems"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by niicky on 2010-07-16
Hi All,

I've had some serious problems installing ubuntu on my new PC. Initially I suspected I had burnt a poor version of 10.04 and re-downloaded it and installed again. Both times ubuntu would think for a while and then provide the below message

> Installation Failed
--------------------
The installer encountered an unrecoverable error. A desktop session will now be started so that you may investigate the problem or try installing again.

It would then take me into the live CD version and I installed fine, however, after the initial install apparently my password was wrong so I couldn't get in to test. On top of this I have attempted to install 9.10 (which I'm doing as I type this).

When 9.10 was last installed. I was not provided a boot loader and ubuntu was booted straight up, I thought, that's fine I'll let it continue but this is really not acceptable to me.

EDIT: I have now installed 9.10, the bootloader appears but when I select windows I receive a flashing underscore. And windows fails to load.

I've never had problems like this with Ubuntu before and am very confused and not sure where to start. All i want to be able to do is dual boot.

If anyone has any advise or experience dealing with this please let me know

---

### Post by Michael__ on 2010-07-16
Hey, just wanted to let you know that I am having this same problem, and apparently started a thread only 20 minutes before you did!

[http://ubuntuforums.org/showthread.php?p=9599250#post9599250](http://ubuntuforums.org/showthread.php?p=9599250#post9599250)

Might want to keep an eye on my thread; I'll certainly be watching yours.

---

### Post by confused57 on 2010-07-16
Found this with a Google search:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Desktop%20installer%20sometimes%20crashes%20on%20startup](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Desktop%20installer%20sometimes%20crashes%20on%20startup)
May or may not be applicable in your case.

---

### Post by niicky on 2010-07-17
Thanks alot for that confused. Looks like your googling is much better than mine.

I'm fairly sure there's something wrong with my grub bootloader and it not pointing to the correct boot area for the windows partition.

---

### Post by confused57 on 2010-07-17
> **niicky said:**
> Thanks alot for that confused. Looks like your googling is much better than mine.

I'm fairly sure there's something wrong with my grub bootloader and it not pointing to the correct boot area for the windows partition.

I really misread your initial post, you were able to get Lucid installed and are having problems booting Windows(and have 9.10 installed).  The best thing to do is run the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
There's the possibility that grub2 is installed to the boot sector of your Window's partition.  If this is the case, here's a fix from meierfra, using testdisk:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I bookmarked this post from oldfred for using bootrec to repair Win7:
[http://ubuntuforums.org/showpost.php?p=9555621&postcount=13](http://ubuntuforums.org/showpost.php?p=9555621&postcount=13)

I just happened to check the forums before hitting the sack and saw your post, but this should give you something to check that might be causing your Window's boot problems.

---

### Post by niicky on 2010-07-17
Hi Confused, looks like you might be right, Grub has installed in the ntfs partition of windows. I'll try this fix and see what happens. Thanks for your help so far.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1670273090 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1670259122 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1670281610 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b4083cd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,250,260,991 1,250,054,144   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3656fdc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,738,283,297 1,738,281,250   7 HPFS/NTFS
/dev/sdb2       1,738,297,260 1,953,520,064   215,222,805   5 Extended
/dev/sdb5       1,738,297,323 1,944,684,314   206,386,992  83 Linux
/dev/sdb6       1,944,684,378 1,953,520,064     8,835,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D6D03182D0316A3F                       ntfs       System Reserved               
/dev/sda2        A4F63BC5F63B9690                       ntfs                                     
/dev/sdb1        4E90F00990EFF4FD                       ntfs       Storage                       
/dev/sdb5        f683d661-a081-47eb-9e8f-ceb3549e05c2   ext4                                     
/dev/sdb6        b7d30b89-3e2c-4228-93ab-9635bf81af51   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set f683d661-a081-47eb-9e8f-ceb3549e05c2
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f683d661-a081-47eb-9e8f-ceb3549e05c2
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f683d661-a081-47eb-9e8f-ceb3549e05c2
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f683d661-a081-47eb-9e8f-ceb3549e05c2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set f683d661-a081-47eb-9e8f-ceb3549e05c2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d6d03182d0316a3f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f683d661-a081-47eb-9e8f-ceb3549e05c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b7d30b89-3e2c-4228-93ab-9635bf81af51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 895.2GB: boot/grub/core.img
 895.9GB: boot/grub/grub.cfg
 890.2GB: boot/initrd.img-2.6.31-14-generic
 890.3GB: boot/initrd.img-2.6.31-22-generic
 890.2GB: boot/vmlinuz-2.6.31-14-generic
 890.2GB: boot/vmlinuz-2.6.31-22-generic
 890.3GB: initrd.img
 890.2GB: initrd.img.old
 890.2GB: vmlinuz
 890.2GB: vmlinuz.old
```

---

### Post by niicky on 2010-07-17
Confused, you are a god.

:) it looks like it's been fixed.

---

### Post by confused57 on 2010-07-17
Good to hear you're able to boot Windows now.  

I hope it's changed with the release of the 10.04.1 live cd installer, but the current 10.04 live cd installer suggests installing the grub bootloader to all  partition boot sectors if you're unsure of where to install it.  This has rendered Windows unbootable for more than a few users dual booting with Ubuntu, thanks to meierfra and others for providing instructions for repairing the misinformation of the installer.  I only use the alternate installer, but I assume the desktop installer has this option if the "Advanced" button is selected for installing grub.

---

