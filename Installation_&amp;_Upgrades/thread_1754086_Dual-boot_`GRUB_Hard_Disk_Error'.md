---
title: "Dual-boot `GRUB Hard Disk Error'"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by mcallisterjp on 2011-05-09
Hi all, noob here.

My system has Windows XP Pro SP2 installed on /sda1 and originally a 10.04 on /sdb1-3, now upgraded to 11.04.

The Ubuntu system works fine (teething troubles with nvidia drivers on upgrade but fixed now), and the Windows system shows up in the grub menu, but when it's selected, I just get `GRUB Hard Disk Error' and nothing else. 

Windows installed properly, and booted successfully until I installed Ubuntu in the first place. I can still access the files on that drive from within Ubuntu.

I've tried fixboot in the Win Recovery Console, which sounded like it did something, but didn't fix the problem.

This problem isn't new to grub2, by the way - I just haven't needed Windows in a year.

What other info do you need?

Thanks in advance,
Pete

---

### Post by wilee-nilee on 2011-05-09
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a what is where without a ton of questions. Note the code tags this is extremely important it is a lot of text and difficult to read without the codetags used, notice the manual method in my signature as well, if my first description is confusing..

---

### Post by mcallisterjp on 2011-05-09
Here's the output of boot_info_script:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2can.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for cbdc4.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   908,411,489   908,411,427  83 Linux
/dev/sdb2         908,411,490   947,481,569    39,070,080  83 Linux
/dev/sdb3         947,481,570   976,768,064    29,286,495  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80C2F69090FA0800                       ntfs       windows                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f59296e9-c297-40d0-809b-b35b165d2947   ext4                                     
/dev/sdb2        7ad62388-01ea-4ffe-9c9b-08143742ab0d   ext3                                     
/dev/sdb3        73c683df-a88a-4be9-ba72-41f9a9b305eb   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        80C2F69090FA0800                       ntfs       music                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/music             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/windows           fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /home                    ext3       (rw,commit=0)
/dev/sr0         /media/XP_PRO_SP2        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 80C2F69090FA0800
	drivemap -s (hd0) ${root}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd3       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd2 during installation
UUID=7ad62388-01ea-4ffe-9c9b-08143742ab0d /home           ext3    defaults        0       2
# swap was on /dev/sdd1 during installation
UUID=73c683df-a88a-4be9-ba72-41f9a9b305eb none            swap    sw              0       0
/dev/fd0        /media/floppy0  ntfs    rw,user,noauto,exec,utf8 0       0
LABEL=music			/media/music ntfs-3g rw,auto,user,utf8 0 0
LABEL=windows			/media/windows ntfs-3g rw,auto,user,utf8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
 425.3GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
   1.7GB: boot/initrd.img-2.6.35-25-generic
   2.4GB: boot/initrd.img-2.6.35-27-generic
   4.0GB: boot/initrd.img-2.6.35-28-generic
   9.1GB: boot/initrd.img-2.6.38-8-generic
   9.1GB: boot/initrd.img-2.6.38-8-generic-pae
  28.1GB: boot/vmlinuz-2.6.35-22-generic
  28.1GB: boot/vmlinuz-2.6.35-25-generic
  28.1GB: boot/vmlinuz-2.6.35-27-generic
  28.2GB: boot/vmlinuz-2.6.35-28-generic
   6.6GB: boot/vmlinuz-2.6.38-8-generic
    .2GB: boot/vmlinuz-2.6.38-8-generic-pae
   9.1GB: initrd.img
   9.1GB: initrd.img.old
   6.6GB: vmlinuz
    .2GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by wilee-nilee on 2011-05-09
Ahem before you malign the applications (grub2) you may want to like understand what you have going, just ribbing you here.;)

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type: [B] Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdc1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot [/B]
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


This is grub legacy, I'm going to let others help you here not a hard fix, but your handy work has left you a little messed up. We have to assume that the OS's are in good shape, to get this fixed. You never put grub into windows.

---

### Post by mcallisterjp on 2011-05-09
Hah, no disrespect meant to any bootloader whatever. I'm under no illusion that anything but me caused that particular piece of broken glass.

Now how should I fix it?

---

### Post by wilee-nilee on 2011-05-09
> **mcallisterjp said:**
> Hah, no disrespect meant to any bootloader whatever. I'm under no illusion that anything but me caused that particular piece of broken glass.

Now how should I fix it?

So there are regulars who are very good at this, I would bet a lot of money on a visit by them within at the most 4 hours, we all live in different places.

The setup is kind of needing a person more confident then myself in leaving you in perfect order. I would help if I did not have a rule of do no harm, at least to the computer lol. So relax crack a beverage keep an eye on the thread pop in a movie help will be arriving soon.;)

---

### Post by drs305 on 2011-05-09
EDIT:  Brainstorm. First, is your BIOS booting from sdb. That may be all you need. If not ...

The best idea is probably to boot the *Natty* LiveCD. Mount your Ubuntu partition (sd**b**1 but confirm it), purge grub, grub-pc and grub-common, then reinstall grub-common and grub-pc. 

Make sure to select sdb as for the installation when asked. You select the drive with the SPACEBAR, then TAB to OK to ENTER.

The instructions are in the 'Chroot' link in my signature line. You will want to do the Chroot procedure.

Once you are done, make sure your BIOS is set to boot sdb first.

It looks like you don't have any of the boot files for XP, so if you want to restore that OS you are going to need to use a Windows repair disk. You can have the Windows bootloader on sda and Grub2 on sdb for added versatility.

---

### Post by mcallisterjp on 2011-05-09
I carried out the purge/reinstall suggested. This did not remove grub 0.97 from the system, but did confuse boot_info_script as to where it is, and on rebooting grub reported XP as living on /sdc, and  the drive labels swapped around: 

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cbdc4.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 1 on boot drive #119 for the stage2 
                       file. A stage2 file is at this location on /dev/sdb. 
                       Stage2 looks on the same partition for 
                       /boot/grub/stage2. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,283,479   398,283,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   908,411,489   908,411,427  83 Linux
/dev/sdc2         908,411,490   947,481,569    39,070,080  83 Linux
/dev/sdc3         947,481,570   976,768,064    29,286,495  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80C2F69090FA0800                       ntfs       music                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        80C2F69090FA0800                       ntfs       windows                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        f59296e9-c297-40d0-809b-b35b165d2947   ext4                                     
/dev/sdc2        7ad62388-01ea-4ffe-9c9b-08143742ab0d   ext3                                     
/dev/sdc3        73c683df-a88a-4be9-ba72-41f9a9b305eb   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/music             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/windows           fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc2        /home                    ext3       (rw,commit=0)
/dev/sr1         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f59296e9-c297-40d0-809b-b35b165d2947 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f59296e9-c297-40d0-809b-b35b165d2947
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 80C2F69090FA0800
	drivemap -s (hd0) ${root}
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd3       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd2 during installation
UUID=7ad62388-01ea-4ffe-9c9b-08143742ab0d /home           ext3    defaults        0       2
# swap was on /dev/sdd1 during installation
UUID=73c683df-a88a-4be9-ba72-41f9a9b305eb none            swap    sw              0       0
/dev/fd0        /media/floppy0  ntfs    rw,user,noauto,exec,utf8 0       0
LABEL=music			/media/music ntfs-3g rw,auto,user,utf8 0 0
LABEL=windows			/media/windows ntfs-3g rw,auto,user,utf8 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
 219.4GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
   1.7GB: boot/initrd.img-2.6.35-25-generic
   2.4GB: boot/initrd.img-2.6.35-27-generic
   4.0GB: boot/initrd.img-2.6.35-28-generic
   9.1GB: boot/initrd.img-2.6.38-8-generic
   9.1GB: boot/initrd.img-2.6.38-8-generic-pae
  28.1GB: boot/vmlinuz-2.6.35-22-generic
  28.1GB: boot/vmlinuz-2.6.35-25-generic
  28.1GB: boot/vmlinuz-2.6.35-27-generic
  28.2GB: boot/vmlinuz-2.6.35-28-generic
   6.6GB: boot/vmlinuz-2.6.38-8-generic
    .2GB: boot/vmlinuz-2.6.38-8-generic-pae
   9.1GB: initrd.img
   9.1GB: initrd.img.old
   6.6GB: vmlinuz
    .2GB: vmlinuz.old
```

Presumably something's wrong with fstab to generate the label musical chairs, but grub 0.97 is also hanging in there.

---

### Post by drs305 on 2011-05-09
Yes, all the drive designations have changed, but it looks like Grub 2 is now installed on your Ubuntu partition. Grub legacy is still on your Windows partition but that doesn't make any difference. It won't be controlling the boot so it doesn't matter, but to restore Windows you will overwrite it later anyway.

So you can try to set the proper drive to boot (it's currently sdc but who knows...). The best thing to do is enter BIOS, determine which drive is your Ubuntu drive and set it to boot first.

If that doesn't work, we can try it manually. Run the following commands. The first will list your drives and partitions. Determine which one is your Ubuntu partition (you can check with 'ls (hdX,1)/boot/grub'. Try 0, 1, and 2 until you find it. 

For the example, I'll say it was sdc1 (hd2,1). Change it if necessary:

```

ls
set prefix=(hd2,1)/boot/grub
set root=(hd2,1)
insmod normal
linux /vmlinuz root=/dev/sdc1 ro  # If it doesn't load:  insmod linux
initrd /initrd.img
boot
```

**SORRY!** I just reread your first post. Is it **Windows** you can't get to work? I misread the post. If Grub2 is booting you into Ubuntu, it's time to work on Windows. If you only need to point the *Windows* drive MBR back to the Windows partition, you can start with these commands. First, if Ubuntu is running normally (no CD), run "**sudo update-grub**". 

You want to only install to the Windows drive so it leaves the Grub bootloader alone. Again, confirm the drive Windows is on before running the following commands and if necessary change **sda** to the Windows drive.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't worry about messages saying lilo isn't fully installed. 

Grub should boot Ubuntu and Windows. If you change the BIOS to boot the Windows drive first, it should boot directly to the Windows bootloader if the Windows boot files are intact.

Here is a Windows boot repair guide:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")]
I'm not a windows guy but I think what you will be looking for is fixmbr and fixboot.

---

### Post by mcallisterjp on 2011-05-09
Edit:

I performed the lilo command suggested, then booted into XP recovery console, which suggested the installation D:\WINDOWS (Why D:\ I have no idea). 

After checking that this was the drive containing the right files, I then performed 'fixboot d:' and 'fixmbr d:'. 'fixboot' alone suggested it was about to muck about with another drive, so I cancelled it.

No change in symptoms.

---

### Post by oldfred on 2011-05-09
Did you do something to change drive order. windows was sdc1 and now it is sda1?

Fixboot is the windows way to fix it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by mcallisterjp on 2011-05-09
fixboot and fixmbr didn't seem to do anything. Testdisk has 'Rebuild BS' rather than 'Backup BS' in the relevant screen, and doesn't seem to think there's anything wrong there.

I'm not aware of having done anything to change the drive name allocation, but it seems to change on most reboots.

---

### Post by oldfred on 2011-05-09
Testdisk should tell you if backup is same or not. The rebuild will make it a valid NTFS partition, but it may not be bootable as XP and Vista/7 have different versions of bootable boot sectors. But then you may be able to repair it with fixboot.

Drive order changing is not good. Ubuntu uses UUIDs so it finds correct partition. XP's boot.ini has to have correct drive to work. 

Is power supply weak and you have added too many drives? BIOS should bring them up in the same order.

---

### Post by mcallisterjp on 2011-05-09
At the suggestion of drs305, I tried booting from the Windows drive to see if the installation was viable by itself.

It was not, giving a 'ntldr is missing' error. I fixed that by copying files from the XP CD, got into a booting XP and activated windows, then ran update-grub from the Ubuntu installation.

Now there are two entries in grub:
Microsoft Windows XP Professional (on /dev/sda1)
Windows NT/2000/XP (on /dev/sdb1)

(sdb1 is the correct partition, sda1 contains no OS)

Both now give the same 'GRUB Hard Disk Error'.

My power supply should be more than adequate to supply the hardware involved.

---

### Post by drs305 on 2011-05-10
The error message you are getting is not one I've seen much of on the Ubuntu forums, although a search did show quite a few threads around the Internet. 

I notice two of your drives are physically identical. Have you ever run a RAID setup on your system? I'm not very familiar with RAID but I know there have been users in the past that had to clear out remants of a former RAID setup for Grub2 to work properly. I know the command was "sudo dmraid -E -r /dev/sd[COLOR="Red"]X[/COLOR]" but if you once had RAID please do a search of this command before running it.

---

### Post by mcallisterjp on 2011-05-10
The drives are identical but have never been run in a RAID; dmraid gave the message 'no raid disks and with names: "/dev/sd[x]"' on the relevant commands.

---

### Post by mcallisterjp on 2011-05-16
Anyone have any ideas on this?

---

### Post by drs305 on 2011-05-17
Since thread inputs seem to have quieted down, I'll offer some observations. Be advised though that I am not a Windows guru.

Confirm that Windows is still sda and Ubuntu is sdc.

The first thing I would try to do is clear up is the remants of Grub legacy on sdb. It may or may not be messing with Grub 2. You may be able to clear it with TestDisk - I have had mixed results with Natty. It will write TestDisk information to the partition boot record of sda1. That info won't really do anything except clear out the Grub 0.97 data. I always back up the drive's MBR before using TestDisk, just as a backup. It is the first command - be careful using dd.

```

sudo dd if=/dev/sda of=sda.MBR.512.img bs=512 count=1
sudo apt-get install testdisk
sudo testdisk /dev/sda1

```
TestDisk will open.
[LIST]
[*]Confirm sda**1** is highlighted.
[*]Proceed > Intel > MBR Code
[*]Y > Y > OK > Quit > Quit
[/LIST]

You could try rebooting and see if that resolves the "GRUB Hard Disk" error.


The next thing I would do is to allow sda to boot independently of Grub/Ubuntu. You can do this by *partially* installing *lilo*, another bootloader, into sda. When you run the commands, it will advise you that lilo is not fully configured and you should run additional commands. Don't. Just the two commands below.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This should not affect Grub2 from booting as long as sdc is first in the boot order. What it will do is allow Windows to be booted directly if you change the BIOS boot order to sda first.

At this point, you could try rebooting. Most likely nothing has changed, but try booting Windows anyway and see if it boots.

Then please run the boot info script, *but use the beta version*. It provides better information on Natty/Grub 1.99 installations. You can download it by clicking the "BIS-2" link in my signature.

---

