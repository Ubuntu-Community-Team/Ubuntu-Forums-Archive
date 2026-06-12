---
title: "Trouble installing on external USB HD"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by mgb on 2010-11-14
Hello,

I have an HP notebook with Windows 7 installed on the internal hd and I am trying to install Ubuntu on an external USB HD. I am using the iso on CD.  The image gets loaded but GRUB is not installed in the right place, I think.  I changed the BIOS settings to have it boot off the USB HD before the internal HD.  But it always by passes and goes right to Windows.  I have it booted into the temporary session (from the Try Ubuntu option).  and can see the filesystem.  How do I get grub to the right place?

Thanks,

mgb

---

### Post by sikander3786 on 2010-11-14
Hi.

When you installed Ubuntu, the Windows drive was connected or disconnected? Did you care for the install location of Grub or it installed automatically to the default location?

I think Grub is not installed at all as you don't even see it when you boot from Windows drive, right?

Instead of making assumptions, it would be better to post the output of bootinfoscript from a Live CD as per instructions here. It would help use properly understand your current situation and advise accordingly.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You can always reinstall Grub. If you are confident that you can do it yourself, you can follow these commands. But I would recommend that you disconnect your Windows drive before proceeding so you don't by any chance, mess up your existing install.

Find your root partition by typing,

```
sudo fdisk -l
```

Note the annotation, I'll use sda1 in this example but it might differ in your case.

Mount your root partition,

```
sudo mount /dev/sda1 /mnt
```

Install Grub,

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the above command it is just sda, not sda1. (In your case it might be sdb or sdf or whatever)

Once it is installed, plug in your Windows HDD and boot from the external one straight into Ubuntu. Run this command if you want Windows to be listed in the Grub menu so you can use it to boot both the OS when the external drive is connected.

```
sudo update-grub
```

Once the external HDD is disconnected, your computer will obviously boot directly to Windows.

---

### Post by mgb on 2010-11-14
Hi,

Thanks for your reply.  Here is the output of the boot_info_script.sh:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 591765984 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   599,173,119   598,763,520   7 HPFS/NTFS
/dev/sda3         599,173,120   625,139,711    25,966,592   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   567,169,023   567,166,976   7 HPFS/NTFS
/dev/sdc2         567,171,070   976,771,071   409,600,002   5 Extended
/dev/sdc5         567,171,072   578,887,679    11,716,608  82 Linux swap / Solaris
/dev/sdc6    *    578,889,728   976,771,071   397,881,344  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0E767F66767F4E09                       ntfs       SYSTEM                        
/dev/sda2        C87CE2667CE24F2E                       ntfs                                     
/dev/sda3        0A62E2F162E2E105                       ntfs       RECOVERY                      
/dev/sda: PTTYPE="dos" 
/dev/sdc1        8ECEF041CEF022DF                       ntfs       PENDRIVE                      
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        b8652924-cfb1-4c51-90d9-589b35c1e425   swap                                     
/dev/sdc6        a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        18BC-B5A8                              vfat                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc6        /media/a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/PENDRIVE          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/18BC-B5A8         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 0e767f66767f4e09
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set c87ce2667ce24f2e
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 0a62e2f162e2e105
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

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=a5cf8d9f-3cf6-4771-8ac1-74f2a4b84ba8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b8652924-cfb1-4c51-90d9-589b35c1e425 none            swap    sw              0       0

=================== sdc6: Location of files loaded by Grub: ===================


 302.9GB: boot/grub/core.img
 492.0GB: boot/grub/grub.cfg
 492.5GB: boot/initrd.img-2.6.35-22-generic-pae
 302.9GB: boot/vmlinuz-2.6.35-22-generic-pae
 492.5GB: initrd.img
 302.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 b2 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  b2 00 00 38 b7 17 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by C.S.Cameron on 2010-11-14
I think that when installing 10.10 to a portable device you need to use manual partitioning to install grub to that device.
If you did not, then boot the Live CD and follow sikander method to install it.
It looks to me like you want to install it to sdc if you leave your internal HDD plugged in.

---

### Post by sikander3786 on 2010-11-15
You need to reinstall Grub as suggested above.

Change sda1 to sdc6 and sda to sdc so you'll simply need to do these 2 commands from Live CD terminal. Leave all drives connected when you do this as now we know from your bootinfoscript about your drive setup.

```
sudo mount /dev/sdc6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

---

### Post by mgb on 2010-11-15
Okay, I executed the commands, but got this error:

```
cp: reading `/usr/lib/grub/i386-pc/915resolution.mod': Input/output error
```

Please advise,

Regards,

mgb

---

### Post by Animal X on 2010-11-15
I had this same trouble. To be honest, i just unplugged my hard drive (internal) and had the external drive as the only one mounted, then i did my install. I think part of the problem here is nowadays HP and others who install windoze use 2 or more partitions for recovery options, and the OS(MicroSux) is almost never on sda1. good luck, I'll be watching this thread.

---

### Post by C.S.Cameron on 2010-11-15
> **animal x said:**
> i had this same trouble. To be honest, i just unplugged my hard drive (internal) and had the external drive as the only one mounted, then i did my install. I think part of the problem here is nowadays hp and others who install windoze use 2 or more partitions for recovery options, and the os(microsux) is almost never on sda1. Good luck, i'll be watching this thread.

+1

---

### Post by sikander3786 on 2010-11-16
From Live CD, try these.

```
sudo mount /dev/sdc6 /mnt
```

```
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc
```

---

### Post by mgb on 2010-11-17
Please see my previous post.  I tried your suggestion but got an error.

Please advise.

Regards,

mgb

---

### Post by sikander3786 on 2010-11-18
> **mgb said:**
> Please see my previous post.  I tried your suggestion but got an error.

Please advise.

Regards,

mgb
There is a small --recheck difference between the 2 commands :-)

Try those from post # 9 and post the output if errors are reported.

---

### Post by mgb on 2010-11-21
I executed the command exactly as you said with the --recheck, but unfortunately got the same error as before.

```
cp: reading `/usr/lib/grub/i386-pc/915resolution.mod': Input/output error
```

Please advise.

Regards,

mgb

---

### Post by sikander3786 on 2010-11-22
> cp: reading `/usr/lib/grub/i386-pc/915resolution.mod': Input/output error

Are you booted from a Live CD? That input/output error might be suggesting that the disc is not readable.

Can you please try with some other disc or a USB Startup Disk? You can create one using unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Thanks.

---

### Post by deanhiller on 2011-07-18
I somehow got into the same issue Input/Output error on trying grub and cat that same file and starting firefox....it seems to have something to do with the mount points I created as when I rebooted everything was then fine.....so very odd but cost me 20 minutes until I decided to reboot and give it another go.

---

