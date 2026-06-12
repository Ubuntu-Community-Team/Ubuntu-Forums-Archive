---
title: "&quot;gave up waiting for root device&quot;"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by stork123 on 2010-05-26
I have a Toshiba NB305 netbook running windows 7. I installed netbook ubuntu 10.04 from a USB drive this morning after playing with the live ISO off the USB. I chose to repartition and keep Windows 7.
Upon boot, I get GRUB and when I choose either the Ubuntu or the Recovery I get a "gave up waiting for root device" page with a command prompt flashing at initiramfs.

The Alert reads, "/dev/disk/by-uuid/49024e15-119a-4339-ad23-f201ce4a6d1f does not exist. Dropping to Shell!

I'm still able to boot windows 7 as well as the live cd and see all the partitions and operating systems.

I've looked inside the Grub.cfg file and the commands aren't pointing to /dev/sda5/ but rather to the uuid? Is this normal? Does this need to be changed?

Thanks for your help.

In the meantime... I will continue to search the forums.
I will run this script and try and get some more info.

[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by darkod on 2010-05-26
It's not exactly the same message but see if this helps:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by stork123 on 2010-05-26
I'll try it right now.
thanks!

Nope.. same error.
I'm not familiar with editing the lines within the GRUB menu.

I deleted the line and then CTRL-X to boot (same issue).
I went back into the GRUB menu and saw that the line was back. Did I actually delete it?

---

### Post by darkod on 2010-05-26
> **stork123 said:**
> I'll try it right now.
thanks!

Nope.. same error.
I'm not familiar with editing the lines within the GRUB menu.

I deleted the line and then CTRL-X to boot (same issue).
I went back into the GRUB menu and saw that the line was back. Did I actually delete it?

When you use 'e' to edit from the grub menu, it is temporary, only for that boot. If that worked, the article says how to make it permanent change.
But if you are sure you followed the steps correctly and it didn't work, no point in continuing with the fix. It seems you have different issue.

---

### Post by stork123 on 2010-05-26
Okay... 
Would it help for me to run bootinfo script?

---

### Post by darkod on 2010-05-26
It could help us notice something. But I'm not too optimistic, it seems you did everything right. It seems one of 'those strange things'...
Run it, and lets see the results.

---

### Post by stork123 on 2010-05-26
running it now...
if this fails... maybe reinstalling from the USB?

Here's the log


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   258,728,939   255,654,892   7 HPFS/NTFS
/dev/sda3         470,738,944   488,396,799    17,657,856  17 Hidden HPFS/NTFS
/dev/sda4         258,729,982   470,738,943   212,008,962   5 Extended
/dev/sda5         258,729,984   464,785,407   206,055,424  83 Linux
/dev/sda6         464,787,456   470,738,943     5,951,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
16 heads, 32 sectors/track, 7644 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,913,727     3,905,664   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E3699DB3699950D                       ntfs       System                        
/dev/sda2        641ABF8A1ABF57AE                       ntfs       TI105803W0C                   
/dev/sda3        C824E4F324E4E602                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        49024e15-119a-4339-ad23-f201ce4a6d1f   ext4                                     
/dev/sda6        469d04d8-78b4-4009-b845-7f9e37aa945d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2F8C-A26B                              vfat       TRAVELDRIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=49024e15-119a-4339-ad23-f201ce4a6d1f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=49024e15-119a-4339-ad23-f201ce4a6d1f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 49024e15-119a-4339-ad23-f201ce4a6d1f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e3699db3699950d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 641abf8a1abf57ae
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set c824e4f324e4e602
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=49024e15-119a-4339-ad23-f201ce4a6d1f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=469d04d8-78b4-4009-b845-7f9e37aa945d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 214.2GB: boot/grub/core.img
 214.2GB: boot/grub/grub.cfg
 214.2GB: boot/initrd.img-2.6.32-21-generic
 214.2GB: boot/vmlinuz-2.6.32-21-generic
 214.2GB: initrd.img
 214.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 28 48 0c 00 fe  |...........(H...|
000001d0  ff ff 05 fe ff ff 02 28  48 0c 00 d8 5a 00 00 00  |.......(H...Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by darkod on 2010-05-26
I can't see anything wrong with it. Sorry.

---

### Post by stork123 on 2010-05-26
okay... thanks.
I'm gonna try and reinstall from the thumbdrive over the existing partition.
Question for you if you have a sec.
I'd like to clone my windows partition to use as a backup incase I blow it all out.
I'm sure this is discussed here - looking around now.
Got a link for that?

I'd like to make a bootable usb of my existing windows 7 starter as a plan b?

---

### Post by darkod on 2010-05-26
Not sure about bootable usb, but you can clone partitions (both windows and linux) with CloneZilla.

It comes as image for live cd or live usb I think. You can boot with it, similar to ubuntu live mode, and clone the partition(s) you want to external hdd for example.

---

### Post by stork123 on 2010-05-26
" eventually I discovered that changing the BIOS SATA Controller Mode from AHCI to Compatibility allowed Ubuntu to boot"

This was the trick...

Still needs some tweaking.
Thanks for all your help!

---

### Post by zachstauffer on 2010-06-30
Sorry for bumping an old thread, but I have the same problem. When I change the SATA controller to IDE Ubuntu will boot, but Windows 7 will not. When I change it back to AHCI Windows boots, but Ubuntu will not. Anybody have an idea of what to do?

Thanks in advance!

---

### Post by C. M .Hughes on 2010-08-26
I, too, apologize for bumping an old thread, but I have had exactly the same issues. I've tried re-installing twice to no avail. 

The BIOS switch had the same results for me as reported by zachstauffer.

---

### Post by zachstauffer on 2010-08-26
Hope this helps, but I fixed my problem by flashing my bios with an updated version. Then I was able to boot UNR in AHCI.

---

### Post by kenorb on 2010-09-16
See those bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
[https://bugs.launchpad.net/ubuntu/+bug/579572](https://bugs.launchpad.net/ubuntu/+bug/579572)

---

