---
title: "dual boot lubuntu winxp problem"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by wallygator.uk on 2011-05-12
hi everyone, just installed lubuntu 11.04 in parallel to an old winxp installation.

right, before the installation i had a very old and redundant winxp installation on drive C, and a newer one which i normally used on drive F. So there was a winxp/winxp dual boot. Boot files if i remember were on drive c, as it was the first one to be installed.

Now i installed lubuntun on drive c (sda1) and have the remaining winxp on sda5

Grub won't even show up the boot page, and log directly.

I read for the last 2 hrs on this particular problem and done everything suggested. the file os-something is present on the system but a update-grub still does not find the winxp partition.

bear in mind that i can mount it and read files, but don't think there is any boot on there. here is the results.txt, hope somebody can help.

I think that I compromised the boot of the winxp when i formatted the drive c sda1 with lubuntu. 

As i still need to do work on xp, the only thing that i can think of is to restore boot and mbr on the xp and then reinstall grub..

.. unless somebody suggest me otherwise

grazie

---

### Post by Quackers on 2011-05-12
So does Lubuntu boot directly? If so run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is picked up. If it is reboot and you should get a grub menu with the choice of system to boot.
If update-grub doesn't find Windows open up synaptic package manager and enter in the search box os-prober. It will appear in the main window. It should have a green box to its left. Sometimes it doesn't install with Lubuntu. Right-click it and select "mark for installation" then click on the green tick mark in the toolbar to apply the change. 
When it is installed close synaptic and go back to the terminal and run sudo update-grub again and this time it should pick up the Windows Loader.

---

### Post by wallygator.uk on 2011-05-13
thanks for your reply, i've done all the above, os-prober is installed, but it does not find win, as said probably the win loader is missing.

the thing is, when booting it does not ever show the screen where you can select the standard kernel or the recovery mode, it goes straight to lubuntu splash screen.

here is the results.txt which i forgot to attached yesterday

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 64211868.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,246,424    31,246,362  83 Linux
/dev/sda2          31,455,331    78,140,159    46,684,829   5 Extended
/dev/sda5          31,455,333    62,171,549    30,716,217   7 HPFS/NTFS
/dev/sda6          62,171,613    64,211,804     2,040,192  82 Linux swap / Solaris
/dev/sda7          64,211,868    78,140,159    13,928,292   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b52538c9-fe52-4c86-bb1e-6fd52a6483fd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8E08530D0852F425                       ntfs                                     
/dev/sda6        a1f9a182-6c78-43ce-93e1-105506229f85   swap                                     
/dev/sda7        4787-4A28                              vfat       éëÿÿ¹œº                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/8E08530D0852F425  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b52538c9-fe52-4c86-bb1e-6fd52a6483fd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b52538c9-fe52-4c86-bb1e-6fd52a6483fd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root b52538c9-fe52-4c86-bb1e-6fd52a6483fd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
# swap was on /dev/sda6 during installation
UUID=a1f9a182-6c78-43ce-93e1-105506229f85 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/core.img
   4.6GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.38-8-generic
  10.8GB: boot/vmlinuz-2.6.38-8-generic
    .9GB: initrd.img
  10.8GB: vmlinuz

---

### Post by wallygator.uk on 2011-05-13
this is the result of update-grub


gualtiero@lubuntu-lap:~$ sudo update-grub
[sudo] password for gualtiero: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
gualtiero@lubuntu-lap:~$ 


as said, the grub panel does not show at all, it goes straight into lubuntu splash screen. this did not happen with the 10.10

thanks

---

### Post by Hedgehog1 on 2011-05-13
If I remember correctly, Windows will not boot from a logical partition, it must boot from a Primary partition.

/dev/sda5 is a logical partition.

Am I off base here? It happens a lot...

***The Hedge***

:KS

---

### Post by wallygator.uk on 2011-05-13
SOLVED

you are right, you can install and run winxp on a logical partition but you cannot boot it! so, i managed to find 100mb unused on the hdd, made it as a primary bootable partition, and copied the files necessary to winxp

boot.ini
NTDETECT.COM
ntldr

taken on a spare win machine. 

then, i run update-grub and it found the loader, but did not with some error. something like did not find partition dev/sda,msdos3 or something like that.

i had to edit grub.cfg entry as follow, from this (produced by the update-grub)

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 0F12758021ABBFDE
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###




to this



### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (custom) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,3)'
	
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

now i had finally the win boot screen, but the entries were wrong, because pointing at wrong hdd

run a repair from winxp cd to update the boot.ini file naming the entry something different from the ones already present (like winxp custom), saved and at the next reboot i was back on track


this whole proces without destroying and reinstalling grub.

hope this can help somebody else.

---

### Post by Quackers on 2011-05-13
Well done indeed :-)
There may be a small problem in store for you though, but I'm not 100% sure.
As you have edited grub.cfg directly, the changes you have made may be over-written whenever grub is updated (by yourself or via updates).

I suspect that making a manual entry (by copy/paste of your new grub.cfg Windows stanza) in the /etc/grub.d/40_custom file and then running sudo update-grub would be a more permanent fix for you.

Maybe somebody else could confirm that before you make any changes.
I wouldn't recommend that you update-grub for the moment though.

---

### Post by Quackers on 2011-05-13
Actually we could find out quite quickly.
If you copy the Windows stanza from grub.cfg into a text file and save it, then run sudo update-grub and see if the Windows entry disappears from the grub menu, we can confirm or deny my fears.
If the worst happens you can then edit /etc/grub.d/40_custom file by copy/pasting your text file contents into it, save the file then run sudo update-grub and the Windows entry should re-appear. This time it will be permanent.

---

### Post by oldfred on 2011-05-13
I would think the os-prober will find the new XP boot partition. But if not the entry would have to be in 40_custom

Just for documentation. meierfra. can get XP to boot from a logical partition.

Way to boot windows in extended logical partition with lilo's MBR post#5
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)

But I think the OP did it the more comman way as he did it.
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)
Create small FAT Primary to boot windows in logical
[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

---

