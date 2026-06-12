---
title: "Ubuntu cd does not see win 7 partition"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Milardo on 2010-05-17
Hi,

   My problem is that I cannot install latest ubuntu with win7 in dual boot configuration. For example, if i have win 7 installed and then use the ubuntu cd to install ubuntu, the cd says my computer has no operating systems on it. The other way around if I have ubuntu installed on it and then try to install win 7, win 7 recognizes the linux partition but will not allow me to install win 7 unless i totally delete ubuntu partition. Does anyone have or had a problem like this, or think that it is a problem with my hard drive, or is it a problem with my laptop (motherboard, controller, etc.) I've updated it with the latest bios , ec.Thanks in advance for any help.

---

### Post by darkod on 2010-05-17
Use these instructions and post the content of your results.txt file. It will show us more.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by Milardo on 2010-05-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   819,202,047   818,995,200   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BAE4799AE4795A19                       ntfs       System Reserved               
/dev/sda2        84A081DEA081D758                       ntfs       LaptopInternalHardDrive       
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```

---

### Post by darkod on 2010-05-17
[COLOR=Red]GUID Partition Table detected[/COLOR], but does not seem to be used.

This is probably the issue confusing grub2 and blocking it from seeing /dev/sda1 properly. However, I don't know what to do and not to lose your data.
Otherwise, you can write a new DOS partition table on the disk but that would destroy all partitions and data.

You could try google for something like "transform gpt to mbr" or similar and see if that's something you would like to do.

A lot of PC manufacturers seem to have started pushing GPT even when there is no need for it, and because it's a new thing there will be hiccups in the transition. :(

---

### Post by Milardo on 2010-05-17
Is there a way to completely erase that gpt partition table? Is it located on my hard drive and do you know how it got there? I've got my windows 7 image saved on another drive if i erase the gpt and load the windows 7 image it won't come back will it? Lastly, what created the gpt partition table? Thanks in advance.

---

### Post by darkod on 2010-05-17
The problem is, a partition table is called like that because it holds information about which partitions exist on the disk. Erase that, and it's like to have formatted the whole disk.

If you are willing to install win7 again, and put your data back, the following should work (THIS WOULD DESTROY YOUR CURRENT DATA, JUST READ DON'T DO IT RIGHT AWAY!!!):

Open Gparted and select your hdd. At the bottom there should be a button like Write Partition Table, or Create Partition Table, or something similar. That will write new partition table to the disk, and you can select the type to be DOS (if it asks).

Otherwise, even formatting the hdd doesn't destroy the partition table, just the information inside. It will update it to know that you have formatted (deleted) all partitions. But it will remain GPT type.

I'm not experienced with this and can't give you specific advice. Hopefully someone else can. Meanwhile you can try reading on google about GPT. I think there was a way to change to DOS without losing the data.

---

### Post by Milardo on 2010-05-17
Thanks for the good info. However, if you know, how did my hard drive get to be gpt anyways and if i reimage with my saved win7 image will it become gpt type again? Oh, it is okay if all my data/os is erased, i got it saved and don't mine starting over if i have to. My desktop has no problems with this, i guess older harddrive and motherboard.

---

### Post by darkod on 2010-05-17
It was GPT all the time from the manufacturer. It depends what info is in the image. There is some possibility the image itself to make the disk GPT again.

But you can try writing standard MBR on it, and restoring the image. See how it goes. :)

---

### Post by Milardo on 2010-05-17
Alright thanks for your help and I will post with the steps I took to resolve this.

---

### Post by darkod on 2010-05-17
This has some steps for conversion but it says the disk should not have any partitions on it:
[http://www.neowin.net/forum/topic/773018-how-do-i-convert-my-hard-drive-from-gpt-to-mbr/](http://www.neowin.net/forum/topic/773018-how-do-i-convert-my-hard-drive-from-gpt-to-mbr/)

---

### Post by Milardo on 2010-05-18
Thanks for the info. However I solved my problem (i think) this way.

Yes it was the gpt partition table which caused the problem. These are the steps I took (not necessary for everybody) to solve my problem. After searching i found this post 

[http://ubuntuforums.org/showthread.php?p=9236110](http://ubuntuforums.org/showthread.php?p=9236110)

Which led me to this site

[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I used the tool to convert my partitions from gpt to mbr. It seemed to work and it didn't erase my partitions, however after reboot i couldn't startup win 7 or repair them. However now Ubuntu cd recognized them. I had a previously saved image of win 7 so I reimaged my hard drive and then I then tried to install Ubuntu which recognized the win 7 partition again with no problem and installed successfully. Thanks for your help.

---

### Post by Milardo on 2010-05-18
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   819,202,047   818,995,200   7 HPFS/NTFS
/dev/sda3         819,202,048   893,421,567    74,219,520  83 Linux
/dev/sda4         893,421,568   901,429,247     8,007,680  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BAE4799AE4795A19                       ntfs       System Reserved               
/dev/sda2        84A081DEA081D758                       ntfs       LaptopInternalHardDrive       
/dev/sda3        b532fc85-969c-4500-a885-27a8eb50500a   ext4                                     
/dev/sda4        33ef7081-a2f8-4081-80f2-2e512839fe15   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b532fc85-969c-4500-a885-27a8eb50500a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b532fc85-969c-4500-a885-27a8eb50500a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set b532fc85-969c-4500-a885-27a8eb50500a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bae4799ae4795a19
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
# / was on /dev/sda3 during installation
UUID=b532fc85-969c-4500-a885-27a8eb50500a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=33ef7081-a2f8-4081-80f2-2e512839fe15 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 449.6GB: boot/grub/core.img
 449.7GB: boot/grub/grub.cfg
 449.7GB: boot/initrd.img-2.6.32-21-generic
 449.7GB: boot/vmlinuz-2.6.32-21-generic
 449.7GB: initrd.img
 449.7GB: vmlinuz
```

---

### Post by Milardo on 2010-05-18
How does the output look now?

---

### Post by darkod on 2010-05-18
> **Milardo said:**
> How does the output look now?

Looks perfectly normal. :)

---

