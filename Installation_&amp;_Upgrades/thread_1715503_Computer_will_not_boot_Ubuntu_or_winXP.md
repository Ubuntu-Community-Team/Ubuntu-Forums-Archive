---
title: "Computer will not boot Ubuntu or winXP"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by LIOTB on 2011-03-27
Good day everyone,

Thank you ahead of time for all your help, time and efforts.

I installed Ubuntu 10.10 on my xp (Media Center) machine. After restarting Ubuntu worked fine, but xp would boot, but only into a black screen with just a courser. I then tried to repair the MBR, after which all I get is an error and told to press ctr alt delete (please see attached photo).

I then attempted the liveCD option to try to fix it. But the things I found online were not exactly as I saw them (10.10 must be too new) and didn't work. However, I was able to get a full readout of my boot sector and other items.

Please note that when you look at my boot list you will find that I made a mistake and added some items. I am hoping we can go around that and delete those later (as I think I noticed on one site) after I boot into windows and can just use the dos window to delete them. The 5th/the one on the bottom is the real one. I put it as my default.

Can we do anything at all to save this poor machine? I have data that can not be saved by merely using liveCD and transferring files as some data is imbedded in programs.

 Thank you everyone for this forum, for Ubuntu, for all the contributions, hard work, fun, and sharing. This is just stupendous. I have wanted to try Linux for some time now and my friend introduced me to Ubuntu. I looked it up and saw how easy it was. I was hooked. 

Thank you again.

LIOTB

Here is the info I was able to retrieve:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,918,966   302,918,904   7 HPFS/NTFS
/dev/sda2         302,919,678   320,172,031    17,252,354   5 Extended
/dev/sda5         302,919,680   319,334,399    16,414,720  83 Linux
/dev/sda6         319,336,448   320,172,031       835,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1EA476A7A47680D7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        af272f29-d135-49f7-a4a7-88237f8bcc13   ext4                                     
/dev/sda6        d865007b-db03-4439-b25f-c0c3d073e013   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1EA476A7A47680D7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] timeout=30 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Xp Media Center Edition" /fastdetect multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" exti multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" exit multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="fixboot" fixbr multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 1ea476a7a47680d7
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
UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d865007b-db03-4439-b25f-c0c3d073e013 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 160.0GB: boot/grub/core.img
 159.7GB: boot/grub/grub.cfg
 157.0GB: boot/initrd.img-2.6.35-27-generic-pae
 157.8GB: boot/initrd.img-2.6.35-28-generic-pae
 159.9GB: boot/vmlinuz-2.6.35-27-generic-pae
 160.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 157.8GB: initrd.img
 157.0GB: initrd.img.old
 160.2GB: vmlinuz
 159.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by Rubi1200 on 2011-03-27
Hi and welcome to the forums :-)

Not sure what you have tried, but GRUB needs to be installed in the MBR.

From the LiveCD:


```
sudo mount /dev/sda5 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot, taking out the CD, and back in Ubuntu run this command to pick up the Windows install:

```
sudo update-grub

```

Let us know if this helps.

---

### Post by LIOTB on 2011-03-27
Dear Rubi1200,

Thank you for your gracious welcome and for your help. Such a splendid first experience all around.

The first part worked and Ubuntu is up and running again. Fhewww!! THANK YOU! I did the second part and all I get when I choose to boot to windows is a black screen with a blinking cursor. 

What can I do next?

Thank you much a head of time for your time and efforts!

LIOTB

P.S. I like the Star Trek homage in your avatar.

---

### Post by Rubi1200 on 2011-03-28
Did you run the update-grub command back in Ubuntu?

Try this:

```
 sudo os-prober
```Followed by```
sudo update-grub
```If that does not do the trick, then post the results of the boot script after running it again (this time you can do it from within Ubuntu).

Thanks.

---

### Post by LIOTB on 2011-03-28
Dear Rubi1200,

Thank you for that, no I had not performed the first step:
```
  sudo os-prober
```

After performing both steps I still have the same problem with a black screen and blinking cursor. Here are the results from the boot script. 

Again thank you.
LIOTB



```
               
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,918,966   302,918,904   7 HPFS/NTFS
/dev/sda2         302,919,678   320,172,031    17,252,354   5 Extended
/dev/sda5         302,919,680   319,334,399    16,414,720  83 Linux
/dev/sda6         319,336,448   320,172,031       835,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EA476A7A47680D7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        af272f29-d135-49f7-a4a7-88237f8bcc13   ext4                                     
/dev/sda6        d865007b-db03-4439-b25f-c0c3d073e013   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows Xp Media Center Edition" /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" exti 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="exit" exit 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="fixboot" fixbr 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1ea476a7a47680d7
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
UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d865007b-db03-4439-b25f-c0c3d073e013 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 159.6GB: boot/grub/core.img
 156.7GB: boot/grub/grub.cfg
 157.0GB: boot/initrd.img-2.6.35-27-generic-pae
 157.8GB: boot/initrd.img-2.6.35-28-generic-pae
 159.9GB: boot/vmlinuz-2.6.35-27-generic-pae
 160.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 157.8GB: initrd.img
 157.0GB: initrd.img.old
 160.2GB: vmlinuz
 159.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

```

---

### Post by Rubi1200 on 2011-03-28
Can you check in BIOS whether there is a large disk (may be called something else) option?

I want to know if your BIOS can "see" the end of the disk.

The reason:

the boot script results seem normal and apparently GRUB is picking up the Windows install.

the GRUB files are at the end of the disk, which may be a problem. The only thing is that it often causes a problem for Ubuntu booting rather than Windows.

In any event, check BIOS first. There are workarounds we can try afterwards.

The other thing is the boot.ini file. I think you need to restore the defaults (you seem to have edited it a number of times):
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by LIOTB on 2011-03-29
Again thank you and just as an update.

For some reason I cannot log in to my BIOS. It asks for a password which it has never done before. I tried all the back door ones and I don't remember every having put in place a password. However, perhaps this well help, when I use the disk utility, I see that the NTFS drive has 155GB, the extended is 8.8GB which is subdivided into 8.4GB ext4 and 428MB Swap. For a total of 164GB.

I will try the boot.ini tomorrow. That is what I wanted to do was "clear" it of all the junk I did to it. 

See you then and thank you.

Best,
LIOTB

---

### Post by Rubi1200 on 2011-03-29
Okay, let me know after editing the boot.ini if this helps you make progress with booting Windows.

---

### Post by LIOTB on 2011-03-29
Hello Rubi1200,

Thank you for your willingness and patience. I opened the boot.ini and deleted all that had wanted to do (had I known I could just open a text file and simply delete text, boy what time that would have saved). However, still the black screen and cursor. 

This is what it looks like now:
```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Xp Media Center Edition" /fastdetect

```

What do I do next? 

Thank you much,
LIOTB

---

### Post by LIOTB on 2011-04-03
Rubi,

I tried to run the fix the Master Boot Record but the same problems returned. As tried again to do the above directions I also got this:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sd
/usr/sbin/grub-probe: error: cannot stat `/dev/sd'.
ubuntu@ubuntu:~$ 

```

I don't know if that means anything to you. I am not sure if that error is significant as i couldn't find anything about it here on the forums. 

Thank you for your help. These is a big deal to have this computer running normally again.
Aaron

---

### Post by oldfred on 2011-04-04
You left off the a in sda. Drives are sda, sdb, sdc etc where the last letter is the drive number(letter?). And partitions are the numbers at the end or sda1, sda2, sdb1 etc.

So you mount the partition (sda5) with grub's files and install the grub2 boot loader into the MBR of the drive (sda).

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt [COLOR=Red]/dev/sda[/COLOR]

Where are you on booting windows. the above just reloads the grub bootloader.

---

### Post by LIOTB on 2011-04-04
Oldfred,

Thank you. Since Rubi's last comment I tried to do "fixmbr" again and it wiped out my grub again. I used the LiveCD and tried to fix the grub. The first try I had the mistake I just posted and then tried it again because it worked before. Then I received your post, oldfred, explaining to me what I had done wrong the first time. Thank you.

Now, I am following Rubi's directions again (not being critical, just saying what I am doing, I am so very grateful to Rubi) and this is what I get (see below). I will, right now, restart my computer and come to the menu where I hope, after choosing windows, will not leave me a black screen and with a cursor. I will post back here in a few minutes.

```

epiphaneers@Blessings:~$  sudo os-prober
[sudo] password for epiphaneers: 
Sorry, try again.
[sudo] password for epiphaneers: 
Sorry, try again.
[sudo] password for epiphaneers: 
/dev/sda1:Windows Xp Media Center Edition:Windows:chain
epiphaneers@Blessings:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-27-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Xp Media Center Edition on /dev/sda1
done
epiphaneers@Blessings:~$ 

```

Thank you again,
LIOTB

---

### Post by LIOTB on 2011-04-04
I just tried to boot into windows. Same result as before, black screen and cursor. 

What shall I do next?

Thank you,
LIOTB

---

### Post by oldfred on 2011-04-04
Boot script is not showing any real errors in the XP NTFS partition. Sometime something internal inside windows is not correct and it does not boot. Then windows repairs will often fix it.

Your boot.ini looks like you have edited it a lot. Sometime just a space at the end of a line can cause problems.

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

Sometimes chkdsk is all that is required also.

All the repair commands I know:

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by LIOTB on 2011-04-06
Thank you OF,

I am working on it right now. I did the XP disc option already, but I will try it again. If that does not work I will try the other options.

Most grateful.
LIOTB

---

### Post by LIOTB on 2011-04-06
Oldfred,

I did all that you said and I still get the same result. The text file was already in windows format. After I did that and cleaned out my boot.ini. Then I got your note.  I didn't do the fixmbr command, because I had performed that once when I  went through Rubi's instructions and once again before your notes. I  did do the other two commands however. When I choose windows xp MCE I get the same black screen and cursor. 

What shall I do next?

Thank you,
LIOTB

here is the configuration information:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,918,966   302,918,904   7 HPFS/NTFS
/dev/sda2         302,919,678   320,172,031    17,252,354   5 Extended
/dev/sda5         302,919,680   319,334,399    16,414,720  83 Linux
/dev/sda6         319,336,448   320,172,031       835,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EA476A7A47680D7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        af272f29-d135-49f7-a4a7-88237f8bcc13   ext4                                     
/dev/sda6        d865007b-db03-4439-b25f-c0c3d073e013   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Xp Media Center Edition" /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Xp Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1ea476a7a47680d7
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
UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d865007b-db03-4439-b25f-c0c3d073e013 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 159.6GB: boot/grub/core.img
 160.2GB: boot/grub/grub.cfg
 157.0GB: boot/initrd.img-2.6.35-27-generic-pae
 157.8GB: boot/initrd.img-2.6.35-28-generic-pae
 159.9GB: boot/vmlinuz-2.6.35-27-generic-pae
 160.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 157.8GB: initrd.img
 157.0GB: initrd.img.old
 160.2GB: vmlinuz
 159.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```

---

### Post by Quackers on 2011-04-06
When you previously ran the fixmbr command, did XP boot up at that time? On rebooting XP should have booted up directly (no grub menu first), did that happen?

---

### Post by LIOTB on 2011-04-06
Quackers,

thank you, no it didn't, just a black screen and cursor. That's when I had to do the LiveCD and use some of the instructions Rubi gave me. That got Ubuntu running again.

Grateful,
LIOTB

---

### Post by Quackers on 2011-04-06
This seems like a Windows problem. If you've restored the mbr of the disc (with fixmbr) and Windows still doesn't boot, then something is wrong with it.
Has Windows booted at all since you installed Ubuntu?

---

### Post by oldfred on 2011-04-06
I agree with Quackers that it is some kind of windows problem.

Did you by any chance change a BIOS setting. When I got a new motherboard I turned on AHCI in BIOS. Ubuntu still worked but my old XP did not work at all. Changed back to IDE mode and both worked again. Possibly that or maybe other BIOS settings.

---

### Post by LIOTB on 2011-04-06
Quackers and Oldfred,

No windows has not booted since I installed Ubuntu.

No BIOS settings were changed. Rubi asked that and I tried to get in, but it asked for a password. I never put one in place and I can't even log in to the BIOS. I could try to clear the CMOS by taking out the battery.

What do you suggest?

Thank you,
LIOTB

---

### Post by Hedgehog1 on 2011-04-07
During the side-by-side install of Ubuntu, the **parted** tool resized your windows partition to make room for the Ubuntu install.

I wonder if that resize step has left your windows partition in a less-then-preferred state.

To attempt a repair of the windows partition, please boot from the XP cd - and do this:

Select the Recovery Console command line interface, then run:

**chkdsk C: /R**

Once it completes, try to boot into XP again.


***The Hedge***

:KS

*There are only two chkdsk options in Recovery Console:
/P : Does an exhaustive check of the drive and corrects any errors. Does not check for bad sectors
/R : Locates bad sectors and recovers readable information. Includes functions of /P

---

### Post by debd on 2011-04-07
All the following codes can be copy-pasted into your terminal. I've modified them according to your boot script info.

*** all the commands has been taken from dsr305's guide at [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)  >>which is an awesome guide to restore grub. thanks dsr305 :)



boot into your normal ubuntu installation(not live cd) , make sure you have your internet connection working properly. Now run this codes:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sda5 /mnt/temp
```

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
```
```
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
```

```
sudo chroot /mnt/temp
```

If all the above commands ran successfully, the terminal prompt should include "root" 

now run:
```
apt-get update
```

```
apt-get purge grub grub-pc grub-common
```

then give :

```
apt-get install grub-common grub-pc
```

this will bring up a blue installation window in the terminal. you probably don't need them ; TAB to highlight "<OK>" and press ENTER.
Read the installation notes. TAB to "<OK>" to continue.
When presented with the device option, use the UP/DN keys to select sda (in your case)
Make sure the installation drive has an asterisk next to it ( example: [*] /dev/sda ).
 If it doesn't, highlight it and press the SPACE bar to select it.
*****Do not select a partition ( example: [ ] /dev/sda5 , etc).**
TAB to "<OK>" and press ENTER. When it has finishing the installation, you should have Grub 2 installed.

after installation is complete, you may run :

```
update-grub
``` 

this is not necessary, but good to do.

exit root mode with ```
exit
```

now run the following codes just to be safe:

```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```

reboot and see if it worked.

---

### Post by LIOTB on 2011-04-08
Hedgehog1 and debd,

thank you both. Wow! 

**_Hedge_**, I had tired that before and again after you suggested it, but there doesn't seem to be anything wrong (no errors), but still the black screen and white cursor. 

**_debd_**, wow my friend, that is stupendous! I looked through the forums, but sometimes it's hard to see if things are applicable. I will try this when I get home. 

You folks on here are champs!

Thank you!
LIOTB

---

### Post by LIOTB on 2011-04-09
debd,

I tried this three times. The first time it completely erased the boot menu all together and booted directly into Ubuntu. I tried it again and it brought back the menu but no windows. I did it again and windows is there but still boots into a black screen with a cursor. 

What can I do next?

Thank you everyone for your help and sacrifice this far.

LIOTB

here is my boot script after this attempt. 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,918,966   302,918,904   7 HPFS/NTFS
/dev/sda2         302,919,678   320,172,031    17,252,354   5 Extended
/dev/sda5         302,919,680   319,334,399    16,414,720  83 Linux
/dev/sda6         319,336,448   320,172,031       835,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EA476A7A47680D7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        af272f29-d135-49f7-a4a7-88237f8bcc13   ext4                                     
/dev/sda6        d865007b-db03-4439-b25f-c0c3d073e013   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Xp Media Center Edition" /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af272f29-d135-49f7-a4a7-88237f8bcc13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Xp Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1ea476a7a47680d7
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
UUID=af272f29-d135-49f7-a4a7-88237f8bcc13 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d865007b-db03-4439-b25f-c0c3d073e013 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 159.5GB: boot/grub/core.img
 160.2GB: boot/grub/grub.cfg
 157.0GB: boot/initrd.img-2.6.35-27-generic-pae
 157.8GB: boot/initrd.img-2.6.35-28-generic-pae
 159.9GB: boot/vmlinuz-2.6.35-27-generic-pae
 160.2GB: boot/vmlinuz-2.6.35-28-generic-pae
 157.8GB: initrd.img
 157.0GB: initrd.img.old
 160.2GB: vmlinuz
 159.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```

---

### Post by debd on 2011-04-10
LIOTB, I dont really know why it happened this way. Grub, in general picks up the bootable partitions without any problem. The possibility in this case may be a problem on your c drive. Speaking from experience, the repair feature of the windows installation disk never worked well for me ; but you may give it a try. Have you already?  And btw, I cant even understand a bit of your boot info script result as an surfing from mobile now, and its horrifingly formatted. Will take look letter.

---

### Post by LIOTB on 2011-04-11
debd,

Thank you much my friend. Yes, i have tried to repair the boot sector many times per my own research and then buy the guidance of those on this thread. Like you said, nothing new happened. Thank you for willingness and sacrifice.

LIOTB

---

### Post by oldfred on 2011-04-11
If grub gets you to a windows boot blue screen or windows does not boot with its boot loader in the MBR, then  repairs to grub will not help. It has to be something in windows.

Sometimes windows repairs say they work, but do not. And one repair pass fixes something that then the second try something else works. I would run windows chkdsk (until there are no errors) and rerun windows repairs.

---

### Post by LIOTB on 2011-04-12
oldfred,

that makes sense. I will run the boot fix again and chkdsk. I ran it a few times already before you contacted me and there were no errors at all, but I will do it again, if the principle is that something might be missed. Thank you for making me aware. 

Again thank you everyone. I will keep trying and get back to you. 

LIOTB

---

### Post by debd on 2011-04-12
LOITB, I just had a  sudden thought this morning. Have you heard about easyBCD ? Its a free software used to correct corrupted windows bootloader and boot files. Google it. You'll easily get to their home page. Now, am very doubtfull about running easyBCD.exe through wine or virtual box. I'd rather ask you to download the easyBCD bootable iso , burn a bootable disk of that. Now boot into it, and do make the right choise. I never used it, so I cant say what option to choose. But I've heard from friends, its pretty easy to use. Give it a try. 
But, if it rewrites the mbr(master boot record) , apparently you'll lose grub. Fear not; its no big deal to restore it. With my itching hands i've to do it now and then. :)
To restore grub, keep the commands I replied in a previous post handy..you may just keep it in a text file on your harddrive. boot from your ubuntu live cd, ** configure and connect to the internet. ** 
and then run the commands like you did previously.
If all these goes well, I think you should have a working dual boot system. :-) 

let us know. Good luck!

---

### Post by oldfred on 2011-04-12
XP has no BCD, so easyBCD.exe is for Vista or 7. Normally XP repairs work on XP or at least give some sort of blue screen with an error code.

---

### Post by debd on 2011-04-12
> XP has no BCD, so easyBCD.exe is for Vista or 7

I knew that; it has a option to restore xp booting as well. but, I think that needs a BCD bootloader. But Isn't it possible that easyBCD writes a BCD mbr that allows to boot into XP ?

---

### Post by oldfred on 2011-04-13
Win7 or Vista BCD boot loaders will add XP partitions to the BCD, so you can boot them, but not sure how to make it work without Vista or 7.

Supergrub often finds ways around issues and boots. It will boot windows as well as Linux.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by LIOTB on 2011-04-14
oldfred and debd,

I tried the supergrubdisk (1) and my computer will not boot at all now. I am going to use Rubi's instructions to repair it through live CD.

I think I will burn a Rescatux  disk and try it. Also I will try easyBCD. I will get back with you.

Thank you both,
LIOTB

---

### Post by LIOTB on 2011-04-16
Hello everyone,

I tried those and I still get the same result...Hummm, what could I be missing? I am not a certified tech,  nor programmer and I am a noob to Ubuntu,  but I am not wholly unfamiliar with computers. There must be something I am missing. Perhaps the order of things, a small detail. I wonder what. 

What is an option from here?

Thank you all for you help.
LIOTB

---

### Post by oldfred on 2011-04-16
If the windows repairs I posted in #14 using the XP disk do not repair it, then there is not much we can do to fix windows. There must be something else wrong with the windows partition even though script seems to show it is ok. But script only shows main files required for booting.

Have you checked in windows forums?

---

### Post by LIOTB on 2011-04-17
oldfred,

I will try those instructions again on Monday. No I have not gone to the Win forums, as I was thinking since this was caused only after I installed Ubuntu that the problem lay there. So, I will go there as well. 

If anyone has any ideas I am completely open to any suggestions? I would prefure not to have to install windows. I am a very busy person and having to reinstall everything would be a nightmare. 

Thank you much,
LIOTB

---

### Post by debd on 2011-04-17
I'm not so sure, but would Norton Ghost Image work in this case?

---

### Post by LIOTB on 2011-04-19
oldfred and debd,

I tried all the instructions again in post #14 multiple times and the results remain the same. 

debd, thank you for the suggestion about Norton, but how would that help at this moment other than back up. (I also try to stay as far away from Norton as I can.)

Does anyone else have any ideas?

Thank you so much to everyone who has tried to help me.

LIOTB

---

### Post by debd on 2011-04-19
> but how would that help at this moment other than back up. 

I dont really know how this piece of software works. but was wondering  if anything could be done with that. Wish some way could have helped.

Anyway, if you decide to reinstall XP, I have a suggestion for you.

This site: [http://ninite.com/](http://ninite.com/) creates a custom installer with the apps of your choise. Once you download and run the installer, the choosen apps are dloded and installed at one go. Therefore less fuss.

---

### Post by LIOTB on 2011-04-23
debd and everyone,

no worries mate. Thank you for the help and the suggestions. If you have anything else please let me know.

-debd, thank you, what do you have in mind for XP re-installation?

Thank you again, I can't tell you what it means that you all helped.

LIOTB

---

### Post by debd on 2011-04-23
> debd, thank you, what do you have in mind for XP re-installation?

"This site: [http://ninite.com/](http://ninite.com/) creates a custom installer with the apps of your choise. Once you download and run the installer, the choosen apps are dloded and installed at one go. Therefore less fuss."

this is what I said. but its worth giving a try if you have a internet connection with  a good speed; and not if you have connection like mine; at 0.24MBps :(

---

### Post by LIOTB on 2011-04-24
debd,

This is a great idea. I like file hippo because it keeps me up to date with one application, but this is nice because I don't have to go back and find them one at a time (even though I have created a restore folder of all my programs, because windows is well...you all can fill in the blank as you like.)

Thank you for the help and this suggestion will help a lot. 

Thanks again every one. For those for whom it applies - a very Happy Easter!
LIOTB

---

### Post by debd on 2011-04-24
I recently came accross an article that mentioned a package named 'ntfsprogs' (its in the synaptic). It is used to fix unbootable/corrupted windows(ntfs) drive from within ubuntu itself.  To use it, first unmount the windows partition if already mounted; and then run

```
sudo ntfsfix /dev/sda1
```

(assuming the windows partition is on /dev/sda1)

...sorry if it is a little late. :p have you reinstalled windows already?

---

### Post by Quackers on 2011-04-24
I'm thinking that Windows either can't find the hard drive, or it can't find its boot files. I don't know why that is as everything looks normal - but obviously it isn't.
The disk read error from the first post concerns me.

---

### Post by LIOTB on 2011-04-26
debd and Quackers,

Thank you. 

debd-  'ntfsprogs' was already on my computer and I did what you suggested. It ran through some scripted, but I still get the cursor and black screen.

Quackers-in subsequent tests and scans there weren't any errors, I am not sure the errors weren't from user error either - everything checked out.

Any ideas?

Again thank you!

LIOTB

---

### Post by LIOTB on 2011-04-26
> **debd said:**
> 

...sorry if it is a little late. :p have you reinstalled windows already?

No, not yet. Thank you much. Perhaps I didn't do it right. 

Thanks again,
LIOTB

---

### Post by LIOTB on 2011-10-07
Hello everyone,

I hope I can still get some help. I used a program that fixed the MB record. Let me back up. 

[U][B]I have been using Ubuntu successfully because of all the help in here and I am very grateful!

[/B][/U]As I was saying the MBR is fixed and only boots into XP now. I know the other partition is there, but how do I get the menu to chose to boot into both again?

Thank you for any assistance anyone can give.

LIOTB

---

### Post by dFlyer on 2011-10-07
you need to use the live cd for the version of ubuntu you have installed and reinstall grub. Just do a forum search on how to reinstall grub.

---

### Post by LIOTB on 2011-10-07
dFlyer,

Thank you, I was thinking that's what I had to do, but I couldn't remember. So much time has passed and so many other things on my mind. I will do that tonight and get back with everyone.

Thank you again,
LIOTB

> **dFlyer said:**
> you need to use the live cd for the version of ubuntu you have installed and reinstall grub. Just do a forum search on how to reinstall grub.

---

### Post by oldfred on 2011-10-08
See post #2 for instructions if it still is the same partition. Rubi1200 gave you the specific commands to run from a liveCD.

---

### Post by LIOTB on 2011-10-08
> **oldfred said:**
> See post #2 for instructions if it still is the same partition. Rubi1200 gave you the specific commands to run from a liveCD.
 
You are right, I feel bad about that. It has been so long and I skimmed over all the pages of the thread and I must have missed that...serious just the second one. I couldn't quite remember and I think I was looking for a wrong que. I am very grateful that you sacrificed your time to help a stranger. You have saved me a grate deal of head ache. I do appriciate Linux and really appriciate the forum community that exisits on the internet at large. Thank you. 
 
I will give this a shot and get back with you. 
 
Most grateful,
LIOTB

---

### Post by LIOTB on 2011-10-10
Well everyone after sevral months (Since Febrary, hey life happens, and I just used ubuntu - while were all were trying to figure out what happened to the MBR and grub - which I have grown to depend on) we finally got it. Thanks to the generosity of and sacrifice of the community.
 
This is the story on the quick. (Don't need to ready just know that I am so very grateful for everyone here)
 
I was fixing some other computers (learned a lot in the last while) came upon som fixit disks on line. I downloaded and explored - found a program that had a little button that said it could fix the Master Boot Record. It did so after 2 seconds something I had spent hours on after work doing manually, but for some reason never worked. After this Windows XP booted up (insert rejoiceing here). I came back here after the grub menu did appear (insert agony here). I had tried to use the disk to fix the grub as they said they could, I am still a noob and couldn't get them to work. So, I came back here and found I already had what I needed. Tryed to us my newly downloaded LIVE 11.4 disk and everthing came up fuzzy, frustrating after sevral tries waiting long periods, each time for the live CD to load. Then I just used the older verson, I did as Rubi (and others) pointed out from the beginning, but for some reason they worked this time. All is well with the world. Thank you all and it has been an adventure. Now if I could just figure out why my internet connection does not work even though it sees my wireless router. 
 
Thank you so very much eveyone, wow, what help there is here. This got my life going again. Places like this realy do make a difference in peoples' lives.
 
Warmest Regards to all, I just hope everyone who has helped me gets this receives a hundred fold in return. If there is a moderator who sees this I humbly pleade with you, if it's not too much trouble, to pass it along to all who helped me.
 
Thank you,
LIOTB

---

