---
title: "I just upgraded from ubuntu 9 to 10"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Colinchocolate on 2010-05-18
After upgrading, it brought me to the usual grub bootloader, and it gives me a grub rescue error message. I restarted my computer, and went through my bios to boot from my hard drive first so I could get back onto my windows partition. Unless I re-route my computer, It always gives me the grub rescue message, or if my USB hard drive with ubuntu 10 isn't in my computer, it gives me a can't find such-and-such message.

---

### Post by wilee-nilee on 2010-05-18
> **Colinchocolate said:**
> After upgrading, it brought me to the usual grub bootloader, and it gives me a grub rescue error message. I restarted my computer, and went through my bios to boot from my hard drive first so I could get back onto my windows partition. Unless I re-route my computer, It always gives me the grub rescue message, or if my USB hard drive with ubuntu 10 isn't in my computer,  message.

Post this script in code tags. To do this paste the script readout into the reply highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It sounds like you have grub installed in a wrong place. Also are you trying to have separate bootloaders one for Ubuntu and one for windows?

This phrase makes no sense > it gives me a can't find such-and-such can you be more specific as to what it actually says.

---

### Post by Colinchocolate on 2010-05-18
Unfortunately, I cannot get into my ubuntu partition, so the script will not work. I will get back with the "cannot find..." message as soon as I restart my computer. I am not trying to put multiple bootloaders for windows and linux, although it may just be that I have two versions of grub. When I re-routed my computer to my main drive, it brought up the usual grub bootloader, and I'm not sure, but I think that the loader still had ver. 9 ubuntu in the list along with my windows.

---

### Post by wilee-nilee on 2010-05-18
> **Colinchocolate said:**
> Unfortunately, I cannot get into my ubuntu partition, so the script will not work. I will get back with the "cannot find..." message as soon as I restart my computer. I am not trying to put multiple bootloaders for windows and linux, although it may just be that I have two versions of grub. When I re-routed my computer to my main drive, it brought up the usual grub bootloader, and I'm not sure, but I think that the loader still had ver. 9 ubuntu in the list along with my windows.

You run the scipt from a live CD.

---

### Post by Colinchocolate on 2010-07-24
Sorry it took so long to finally get this here.... It looks like I have two bootloaders and wish to remove the one that pops up if my hard drive isn't inserted. It gives me a grub rescue error. if my hard drive is inserted, it goes to the working grub bootloader , as I have set the bios up to boot from my hard drive first if available. Can you help me delete the one on my main hard drive? 


 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,155,279    78,155,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   536,137,244   536,137,182   7 HPFS/NTFS
/dev/sdb2         536,137,726   976,768,064   440,630,339   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris
/dev/sdb6         536,137,728   964,685,823   428,548,096  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AE740FD3740F9CE9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2E1006301005FF97                       ntfs       External Drive                
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        d663890d-00e3-4fca-af88-75076b2b9f03   swap                                     
/dev/sdb6        a06fdd77-7039-49cc-8b1e-deb262a55ba2   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/External Drive    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/AE740FD3740F9CE9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\Windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
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
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a06fdd77-7039-49cc-8b1e-deb262a55ba2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a06fdd77-7039-49cc-8b1e-deb262a55ba2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set a06fdd77-7039-49cc-8b1e-deb262a55ba2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae740fd3740f9ce9
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 356.2GB: boot/grub/core.img
 392.7GB: boot/grub/grub.cfg
 276.9GB: boot/initrd.img-2.6.32-21-generic
 356.2GB: boot/vmlinuz-2.6.32-21-generic
 276.9GB: initrd.img
 356.2GB: vmlinuz
=============================== StdErr Messages: ===============================

hexdump: /media/External Drive/TribalLeader4.png: Input/output error
hexdump: /media/External Drive/TribalLeader4.png: Input/output error
hexdump: /media/External Drive/TribalLeader4.png: Input/output error
```

Oh, and just an unfortunate note, I cannot connect to the internet through my ubuntu, because I cannot get my wireless driver to work... that means, either I figure out how to fix it, or all updates and such have to be through my windows XP and transfered.

---

### Post by kansasnoob on 2010-07-25
> I cannot connect to the internet through my ubuntu, because I cannot get my wireless driver to work.

Are you able to connect using a Live CD?

I don't know anything about wireless but you'll need to install a package to get things totally sorted out. You actually have two problems:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

You see /dev/sda should have a "Windows readable" mbr which we can fix with an Ubuntu Live CD, but also /dev/sdb says it's looking for grub2 on partition #5 which is wrong.

So, to properly sort out the Windows drive, **if you can connect using any Ubuntu Live CD** then you'd need to copy-n-paste the following commands from Terminal in the Live CD:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

To sort out the Ubuntu drive you wouldn't need a connection, just use a Live CD and copy-n-paste the following:

```
sudo mount /dev/sdb6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

Note: If that should show any errors then also run:

```
grub-install --recheck /dev/sdb
```

Then:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

