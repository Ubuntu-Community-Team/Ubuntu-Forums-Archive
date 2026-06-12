---
title: "Cant boot back into windows"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by slowhands36 on 2010-03-25
I had ubuntu installed on 2nd hard drive but i didt use entire drive so i reinstalled on 2nd hard drive and used entire drive 500gb.Now i cant boot back into windows 7 it loads the boot menu from previous ubuntu installation and it also has the last ubuntu menu too  but when i choose windows 7 loader it takes me to the previous ubuntu and windows 7 select screen  also i cant see the main hard drive from in ubuntu  and advice would be greatly appreciated  My windows 7 installation disk is a iso file i got from miscrosoft on release day   how can i fix my boot part on windows 7 now...

---

### Post by lindsay7 on 2010-03-25
do this and lets see what your boot info looks like,


Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link below to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command 
Code:
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 courtesy of community member meierfra
__________________

---

### Post by slowhands36 on 2010-03-25
iam sorry  i dont know what you mean by link in your signature  i booted from the live cd and choose try without installing   but iam not sure what you mean by link in your signature

---

### Post by oldfred on 2010-03-25
I think lindsay7 copied another post where they had the link in their signature. Version is up to 55 now.(I think)

This is the  link to current version.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by slowhands36 on 2010-03-25
This is it hope i done it right 

> 


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=068e8022-85eb-44aa-9a69-0369564d4b72)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc754c404

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d79c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   958,678,874   958,678,812  83 Linux
/dev/sdb2         958,678,875   976,768,064    18,089,190   5 Extended
/dev/sdb5         958,678,938   976,768,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       88acfcc0-60f8-41b5-84cd-adc1e239ec75   ext4                                     
/dev/sda1        1E14C46F14C44C09                       ntfs                                     
/dev/sdb1        068e8022-85eb-44aa-9a69-0369564d4b72   ext4                                     
/dev/sdb5        06d4e65e-e4db-4644-9fe7-4e8fe7e562bc   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.5GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.8GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.5GB: boot/vmlinuz-2.6.31-20-generic
   1.8GB: initrd.img
    .6GB: initrd.img.old
   1.5GB: vmlinuz
    .6GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set 068e8022-85eb-44aa-9a69-0369564d4b72
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 068e8022-85eb-44aa-9a69-0369564d4b72
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=068e8022-85eb-44aa-9a69-0369564d4b72 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 068e8022-85eb-44aa-9a69-0369564d4b72
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=068e8022-85eb-44aa-9a69-0369564d4b72 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 068e8022-85eb-44aa-9a69-0369564d4b72
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=068e8022-85eb-44aa-9a69-0369564d4b72 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 068e8022-85eb-44aa-9a69-0369564d4b72
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=068e8022-85eb-44aa-9a69-0369564d4b72 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e14c46f14c44c09
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
UUID=068e8022-85eb-44aa-9a69-0369564d4b72 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=06d4e65e-e4db-4644-9fe7-4e8fe7e562bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.3GB: boot/grub/core.img
   1.1GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   1.6GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.31-20-generic
   1.6GB: initrd.img
    .8GB: initrd.img.old
   1.6GB: vmlinuz
    .6GB: vmlinuz.old

---

### Post by slowhands36 on 2010-03-25
looks like it still has wubi installed from previous ubuntu installation

---

### Post by lindsay7 on 2010-03-25
Yes, sorry, (thanks old fred) I cut off a  line in my post which should have said

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by slowhands36 on 2010-03-25
lol  np  i posted the file  hope that its done right...looks like it stull has wubi installed from previous installation  can you remove the wubi

---

### Post by oldfred on 2010-03-25
You normally uninstall wubi from inside windows.

You seem to be missing this file from your windows.
/Windows/System32/winload.exe

I would suggest to install grub2 to the sdb drive and after we fix windows you can boot from that by changing the primary master in BIOS. When we fix windows it will probably install the windows boot loader to sda which will be ok if we have installed grub to sdb, otherwise we still have to reinstall grub to sda after fixing windows. Grub works a little bit better if it is on the same drive as the Ubuntu install and since you have two drives you can leave the windows boot loader in sda.

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

Some BIOS have to have a boot flag to let you boot. Windows has to have a boot flag on the bootable partition, but linux does not use one. So I would still put a boot flag on sdb1 in case your BIOS requires one to boot. You can use the liveCD or gparted and right click on the partition to manage flags or from Ubuntu:

set boot flag on for sdb1 (off on others)
sudo sfdisk -A1 /dev/sdb



Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

If you have to reinstall from the liveCD:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by slowhands36 on 2010-03-25
ok thats were my problem is   the only installation disk i have for my windows 7 is a iso image i burnt to disk to install windows 7 with.It wount do anything when i put disk in and bootup  it wont start the windows installation  it would work if i could get booted into windows to run it but i cant boot into windows 7   i dunno what to do to fix the windows 7 to boot into it...**SOLVED**

---

### Post by lindsay7 on 2010-03-25
take a look at this,

[http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)

---

### Post by oldfred on 2010-03-25
Linsey7,
I have done the same thing where I copy and paste a link from here and it does not save the full link. I have one or two in my notes that I wish I knew where they linked to. The forum seems to shorten the links and you can only save  to text after clicking thru.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

---

### Post by lindsay7 on 2010-03-25
yup, it is not my night for cut and paste!  I copy something that I used in another post and it does not copy the whole line.

Thanks for catching it.

---

