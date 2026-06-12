---
title: "Where to install grub-pc?"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2010-07-18
I installed v 10.04 to a USB flash drive and could boot up from it without difficulty. However, I encountered problems when trying to update everything immediately after installing.

I was asked where I wanted to install grub-pc and chose the flash drive only. However, I was told that that installation failed and that failure ultimately ruined the entire installation. I could have chosen to install grub-pc to various partitions on my internal hard drive (on which I'm running Windows), but thought that that was unnecessary.

When I was running v 9.10 from the flash drive, I wasn't, so far as I can recall, ever asked anything about installing the old-style grub to my internal hard drive.

What am I doing wrong about grub-pc and why did the original installation of 10.04 work, while only the updating failed? Wasn't grub-pc installed on the original installation?

Leslie

---

### Post by oldfred on 2010-07-18
Plug flash drive in and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

You should only install grub2 (grub-pc) to drives not partitions unless you are very advanced and understand significant issues with install to partitions. If you installed to the USB MBR that should have been correct.

---

### Post by lesliek on 2010-07-19
Thanks very much for replying, oldfred.

I hope it's not inappropriate to change the focus of this thread in light of later decisions by me.

I decided, instead of trying the live USB route, to try to install v 10.04 on the hard disk of my Windows netbook via Wubi. That worked, but I could see (from Googling) that I was going to face the same problem caused by grub2 when I tried to update that installation as I'd faced when trying to update the live USB installation.

I also discovered that I could downgrade from grub2 to the original grub. I decided that that's what I wanted to do, since I'm running v 10.04 on two other computers with the original grub with no problems. (I learnt that when one upgrades to 10.04 from earlier versions using the original grub, as I did, one isn't shunted to grub2.)

The instructions for the downgrade were in the Ubuntu community documentation on grub2. One of those instructions was to run sudo grub-install /dev/sdX.

I'm afraid I still don't know what device to name in that command.

I ran the script you told me about, with the following result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,823,654     7,823,592   7 HPFS/NTFS
/dev/sda2           7,823,655     7,871,849        48,195  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065    15,743,699    15,727,635   5 Extended
/dev/sdb5              16,128    15,743,699    15,727,572   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       bbdb8c34-e4d1-4dbe-b621-9ae21aea15da   ext4                                     
/dev/sda1        BCB4F1F4B4F1B0CE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        500CA7F00CA7CEF2                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"


======================== sdb5/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 500ca7f00ca7cef2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 500ca7f00ca7cef2
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bcb4f1f4b4f1b0ce
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb5/Wubi: Location of files loaded by Grub: =================


   4.6GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.32-21-generic
   4.0GB: boot/vmlinuz-2.6.32-21-generic
    .3GB: initrd.img
   4.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

I'd be very grateful if you could tell me from those results what device I should be naming in the grub-install command that I mentioned above.

Thanks again,

Leslie

---

### Post by oldfred on 2010-07-19
With wubi you do not install grub.

Wubi runs as a file inside the windows NTFS partition and uses the windows boot loader to boot so you can easily uninstall wubi. You see a grub menu but it is just showing the standard boot sequence for grub after the windows boot. Grub is not really used as a boot loader for the windows system.

I do not know wubi but if it works I would not mess with the grub as it is not the same set of instructions as a standard install.

---

### Post by lesliek on 2010-07-19
Thanks for your further reply, oldfred.

I won't try the downgrading from grub2 to grub then.

At the same time, maybe I should add something, just in case anyone else reads this and finds it helpful.

When I used Wubi, I installed v 10.04 as it was originally released and it worked fine.  However, after installing it in that form, I wanted to update all the packages in that original release to the current version. Two among the hundreds to be updated were grub-pc and grub-common. Those two weren't classified as security updates, but merely as recommended ones. I found that if I omitted only those two updates and installed all the others, everything continued to work fine. It must be something in one or other or both or those two packages that caused my problem, though I haven't any idea what. I'll just stay away from them in future.

Thanks again,

Leslie

---

### Post by sonikmh on 2010-07-27
Hello,

I would also like some advice regarding GRUB - I recently installed Ubuntu 10.04 over my 7.10 instalation and now I can run Ubuntu with no problem, but I can't boot up my windows which is on the first hdd (ubuntu is on the second hdd).

I tried to figure it out but I'm still not really sure what to do exactly to fix it.
Both partitions from the WinXP hdd are perfectly alright an mountable inside Ubuntu.

Here is my result from the script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251,0 GB, 251*000*193*024 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 30*515, celkem 490*234*752 sektor&#367;
Jednotky = sektory po*1 * 512 = 512 bajtech
Velikost sektoru (logického/fyzického): 512 bajt&#367; / 512 bajt&#367;

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    51,183,089    51,183,027   7 HPFS/NTFS
/dev/sda3          51,183,090   490,223,474   439,040,385   f W95 Ext d (LBA)
/dev/sda5          51,183,153   490,223,474   439,040,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80,0 GB, 80*026*361*856 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 9*729, celkem 156*301*488 sektor&#367;
Jednotky = sektory po*1 * 512 = 512 bajtech
Velikost sektoru (logického/fyzického): 512 bajt&#367; / 512 bajt&#367;

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1     154,302,464   156,301,311     1,998,848 Linux Swap
/dev/sdb2           2,048   154,300,415   154,298,368 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda: PTTYPE="dos" 
/dev/sda1        A09C952F9C950148                       ntfs       Nataliee                      
/dev/sda3: PTTYPE="dos" 
/dev/sda5        D2C44B3AC44B2059                       ntfs       Evellyn                       
/dev/sdb: PTTYPE="gpt" 
/dev/sdb1        12cc6eb2-f385-4735-8f38-da535b555f9e   swap                                     
/dev/sdb2        3438f3b4-c7c9-44d7-8d3d-df1c12fca62e   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/Evellyn           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/Nataliee          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
set locale_dir=($root)/boot/grub/locale
set lang=cs
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3438f3b4-c7c9-44d7-8d3d-df1c12fca62e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3438f3b4-c7c9-44d7-8d3d-df1c12fca62e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3438f3b4-c7c9-44d7-8d3d-df1c12fca62e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3438f3b4-c7c9-44d7-8d3d-df1c12fca62e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 3438f3b4-c7c9-44d7-8d3d-df1c12fca62e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a09c952f9c950148
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=12cc6eb2-f385-4735-8f38-da535b555f9e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda5
UUID=D2C44B3AC44B2059 /media/Evellyn     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=A09C952F9C950148 /media/Nataliee     ntfs    defaults,umask=007,gid=46 0       1

=================== sdb2: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  42.0GB: boot/grub/grub.cfg
  21.6GB: boot/initrd.img-2.6.32-21-generic
  21.6GB: boot/initrd.img-2.6.32-23-generic
  21.6GB: boot/vmlinuz-2.6.32-21-generic
  21.6GB: boot/vmlinuz-2.6.32-23-generic
  21.6GB: initrd.img
  21.6GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old
```

Thanks for any help!

---

### Post by oldfred on 2010-07-27
Your problem is totally different.

Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.
Or:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

[http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html](http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html)
GRUB 2 boot.img will go into the protective MBR (using the first 446 bytes of the MBR). Use legacy boot in BIOS ?if EFI boot jumps directly to boot partiion.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.
sudo parted /dev/sda set <partition_number> bios_grub on
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

---

### Post by sonikmh on 2010-07-30
Ohh, thank You! That finally worked well - the first solution from the comments of the bug :-)

---

