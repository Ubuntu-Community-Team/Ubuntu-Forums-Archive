---
title: "Ubuntu 10.04 / Windows 7 bad combination"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by sambatyon.abulafia on 2010-06-12
Hi, I have a computer with a dual boot configuration. I have no problems booting linux but as soon as I boot windows the catastrophe begins. 

First windows 7 will boot without problems but when I turn off the computer and boot again the boot loaders are gone, I either get the message "BOOTMGR is missing" or "NTLDR is missing." of course I would only need to use the windows installation dvd and run bootrec and then use the ubuntu cd to reinstall grub. The problem is this takes quite a long time and I need the dual boot (since I need widows for my job and rather use ubuntu for my home).

Any Ideas?

---

### Post by wilee-nilee on 2010-06-12
Post this boot script in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

be sure to post with the cod tags otherwise it is hard to read it is a lot of text.

---

### Post by sambatyon.abulafia on 2010-06-12
Interesting enough, sdb is an external drive and I don't know when its mbr was written (I guess some time trying to fix the boot loader)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   489,784,699   458,984,375   7 HPFS/NTFS
/dev/sda4         489,785,342   976,771,071   486,985,730   5 Extended
/dev/sda5         489,785,344   505,409,535    15,624,192  82 Linux swap / Solaris
/dev/sda6         505,411,584   585,488,383    80,076,800  83 Linux
/dev/sda7         585,490,432   976,771,071   391,280,640  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,127 1,953,520,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        9E68249F682477E3                       ntfs       RECOVERY                      
/dev/sda3        CC28269A28268394                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f34e7021-538d-4e9d-8271-f286044df889   swap                                     
/dev/sda6        7013b966-9a34-4872-9031-372129f7d97a   ext4                                     
/dev/sda7        d0f84f5f-a227-4f03-9866-6eeaa20aacbe   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        52DCB673DCB650C9                       ntfs       Expansion Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sdb1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7013b966-9a34-4872-9031-372129f7d97a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7013b966-9a34-4872-9031-372129f7d97a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7013b966-9a34-4872-9031-372129f7d97a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7013b966-9a34-4872-9031-372129f7d97a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7013b966-9a34-4872-9031-372129f7d97a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 9e68249f682477e3
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 52dcb673dcb650c9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7013b966-9a34-4872-9031-372129f7d97a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d0f84f5f-a227-4f03-9866-6eeaa20aacbe /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f34e7021-538d-4e9d-8271-f286044df889 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 284.6GB: boot/grub/core.img
 276.5GB: boot/grub/grub.cfg
 284.8GB: boot/initrd.img-2.6.32-21-generic
 285.2GB: boot/initrd.img-2.6.32-22-generic
 284.6GB: boot/vmlinuz-2.6.32-21-generic
 267.1GB: boot/vmlinuz-2.6.32-22-generic
 285.2GB: initrd.img
 284.8GB: initrd.img.old
 267.1GB: vmlinuz
 284.6GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-06-12
There is a dell data save program that is probably the root of this problem and this can be removed when everything is set back up. I thought you were missing some boot files but I think that sda2 and 3 are working together as sda2 seems to be the recovery.

For the time being here is a link to the dell program problem.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

It sounds like you have the install dvd for W7 is this correct?

You have a fixable situation but probably will need a person more experienced with this setup, and problem. The good thing is that they will be on line within a couple of hours if things go as usual. There are others who can do these fixes but there are a handful of regulars who take care of most problems.

Also is sdb a data partition is this also correct?

It may be that the instructions in the link that entail the reloading of the W7 boot then booting into W7 and removing the data safe program from add remove programs then just reloading grub to sda will fix the problem. Also taking the boot flag off of sdb would be what I would do if it is not for booting. I think we should wait for some confirmation of this though just to make sure.

---

### Post by sambatyon.abulafia on 2010-06-12
That might be the problem. I will reboot as soon as I can and uninstall this dell program and post what happens. Once again, thanks

---

### Post by wilee-nilee on 2010-06-12
> **sambatyon.abulafia said:**
> That might be the problem. I will reboot as soon as I can and uninstall this dell program and post what happens. Once again, thanks

I have the feeling you know what to do if you know how to load the W7 bootloader and grub2. There are no actual boot files in sdb so I don't think it is a problem.

---

### Post by sambatyon.abulafia on 2010-06-12
Well, I was talking about the dell software… ;) about the loader in sdb, I think it sometimes comes in handy. Has help me to boot when everything was screwed up and I needed to google something fast.

---

### Post by wilee-nilee on 2010-06-12
> **sambatyon.abulafia said:**
> Well, I was talking about the dell software… ;) about the loader in sdb, I think it sometimes comes in handy. Has help me to boot when everything was screwed up and I needed to google something fast.

I might be wrong but you would have too do a specialized removal of the 1st 512mb of sdb if you wanted to remove it, which you don't need to, nor do you want to. I think it boots from sdb as it is reading sda2. If you get grub set up so it stays you should be set. But as I said all along I really like to have others confirm this stuff, but you seem to have a grasp of the situation, and knowing about the oh so pleasant dell data safe program is helpful if that is what the booting problem is in general.

So I am not telling you to remove anything, and I don't think even having sdb as active with the bootflag still on is a problem if sda is 1st in line to boot.

---

