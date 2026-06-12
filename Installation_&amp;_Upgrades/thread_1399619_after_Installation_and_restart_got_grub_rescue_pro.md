---
title: "after Installation and restart got grub rescue prompt"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Miki800 on 2010-02-05
hello community.

I just installed Ubuntu 9.10 on hd1 - /dev/sdb1
at the end of the installation I chose to install grub at hd0 - /dev/sda1

the file system I chose was ext4 for ubuntu "/" - 50 GB,
ext3 for "/home" - 5 GB, and 1.5 more for swap.

when the installation was complete I got the following prompt:

> GRUB loading
error: no such disk
grub rescue>
>


there was nothing I could do, pressing TAB did not show me all the commands like grub is expected to.
typing 'help' did not show any commands as well, instead it showed me - "NO SUCH COMMAND" or something like that (I did not took note of what the output was)


please assist me in fixing my setup.

I believe the problem is in the grub loader - which was not really installed properly in hd0 - /dev/sda1 (which is FAT32 - windows)

[edit]The following has failed in doing anything, this did not change a thing. this did not help[/edit]
since I did not see under "C:\" a 'boot' folder.
so I copied - using this live CD that I'm using right now - the 'boot' folder from the ext4 ubuntu installation to "C:\boot" under hd0 - /dev/sda1

hoping that the hidden grub installation that was supposedly installed under it will be able to see that folder and use it to boot properly.



now I'm asking myself, why am I going through this huge effort for?
who signed on releasing ubuntu 9.10 after beta as a working version without testing it's bundled grub2 to see if it's capable of booting a filesystem that is an option in the installation process of ubuntu?

why?


please assist me, I don't want to waste my time with boot loaders any more, all I want is my desktop back...

---

### Post by presence1960 on 2010-02-05
You should have installed GRUB on MBR (either /dev/sda or /dev/sdb) not a partition such as sda1 or sdb1. Plus you moved files around. I need to see exactly what you got on there & your boot process. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

P.S. This seems to be a case of user error not Ubuntu error. It should be fixed without a lot of effort.

---

### Post by Miki800 on 2010-02-05
that is funny, I just saw you answer the same thing to another user in another thread.
thank you for the super quick reply.


> 
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /grub.cfg /boot/grub/grub.cfg /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /boot/grub/core.img /IO.SYS 
                       /MSDOS.SYS

sda2: _________________________________________________________________________

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

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x057c057b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   976,768,064   812,921,130   f W95 Ext d (LBA)
/dev/sda5         163,846,998   389,142,494   225,295,497   7 HPFS/NTFS
/dev/sda6         389,142,558   976,768,064   587,625,507   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96589658

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    92,775,374    92,775,312  83 Linux
/dev/sdb2          92,775,375   488,392,064   395,616,690   f W95 Ext d (LBA)
/dev/sdb5         102,414,438   488,392,064   385,977,627   7 HPFS/NTFS
/dev/sdb6          92,775,501   100,101,014     7,325,514  83 Linux
/dev/sdb7         100,101,078   102,414,374     2,313,297  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        14FF59B7D52F0B71                       ntfs                                     
/dev/sda5        53FD66DF54BC2DC4                       ntfs                                     
/dev/sda6        BCFA2780CE0EDCA1                       ntfs                                     
/dev/sdb1        8f7cc702-e2b6-4a12-a81e-16a6e80f038a   ext4                                     
/dev/sdb5        4EE00CDF07EB33A4                       ntfs                                     
/dev/sdb6        6cc972c0-9dfc-490b-90ea-f47dcbc63404   ext3                                     
/dev/sdb7        fea2b7d5-f539-47ac-a262-a9aa7ecf2fde   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/14FF59B7D52F0B71  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6        /media/6cc972c0-9dfc-490b-90ea-f47dcbc63404 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /media/8f7cc702-e2b6-4a12-a81e-16a6e80f038a ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb5        /media/4EE00CDF07EB33A4  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/grub.cfg: ================================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-13-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-13-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-11-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-11-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 14ff59b7d52f0b71
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 14ff59b7d52f0b71
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-19-generic-pae
    .0GB: boot/vmlinuz-2.6.31-19-generic-pae
    .0GB: grub.cfg

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 8f7cc702-e2b6-4a12-a81e-16a6e80f038a
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 14ff59b7d52f0b71
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=8f7cc702-e2b6-4a12-a81e-16a6e80f038a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=6cc972c0-9dfc-490b-90ea-f47dcbc63404 /home           ext3    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=fea2b7d5-f539-47ac-a262-a9aa7ecf2fde none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-19-generic-pae
    .0GB: boot/vmlinuz-2.6.31-19-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz


---

### Post by presence1960 on 2010-02-06
First delete those boot directories/files you copied into the windows partition. They do not belong there. I would put GRUB on MBR of sdb and when that is done set 250 GB (sdb) hard disk as first in the hard disk boot order in BIOS.

Boot the 9.10 Live Cd. Choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sdb1 /mnt 
``` This will mount your Ubuntu root (/) partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` This will put GRUB2 on MBR of sdb.

Reboot without the Live CD & go into BIOS and set the 250 GB disk (sdb) as first to boot in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu. When the desktop loads open a terminal and run ```
sudo update-grub
``` This will update the GRUB menu.

One optional thing that I suggest. Your 500 GB disk has windows on it but has GRUB on MBR. Not a problem. But I would suggest to put windows bootloader back on MBR, but is not a necessity. If you want to do that from ubuntu run in terminal ```
sudo apt-get install lilo
``` this will install lilo. Then in terminal run ```
sudo lilo -M /dev/sda mbr
``` This will fix the sda MBR so if you ever put the 500 GB disk as first to boot in the hard disk boot order in BIOS it will boot right to windows.

---

### Post by presence1960 on 2010-02-06
```
================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

[COLOR="Red"]C:\wubildr.mbr = "Ubuntu"[/COLOR]
```

I see you had wubi installed at one point. You can remove the wubi reference from boot.ini either by going Control panel > System > Advanced > Startup & Recovery options. Somewhere in there there is an Edit button that will open boot.ini in Notepad. Remove only the reference to wubi. Leave the windows entry untouched. Close file and the wubi entry will be removed. You will no longer get that invalid ubuntu option when you boot windows. Or from Ubuntu open the boot.ini file and remove the entry for wubi.

I also see you have windows 95 boot files in XP: IO.SYS & MSDOS.SYS

---

### Post by Miki800 on 2010-02-06
> **presence1960 said:**
> First delete those boot directories/files you copied into the windows partition. They do not belong there. I would put GRUB on MBR of sdb and when that is done set 250 GB (sdb) hard disk as first in the hard disk boot order in BIOS.

Boot the 9.10 Live Cd. Choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sdb1 /mnt 
``` This will mount your Ubuntu root (/) partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` This will put GRUB2 on MBR of sdb.

Reboot without the Live CD & go into BIOS and set the 250 GB disk (sdb) as first to boot in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu. When the desktop loads open a terminal and run ```
sudo update-grub
``` This will update the GRUB menu.

One optional thing that I suggest. Your 500 GB disk has windows on it but has GRUB on MBR. Not a problem. But I would suggest to put windows bootloader back on MBR, but is not a necessity. If you want to do that from ubuntu run in terminal ```
sudo apt-get install lilo
``` this will install lilo. Then in terminal run ```
sudo lilo -M /dev/sda mbr
``` This will fix the sda MBR so if you ever put the 500 GB disk as first to boot in the hard disk boot order in BIOS it will boot right to windows.


thank you for the amazingly fast and seemed-trustworthy help!
I already am at the livecd Desktop right now
so you say lilo -M installs NTLDR? thats some news for me I had no idea, will try that out

great, I've installed grub on sdb as you suggested, seemed to have worked too

about this:
> 
sudo update-grub


can't I theoretically chroot into THAT ubuntu and then do that and it will work?

oh and since you seem like the perfect guy for this question - 

can't I install bootloaders in a way that will allow me to chose to run OS from sda or sdb without changing boot priorities in the BIOS?

btw - this sdb where I installed ubuntu is a USB Mobile Disk (HD)
is it possible that the BIOS will not recognize is sometimes?



I did all you instructed so far, I hope next time I read this is from a non-live-cd desktop :)

---

### Post by presence1960 on 2010-02-06
> **Miki800 said:**
> thank you for the amazingly fast and seemed-trustworthy help!
I already am at the livecd Desktop right now
so you say lilo -M installs NTLDR? thats some news for me I had no idea, will try that out

great, I've installed grub on sdb as you suggested, seemed to have worked too

about this:


can't I theoretically chroot into THAT ubuntu and then do that and it will work?

oh and since you seem like the perfect guy for this question - 

can't I install bootloaders in a way that will allow me to chose to run OS from sda or sdb without changing boot priorities in the BIOS?

btw - this sdb where I installed ubuntu is a USB Mobile Disk (HD)
is it possible that the BIOS will not recognize is sometimes?



I did all you instructed so far, I hope next time I read this is from a non-live-cd desktop :)

> can't I theoretically chroot into THAT ubuntu and then do that and it will work?

Yes see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") method # 3.

> so you say lilo -M installs NTLDR? thats some news for me I had no idea, will try that out

My mistake. I did not see you were missing NTLDR among all those files in the XP partition. You will have to restore NTLDR. Installing lilo and running that command makes the MBR be repaired to boot windows.

> can't I install bootloaders in a way that will allow me to chose to run OS from sda or sdb without changing boot priorities in the BIOS?
 Yes, but in my experience it is better to install GRUB to the disk that has Ubuntu on it. But it is supposed to work from any disk as long as the disk with GRUB on MBR boots first.

> btw - this sdb where I installed ubuntu is a USB Mobile Disk (HD)
is it possible that the BIOS will not recognize is sometimes? In that case you need a BIOS capable of booting from USB and must set the USB ahead of hard disk in the Device boot order so that when the USB is plugged in it will boot before the internal hard disk(s)

Since the sdb is an external disk you will be better served putting GRUB on the external disk and repairing the MBR of sda to boot windows. This way when you boot without the external windows boots & when you boot with the external GRUB takes over and you can boot into windows or ubuntu.

---

### Post by Miki800 on 2010-02-06
> **presence1960 said:**
> ```
================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

[COLOR="Red"]C:\wubildr.mbr = "Ubuntu"[/COLOR]
```

I see you had wubi installed at one point. You can remove the wubi reference from boot.ini either by going Control panel > System > Advanced > Startup & Recovery options. Somewhere in there there is an Edit button that will open boot.ini in Notepad. Remove only the reference to wubi. Leave the windows entry untouched. Close file and the wubi entry will be removed. You will no longer get that invalid ubuntu option when you boot windows. Or from Ubuntu open the boot.ini file and remove the entry for wubi.

I also see you have windows 95 boot files in XP: IO.SYS & MSDOS.SYS

well you can see everything with that little script of yours can't you? :D


from when I installed wubi - I can still jumpstart grub somehow, I'm not sure where the grub.cfg might be hidden, can it all be in wubildr.mbr?

maybe I can somehow upgrade THAT grub to something that can see more hard drives other then the current one?








> **presence1960 said:**
> Yes see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") method # 3.


I'll read that later! couldn't wait to see if all you said would work and it did! so I just did it without the livecd, it worked and I'm in ubuntu now thank you so much :)

> **presence1960 said:**
> 
My mistake. I did not see you were missing NTLDR among all those files in the XP partition. You will have to restore NTLDR. Installing lilo and running that command makes the MBR be repaired to boot windows.

actually once I restored MBR using that line you gave me into sda,
I could boot XP with NTLDR that was already there :) so no more fixing need to be done, both OS work great!

> **presence1960 said:**
> 
Yes, but in my experience it is better to install GRUB to the disk that has Ubuntu on it. But it is supposed to work from any disk as long as the disk with GRUB on MBR boots first.
as I just said and moreover then that - I have grub with sda under the wubi part that NTLDR can boot into, old grub and I have no idea how to upgrade it or where it's files are located.
I also have GRUB2 under sdb where I have ubuntu

THAT GRUB2 - can boot the XP's NTLDR under sda, that is just wonderful!

I wish it would be the other way around - that sda could boot GRUB2 which is the only GRUB among the two GRUBs I have that can boot another OS from ANOTHER HD.
why this is something I wish - because its a pain to make sure ubuntu boots after reset - for the BIOS to recognize my USB drive I need to turn it off and on real quick before the BIOS goes to the booting part, which is a huge pain and I need to remember that every time...
stupid hardware issues.

> **presence1960 said:**
> 
In that case you need a BIOS capable of booting from USB and must set the USB ahead of hard disk in the Device boot order so that when the USB is plugged in it will boot before the internal hard disk(s)

yeah I figured that THAT is what I need to do, but every time I reset without turning off and on the USB HD the BIOS does not see the HD again.
and if I do turn off and on the USB HD and go to the BIOS after once been there without it's configurations of being before the non-USB HD - those configurations are gone and I need to reapply them to the BIOS everytime after I disconnect the HD :(

> **presence1960 said:**
> 
Since the sdb is an external disk you will be better served putting GRUB on the external disk and repairing the MBR of sda to boot windows. This way when you boot **without the external windows boots** & when you boot with the external GRUB takes over and you can boot into windows or ubuntu.

yes, with the external HD I can boot into windows but not the other way around, when I choose wubi (which does not exist any more for some time now) I have grub, when I press 'c' in that old ancient grub and play around with it - 

It does not see sdb / hd1... it only sees sda / hd0.

the grub in the external HD sees them all!



well presence, you have proven you are superior to the ubuntu makers with your rapid solving problems ability, I thank you so much!

all I wanted after a really long day and night is to watch my favorite show and go to sleep and you made that happen with such little effort on my part.

I really appreciate it!

---

### Post by meierfra. on 2010-02-06
> I also see you have windows 95 boot files in XP: IO.SYS & MSDOS.SYS
They seem to be on every XP partition, but have size 0.   The next release of the boot info script won't show those ghost files anymore. 

> from when I installed wubi - I can still jumpstart grub somehow, I'm not sure where the grub.cfg might be hidden, can it all be in wubildr.mbr?

wubildr.mbr calls wubildr and wubildr is a boot loader  based on  Grub4Dos (Wubi 9.04 and older) and Grub2  ( Wubi 9.10)


>  for the BIOS to recognize my USB drive I need to turn it off and on real quick before the BIOS goes to the booting part, which is a huge pain and I need to remember that

Most boot loaders rely on the Bios to boot a USB drive. Since your bios seem to have problems detecting the USB drive,  neither Grub not Wubildr will be able to boot Ubuntu without your turning on and off  procedure. 

You might look into [PLOP]("http://www.plop.at/en/bootmanager.html"). Its the only  free boot loader I know which is able to boot a USB drive without bios support.

If PLOP does not work, you  might consider creating small  boot partition on the internal drive which holds the  Ubuntu kernels.

---

### Post by meierfra. on 2010-02-06
>  and all credit is his.
Not true. The boot info script would not exists without the influence and  inspiration of caljohnsmith.  In case anybody is interested, this is the thread which started the boot info script: [http://ubuntuforums.org/showthread.php?t=837791](http://ubuntuforums.org/showthread.php?t=837791)
Essentially, caljohnsmith had the idea, and I had the technical skill to implement it.

---

### Post by Miki800 on 2010-02-06
> **meierfra. said:**
> Not true. The boot info script would not exists without the influence and  inspiration of caljohnsmith.  In case anybody is interested, this is the thread which started the boot info script: [http://ubuntuforums.org/showthread.php?t=837791](http://ubuntuforums.org/showthread.php?t=837791)
Essentially, caljohnsmith had the idea, and I had the technical skill to implement it.

what matters to me is that it had been implemented! well done really!

> **meierfra. said:**
> wubildr.mbr calls wubildr and wubildr is a boot loader  based on  Grub4Dos (Wubi 9.04 and older) and Grub2  ( Wubi 9.10)

I wonder if I can download a wuildr thats of GRUB2 or edit the wubildr archive file to checkout it's grub.cfg and change it to what I want...


> **meierfra. said:**
> Most boot loaders rely on the Bios to boot a USB drive. Since your bios seem to have problems detecting the USB drive,  neither Grub not Wubildr will be able to boot Ubuntu without your turning on and off  procedure. 

You might look into [PLOP]("http://www.plop.at/en/bootmanager.html"). Its the only  free boot loader I know which is able to boot a USB drive without bios support.
sounds like a decent solution, I might check it out

> **meierfra. said:**
> If PLOP does not work, you  might consider creating small  boot partition on the internal drive which holds the  Ubuntu kernels.

this sounds really interesting - I'd like to make that happen
but I need to merge it with something like the existing wubildr so I don't destroy access to the ntldr XP loader which is very important as a safe stable fall back when I give up on ubuntu this year as well from some yet unknown reason as well as any year before that :) haha (maybe not this time, we'll see ^_^ )

---

### Post by Miki800 on 2010-02-06
I take it back - this did not work.

after I posted my happy-success posts I preformed the grub update - it asked me what to do, one of the options was to keep current grub and it's configurations - THAT is what I selected.

other then that I also upgraded everything that was possible according to synaptic and also 'activated' restricted drivers.

by the way, just for the sake of the test after I used LILO to restore XP's MBR I successfully booted into it as well.

after the first RESET (which came after the first time I successfully booted ubuntu) I got the same first prompt error message again:

> 
GRUB loading
error: no such disk
grub rescue>
> 

the thing is - I got it when the external HD was disconnected and when I made sure it was the first BIOS' choice of booting devices (two separated scenarios).

which could means a few of some things:
* upgrading grub corrupted XP's MBR
* upgrading grub installed a corrupted grub installtion under XP's MBR
* upgrading grub corrupted UBUNTU's working grub installtion
* upgrading something else using synaptic corrupted UBUNTU's MBR
* upgrading grub or something else corrupted UBUNTU's working grub configurations file (grub.cfg)
**but notice the fact that when I upgraded grub using synaptic (yes, after already upgrading it using the command line that you gave me as well)**

it asked me what to do with the current grub and I answered "KEEP IT"! why does grub developers team give such option if it does not apply and they change things no matter what?

if it worked before, and it does not work now - it's bound to be the fault of something that has changed from last time - so it has to be some upgrade.

as I write this I actually check the (mounted sdb1 path)/boot/grub/grub.cfg file - and it seems ok, just as before.

so I have no idea whats the cause of this behaviour!



**_[COLOR="Red"]BUT I DO REMEMBER THIS HAPPENING EVERY TIME AFTER I UPDATE A NEWLY INSTALLED UBUNTU - VERSION AFTER VERSION THIS HAPPENED TO ME EVERY YEAR SINCE 8.04 - 8.10 9.04 and now 9.10[/COLOR]_** - bold and caps not because I'm upset or anything - just wanted to make sure it's emphasized!
by **_[COLOR="Red"]THIS[/COLOR]_** I mean grub getting corrupt, I have to waste time fixing it.

(great, now my live cd is suddenly corrupt so I can not preform the actions which solved this problem previously
and I have no access to another computer to get a new image to burn it -_- what a huge waste of my time again)

---

### Post by meierfra. on 2010-02-06
Sorry,  presence1960 left out one step and I didn't catch  his omission.  One needs to tell  Ubuntu to install Grub to the external drive whenever Grub gets updated. 

Just follow the instruction from post 4 again.

Once  booted into Ubuntu:

```
sudo update-grub
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate

```

---

### Post by Miki800 on 2010-02-06
> **meierfra. said:**
> Sorry,  presence1960 left out one step and I didn't catch  his omission.  One needs to tell  Ubuntu to install Grub to the external drive whenever Grub gets updated. 

Just follow the instruction from post 4 again.

Once  booted into Ubuntu:

```
sudo update-grub
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate

```

I will, thank you - as soon as I clean this live cd and make sure it's operable again or get my hands on a new one.

I see you've added another line to what presence gave me the last time, since I want to know and I can't repair this with the corrupt live cd at my hand I will ask - what does debconf-communicate do that has to do with grub?


and also - how can I make sure that no other random grub update will take place -when I select update all using synaptic in the future- which might corrupt my grub again as before?

and why updating grub actually corrupts it?

---

### Post by meierfra. on 2010-02-06
> I wonder if I can download a wuildr thats of GRUB2 or edit the wubildr archive file to checkout it's grub.cfg and change it to what I want...
I'm sure one can do something like that. But I'm not sure how easy it would be.


> but I need to merge it with something like the existing wubildr so I don't destroy access to the ntldr XP loader which is very important as a safe stable fall back when I give up on ubuntu this year as well from some yet unknown reason as well as any year before that
There are  ways to   keep XP in the MBR and access Grub  from the XP boot menu.  But they are not as reliable as installing Grub to the MBR. 
And I don't  think the  "safe stable fall back" is all that important. Running   the lilo command from  post 4  (or fixmbr from a XP CD) will restore direct  access to the XP boot loader at any time you  need  it.


> I see you've added another line to what presence gave me the last time, since I want to know and I can't repair this with the corrupt live cd at my hand I will ask - what does debconf-communicate do that has to do with grub?


and also - how can I make sure that no other random grub update will take place -when I select update all using synaptic in the future- which might corrupt my grub again as before?

and why updating grub actually corrupts it? 


You don't need to be afraid of Grub updates. You just have to make sure they are done right. Currently  Grub/kernel updates  trigger the command

```
grub-install /dev/sda
```

this installs Grub to the mbr of the interal drive, causing all your problems.

```
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate
```

will tell Ubuntu to use

```
grub-install /dev/sdb
```

instead. Now Grub will be installed to the MBR of  your external drive and you should not have any more problems.


Are you currently able to boot from your external drive?  If yes,  you won't need the  Live CD.  Just boot into  Ubuntu from the external drive and then

```
sudo grub-install  /dev/sdb
sudo update-grub
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```


> - it asked me what to do, one of the options was to keep current grub and it's configurations - THAT is what I selected.
In the future, choose the new one. That way you will have access to the new kernels.

---

### Post by presence1960 on 2010-02-06
I see a little has gone on since I retired for the night. Thanks meierfra. That thread you linked to about the beginnings of the boot info script provided some insight into it's origins.

Maybe I will have to edit my line that says all credit is yours. I added that line because quite a few people I have attempted to help have referred to the script as "that little script of yours(me)." I don't really want anyone to think it is mine or that I have anything to do with it. I am just an end-user and appreciate the work done with the script so we have a wonderful tool to troubleshoot problems. That script saves a lot of time, experimenting and heartache. Again, thanks meierfra.

---

### Post by Miki800 on 2010-02-06
thank you both, my OSs are working again, this is solved.

---

### Post by TriadHonor on 2010-02-07
The solution is really simple and require to use Windows, not Linux.

Just read my guide ---> [http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)

Also Also SourceForge use the same method to fix this.

---

### Post by presence1960 on 2010-02-07
> **TriadHonor said:**
> The solution is really simple and require to use Windows, not Linux.

Just read my guide ---> [http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)

Also Also SourceForge use the same method to fix this.

I know about that solution, but if you read the entire thread here you will see that solution does not apply here as the OP no longer has wubi installed.

---

### Post by fasat2112 on 2011-08-16
Dear users,

I found a simple solution for this screen:
grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,5) (hd1,4) (hd1,3) (hd1,1)
grub rescue>
grub rescue> (hd1,1)
error: unknown filesystem
grub rescue>

even worse:
grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,5) (hd1,4) (hd1,3) (hd1,1)
grub rescue>
grub rescue> (hd1,1)
error: unknown disc
grub rescue>

Practicly my HDD vanished from DOS and also LiveUbuntu.

What next?

Simple.

Use small like 4GB USB key and DVD-Rom.
Install 10.04 or 10.10 Ubuntu from DVD to USB key, GRUB reinstalls on USB key, take from vanished HDD all data you had, then wipe HDD to reinstall Win XP and UBUNTU on same disc.

My problem was GRUB crashes completle NO WINDOWS, NO UBUNTU, NO GRUB, nothing, like I didn't had no HDD installed.

I was trying for almost 2 days, read all compatible forums to rewrite this mess and I find solution that actualy work with no extra knowledge of running commands. If GRUB installed on first install of UBUNTU on HDD why not on USB key. Instalation takes around 2x more time for writting to USB key.

I hope some helps this post.

BR

NOTICE:
-I had dual boot XP and UBUNTU on same HDD when crash GRUB loader
-also if NOT work FIXMBR nor FIXBOOT from XP rescue system

---

