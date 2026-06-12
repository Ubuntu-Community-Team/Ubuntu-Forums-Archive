---
title: "&quot;No such device&quot; when trying to launch Win7"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Lexoka on 2010-08-01
[SIZE="4"][COLOR="Red"]Solved, see post #8.[/COLOR][/SIZE]

Hi,

I hope I'm in the right forum category. I've just installed Ubuntu on a new hard drive, and it works fine, but when I try to launch Windows 7 from GRUB, I get an error:

```

No such device: ac2e30ab2e307086
No such partition.

```

I'm not sure what's happening, but that device ID seems kind of short. For what it's worth, the HDD is a Samsung Spinpoint F1 1TB. I've seached for a solution to this and haven't found one, but I did notice a diagnosis script for loading issues, so here's the result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,859,647   104,857,600   7 HPFS/NTFS
/dev/sda2         104,859,648 1,953,521,663 1,848,662,016   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048    99,999,743    99,997,696 Linux or Data
/dev/sdb2      99,999,744   116,000,767    16,001,024 Linux Swap
/dev/sdb3     116,000,768   390,629,375   274,628,608 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AC2E30AB2E307086                       ntfs       System                        
/dev/sda2        F6D6E10DD6E0CEC5                       ntfs       Tera                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bbfd9b70-7f82-45c2-a007-506b2b28557b   ext4                                     
/dev/sdb2        c86cd806-84f6-4464-b6b2-f8d1c0111932   swap                                     
/dev/sdb3        3e77abef-4074-42c8-ba5d-5eb05c182c17   ext4                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        5490816990815282                       ntfs       Media                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /home                    ext4       (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
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
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=bbfd9b70-7f82-45c2-a007-506b2b28557b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=bbfd9b70-7f82-45c2-a007-506b2b28557b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bbfd9b70-7f82-45c2-a007-506b2b28557b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ac2e30ab2e307086
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=bbfd9b70-7f82-45c2-a007-506b2b28557b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=3e77abef-4074-42c8-ba5d-5eb05c182c17 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=c86cd806-84f6-4464-b6b2-f8d1c0111932 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.8GB: boot/vmlinuz-2.6.32-21-generic
  38.8GB: initrd.img
  38.8GB: vmlinuz

```

Any help would be much appreciated, thanks!

---

### Post by HarmCla on 2010-08-01
I just want to say that you're not alone out there.
I also ran into this problem today.
My setup looks similar to yours.

Grub2 was located on sdb,
grub could not reach windows 7 on sda, nor winxp on sda.
but booting my laptop from sda just started win7 without any problem.

It worked perfectly before untill I changed MBR to GUID on sdb getting this problem.
So I tought Grub2 doesn't like GUID and installed Grub2 to sda (which has MBR), still no luck.

However, booting win7 through grub on sdb gave me:
"Non-system disk, press any key to reboot"
booting win7 through grub on sda gave me:
"No such device: *blablabla*
No such partition."

I may not be much help, but I can confirm that nothing seems to be wrong with windows 7, it's a grub thing.

I hope someone knows what is happening here.

---

### Post by Lexoka on 2010-08-01
By the way, the results from the script say "Windows is installed in the MBR of /dev/sdc"

But Windows is actually installed on sda. So that's weird...

---

### Post by HarmCla on 2010-08-01
Nothing is wrong with that Device ID, you can see the same device ID in your boot info script.
Look:

> blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        [COLOR=Red]AC2E30AB2E307086[/COLOR]                       ntfs       System                        
/dev/sda2        F6D6E10DD6E0CEC5                       ntfs       Tera                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bbfd9b70-7f82-45c2-a007-506b2b28557b   ext4                                     
/dev/sdb2        c86cd806-84f6-4464-b6b2-f8d1c0111932   swap                                     
/dev/sdb3        3e77abef-4074-42c8-ba5d-5eb05c182c17   ext4                                     
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        5490816990815282                       ntfs       Media                         
/dev/sdc: PTTYPE="dos" 

And I found out that Grub2, or grub-pc, supports GPT (GUID Partition Table).
So I'm out off guesses right now. :(

---

### Post by HarmCla on 2010-08-01
> **Lexoka said:**
> By the way, the results from the script say "Windows is installed in the MBR of /dev/sdc"

But Windows is actually installed on sda. So that's weird...
Note that you also have windows XP on your sdc-drive.

---

### Post by drs305 on 2010-08-01
Lexoka,

From the Grub2 menu, try this:
Highlight the Windows menu item. Press "e" to enter the Grub2 edit mode.
Cursor down to the beginning of the "search" line.
Press and hold the DEL key until the entire line is removed.
Press CTRL-x to boot and see if it boots Windows.

Let us know if it works. If it does, we can edit the Grub files to remove the "search" line or come up with a more permanent fix.

---

### Post by Lexoka on 2010-08-01
> **HarmCla said:**
> Note that you also have windows XP on your sdc-drive.

Actually, I don't. I did format this drive using Windows XP (I did that prior to installing Windows 7) but there's no operating system on it, it's just a storage drive. That's why I don't understand the whole "Windows is installed in the MBR of /dev/sdc" thing.

> **drs305 said:**
> Lexoka,

From the Grub2 menu, try this:
Highlight the Windows menu item. Press "e" to enter the Grub2 edit mode.
Cursor down to the beginning of the "search" line.
Press and hold the DEL key until the entire line is removed.
Press CTRL-x to boot and see if it boots Windows.

Let us know if it works. If it does, we can edit the Grub files to remove the "search" line or come up with a more permanent fix.

I removed the "search..." line and pressed CTRL-x. The screen went black for a split second and then back to "normal". Other than that, nothing seemed to happen, no error message or anything.

---

### Post by oldfred on 2010-08-01
I had a similar issue & filed a bug, mixed gpt & msdos is the issue & they have a fix. The solution was to add a command to 40_custom. Then in my older notes I found a link to meierfra's where the same issue was resolved with a line in grub.  

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!

I prefer to have the boot loader on the same drive as the operating system and change BIOS to boot Ubuntu. That way if a drive fails I can still boot another.

---

### Post by Lexoka on 2010-08-01
> **oldfred said:**
> I had a similar issue & filed a bug, mixed gpt & msdos is the issue & they have a fix. The solution was to add a command to 40_custom. Then in my older notes I found a link to meierfra's where the same issue was resolved with a line in grub.  

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!

I prefer to have the boot loader on the same drive as the operating system and change BIOS to boot Ubuntu. That way if a drive fails I can still boot another.

Thanks, that worked! I did exactly what meierfra said, and now it works just fine.

And I've just checked, I can still boot Ubuntu as well. Thanks a lot to everyone.

---

### Post by Shuroy on 2010-09-27
> **oldfred said:**
> I had a similar issue & filed a bug, mixed gpt & msdos is the issue & they have a fix. The solution was to add a command to 40_custom. Then in my older notes I found a link to meierfra's where the same issue was resolved with a line in grub.  

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!

I prefer to have the boot loader on the same drive as the operating system and change BIOS to boot Ubuntu. That way if a drive fails I can still boot another.

I got Win7 on sda1 and Ubuntu on sdc4 and this fix helped me, thx a lot!

---

