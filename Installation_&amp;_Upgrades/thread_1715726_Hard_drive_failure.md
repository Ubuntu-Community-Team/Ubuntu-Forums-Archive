---
title: "Hard drive failure"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by bswanboat on 2011-03-27
Several times when I tried to boot the machine, I would get a insert system disk hard drive failure error message. By changing the bios to manual or back I have been able to boot without a problem. 

When I moved the machine from one desk to another to try to identify the error, the hard drive boots without a problem. 

But now I am getting the grub rescue> prompt.
[[COLOR="Blue"]HOWTO: Purge and Reinstall Grub 2 from the Live CD[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1581099") is excellent! I have gotten an old machine to work following these instructions, but this machine showed that grub was removed and installed successfully into the mbr. When I rebooted grub rescue> was still there. 

Next I tried to reinstall Ubuntu 10.04 LTS by formatting the partitions on installing. The result -- grub rescue> prompt. The only command grub rescue responds to is [COLOR="Magenta"]ls[/COLOR]. The hard drive test show the hard drive is healthy. When I did a ls (hd0,2)/boot, I receive the error message that the file system is not recognized.

Does anyone have any idea what is preventing grub from being installed correctly or keeping it from not working?

Does the hard drive just need a good low level formatting?

---

### Post by Rubi1200 on 2011-03-27
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bswanboat on 2011-03-27
The hard drive is a Samsung SP160N. A search has shown others have had similar issues with this hard drive. 

            ```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    15,951,599    15,951,537   c W95 FAT32 (LBA)
/dev/sda2    *     15,951,600   164,263,679   148,312,080   7 HPFS/NTFS
/dev/sda3         164,263,934   312,580,095   148,316,162   5 Extended
/dev/sda5         164,263,936   309,647,359   145,383,424  83 Linux
/dev/sda6         309,649,408   312,580,095     2,930,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        7270-48C2                              vfat       HP_RECOVERY                   
/dev/sda2        EA50AF0450AED69B                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e89f94bb-c582-4c48-af7f-6662fc05804c   ext4                                     
/dev/sda6        34f17d26-a1fb-4b27-884e-c762c8ae5f70   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/HP_PAVILION       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


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
search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
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
search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e89f94bb-c582-4c48-af7f-6662fc05804c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e89f94bb-c582-4c48-af7f-6662fc05804c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e89f94bb-c582-4c48-af7f-6662fc05804c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7270-48c2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set ea50af0450aed69b
	drivemap -s (hd0) ${root}
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
UUID=e89f94bb-c582-4c48-af7f-6662fc05804c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=34f17d26-a1fb-4b27-884e-c762c8ae5f70 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 127.2GB: boot/grub/core.img
 142.2GB: boot/grub/grub.cfg
 125.0GB: boot/initrd.img-2.6.32-24-generic
 125.0GB: boot/vmlinuz-2.6.32-24-generic
 125.0GB: initrd.img
 125.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Rubi1200 on 2011-03-27
According to the boot script results, everything seems to be where it should be (at least nothing obviously wrong stands out).

The one thing I did notice was this:
> timeout=0The default timeout for the Windows bootloader is 30. Both sda1 and sda2 are set to 0. 

I suggest first changing that to something like 5 or higher:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

When you say you are manually changing BIOS, what settings are you changing?

---

### Post by bswanboat on 2011-03-27
Your quick and detailed response is much appreciated. I will up the time on the timeout and give it a shot.

Many thanks!
Bill

---

