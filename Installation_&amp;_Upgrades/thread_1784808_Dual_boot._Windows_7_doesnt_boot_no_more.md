---
title: "Dual boot. Windows 7 doesnt boot no more"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by PigFoot55 on 2011-06-17
Hi everyone,
I have a little problem here.
I have Ubuntu 10.10 here alongside Windows7. Everything worked properly until today. I made some regular updates (normal ones, NOT 11.04 update) and now I cant boot into Windows.
Reboot-> GRUB showes up -> I select Windows7 -> the screen clears -> and it jumps back to GRUB

Ive tried windows repair CD (no error occurred), Ive tried updating grub  ```
 sudo update-grub
```
but nothing helped.

Heres my boot_info_script result: 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 862855232 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 6 for (,msdos6)/boot/grub. No 
                       errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   535,437,219   535,025,572   7 NTFS / exFAT / HPFS
/dev/sda3         535,437,310   945,829,887   410,392,578   f W95 Extended (LBA)
/dev/sda5         885,022,720   945,829,887    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda6         535,437,312   870,756,351   335,319,040  83 Linux
/dev/sda7         870,758,400   885,020,671    14,262,272  82 Linux swap / Solaris
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        CA8A74088A73EF77                       ntfs       
/dev/sda2        64BE7652BE761CAC                       ntfs       
/dev/sda4        44527EE9527EDEDC                       ntfs       LENOVO_PART
/dev/sda5        9642B14E42B133B9                       ntfs       LENOVO
/dev/sda6        ae78be8d-0395-4c0a-a419-b023a5dada6b   ext4       
/dev/sda7        04983b51-2442-4666-a4f3-5adae7e17901   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set CA8A74088A73EF77
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 44527EE9527EDEDC
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=04983b51-2442-4666-a4f3-5adae7e17901 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 411.441459656 = 441.781903360  boot/grub/core.img                             1
 352.373703003 = 378.358382592  boot/grub/grub.cfg                             1
 256.820537567 = 275.758952448  boot/initrd.img-2.6.35-25-generic-pae          2
 287.972656250 = 309.208285184  boot/initrd.img-2.6.35-27-generic-pae          2
 353.956047058 = 380.057411584  boot/initrd.img-2.6.35-28-generic-pae          2
 411.452407837 = 441.793658880  boot/vmlinuz-2.6.35-25-generic-pae             1
 411.570529938 = 441.920491520  boot/vmlinuz-2.6.35-27-generic-pae             1
 411.582279205 = 441.933107200  boot/vmlinuz-2.6.35-28-generic-pae             1
 353.956047058 = 380.057411584  initrd.img                                     2
 287.972656250 = 309.208285184  initrd.img.old                                 2
 411.582279205 = 441.933107200  vmlinuz                                        1
 411.570529938 = 441.920491520  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```


Can this ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector))  help?


Thanks for any help/advice

---

### Post by Quackers on 2011-06-17
Grub has also been installed to sda1 (your Windows boot partition). Windows won't like that there. You should repair the Windows bootloader with bootrec.exe /fixboot from the repair console in a repair disc (or installation disc) and then update-grub again.

---

### Post by PigFoot55 on 2011-06-17
So the command will be like this?
```
bootrec.exe /fixboot
```

btw thanks for such a quick reply

---

### Post by Quackers on 2011-06-17
Yes I would try that from the command prompt option in the repair console of the installation/repair disc.

---

### Post by PigFoot55 on 2011-06-17
Worked like a charm :) Thank you Quackers, you saved me once again.
But still i wonder how is it possible that it got overriden...

---

### Post by Quackers on 2011-06-17
I'm glad to hear that :-)
It happened because sda1 seems to have been named as the destination for grub - 
during the installation maybe?

Please mark the thread as solved, using Thread Tools near the top of the page.
Thanks.

---

