---
title: "Booting to Windows without external drive containing Linux."
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by de_flurk on 2010-12-16
Hello forum!

I'm new to Linux but got it working on my external hard-drive via USB. Now my question is, how can I boot to my windows vista without having to connect the external drive. (If I don't connect my external USB hard-drive before powering my pc, 
I can't boot because the GRUB files cannot be found... "GRUB rescue command shows up). So is it possible to boot vista regularly and still have Linux on the external drive? If it's possible, I reckon that I need the GRUB files to be on my internal hard drive, but how should I do that? I have little or no knowledge about programming...

Thanks in advance!
De_Flurk

---

### Post by sikander3786 on 2010-12-16
Welcome to the forums :-)

That sounds like you installed Grub (the Ubuntu bootloader) to your intenal HDD instead of the external one which in turn, replaced your Vista MBR already on the internal disk.

You need to repair startup from the Vista install/repair disc and then install Grub to the MBR of external one. That way, when you disconnect your external HDD, you'll be able to boot Windows ;-)

In order to let us know more about your setup, boot Ubuntu and post the output of bootinfoscript as per instructions here (with external HDD connected obviously).

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by de_flurk on 2010-12-16
Hey!
Thanks for the quick reply.
I also need to tell you that a had problems booting Linux the first day, so you're right about the GRUB being installed on my internal hard-drive. So here's the boot info file you asked for.
Looking forward to your reply!
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

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
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 408206912 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

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

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    31,602,687    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,602,688   976,771,071   945,168,384   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   307,202,047   307,200,000   7 HPFS/NTFS
/dev/sdb2    *    307,202,048   586,075,094   278,873,047  83 Linux
/dev/sdb3         586,076,158   625,141,759    39,065,602   5 Extended
/dev/sdb5         586,076,160   625,141,759    39,065,600  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-061E                              vfat       DellUtility                   
/dev/sda2        92C0A518C0A50397                       ntfs       Back-up                       
/dev/sda3        B854480E5447CDB6                       ntfs       Local Drive                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B81EA3DD1EA392C4                       ntfs       ExtWin                        
/dev/sdb2        9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        e5274fd4-1c4e-45e0-8d13-96a97949c7a9   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/ExtWin            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set 9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=9aee8ec2-64ac-4ff3-9737-5a7c4e03e56f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set b854480e5447cdb6
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e5274fd4-1c4e-45e0-8d13-96a97949c7a9 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 208.9GB: boot/grub/core.img
 176.7GB: boot/grub/grub.cfg
 209.0GB: boot/grub/stage2
 158.5GB: boot/initrd.img-2.6.35-23-generic-pae
 209.0GB: boot/vmlinuz-2.6.35-23-generic-pae
 170.3GB: grub/stage2
 158.5GB: initrd.img
 209.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by sikander3786 on 2010-12-16
There are a few more problems with your external drive as well. Grub Legacy is installed in the boot sector of sdb2 which doesn't need to be there. There is also a stage2 file being loaded. Grub2 is properly installed in the MBR of sdb as well so I hope you are able to boot Ubuntu successfully when you set the external device as the first boot device. Right?

For now, disconnect your external HDD. Boot a Vista install/repair disc/usb and perform startup repair (3 times at least). If you don't have a Vista repair disc, you can grab one here (it is legal).

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Or if that doesn't work, you can use bootrec.exe to do the repairs.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by de_flurk on 2010-12-16
Thanks a lot sikander3786! It now boots perfectly, even when I disconnect my external hard-disk. 
I forgot to mention that I still use half of the external hard-disk for some storage of files that can both be used in windows and Linux (Music, photos, etc.) and the other half of the external hard-disk for the Ubuntu operating system. But anyway, it works now, so I'm going to leave everything nicely were it is :P
Thanks for the fast and great support.
Greeting,
De_flurk

---

### Post by sikander3786 on 2010-12-16
You are more than Welcome :-)

Happy Ubuntu-ing!

---

