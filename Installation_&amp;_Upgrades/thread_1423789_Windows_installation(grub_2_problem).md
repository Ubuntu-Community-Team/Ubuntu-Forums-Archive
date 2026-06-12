---
title: "Windows installation(grub 2 problem)"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Irti on 2010-03-07
Hi..i know there are many articles online on how to get your windows installation to be recognized in grub, but they all are for grub legacy....i couldn't find one which works for grub2 which karmic uses...I installed ubuntu and now my windows wont start ..it shows up in grub2 but doesnt start..if anyone knows any how to for this(using grub2)..please post the link for me....thanks a lot

---

### Post by presence1960 on 2010-03-07
A little info about your setup would be nice. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Irti on 2010-03-09
Ummmmm...i did that...Here is what it says

irteza@ICTCTRGF:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/irteza/Desktop/boot_info_script*.sh: No such file or directory
irteza@ICTCTRGF:~$ 

I checked and I do have a desktop folder ..i tried saving it to some other folder by giving a different path...still not happening

---

### Post by presence1960 on 2010-03-09
> irteza@ICTCTRGF:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/irteza/Desktop/boot_info_script*.sh: No such file or directory
irteza@ICTCTRGF:~$
You have to move the file to the desktop then run the command.

---

### Post by Irti on 2010-03-09
ok am sorry if i am being a dumba** here.... i downloaded the file..it was named boot_info_script055.download ... i pasted it on the desktop... and tried all these steps..

1. I tried running the command you gave me ... same error
2. renamed the file to boot_info_script055.sh and ran the command as sudo     bash ~/Desktop/boot_info_script055.sh ... same error
3. ran the command as sudo bash ~/Desktop/boot_info_script*.sh ... same error
4. renamed the file back to  boot_info_script055.download and ran the command as sudo bash ~/Desktop/boot_info_script055.sh ... same error

and now i am at a total loss as to what i am doing wrong....

---

### Post by presence1960 on 2010-03-09
> **Irti said:**
> ok am sorry if i am being a dumba** here.... i downloaded the file..it was named boot_info_script055.download ... i pasted it on the desktop... and tried all these steps..

1. I tried running the command you gave me ... same error
2. renamed the file to boot_info_script055.sh and ran the command as sudo     bash ~/Desktop/boot_info_script055.sh ... same error
3. ran the command as sudo bash ~/Desktop/boot_info_script*.sh ... same error
4. renamed the file back to  boot_info_script055.download and ran the command as sudo bash ~/Desktop/boot_info_script055.sh ... same error

and now i am at a total loss as to what i am doing wrong....

Something is not right with the downloaded file. It should look like the picture below and have the name ```
boot_info_script055.sh
```right from the download. You should not have to change it or edit the extension (file type).

I even downloaded it again and the file name is boot_info_script055.sh not boot_info_script055.download

---

### Post by Irti on 2010-03-13
hey...am sorry i couldn't reply immediately ...got a little busy at job and couldnt find any time at all... i downloaded the file...it seems there was a problem with chrome in linux...it kept changing the extension to .download .... tried with mozilla and it worked just fine...thanks...here are the results .....


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16031603

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,392,639   102,392,577   7 HPFS/NTFS
/dev/sda2    *    102,392,640   143,352,719    40,960,080  af HFS
/dev/sda3         143,364,060   182,418,074    39,054,015  83 Linux
/dev/sda4         182,418,075   186,418,259     4,000,185   5 Extended
/dev/sda5         182,418,138   186,418,259     4,000,122  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E2886C26886BF785                       ntfs                                     
/dev/sda2        40318a5b-7514-3e47-be9f-c21919f2d851   hfsplus    disk0s2                       
/dev/sda3        d11f2057-14f8-4771-9573-c8dd266a39c9   ext4                                     
/dev/sda5        effa558f-0ddf-488e-9fb6-2d50b9b9ad03   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=irteza)
/dev/sda1        /media/E2886C26886BF785  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
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
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set d11f2057-14f8-4771-9573-c8dd266a39c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e2886c26886bf785
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Mac OS X (on /dev/sda2)" {
	insmod hfsplus
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 1947801834cdc56f
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 1947801834cdc56f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d11f2057-14f8-4771-9573-c8dd266a39c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=effa558f-0ddf-488e-9fb6-2d50b9b9ad03 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  76.5GB: boot/grub/core.img
  77.6GB: boot/grub/grub.cfg
  75.4GB: boot/initrd.img-2.6.31-14-generic
  76.5GB: boot/initrd.img-2.6.31-19-generic
  77.6GB: boot/initrd.img-2.6.31-20-generic
  75.4GB: boot/vmlinuz-2.6.31-14-generic
  76.2GB: boot/vmlinuz-2.6.31-19-generic
  77.1GB: boot/vmlinuz-2.6.31-20-generic
  77.6GB: initrd.img
  76.5GB: initrd.img.old
  77.1GB: vmlinuz
  76.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by presence1960 on 2010-03-13
About the only thing I noticed is you have the boot flag on OS X. Windows needs the boot flag to boot. Boot into ubuntu and open gparted. Right click on sda1 (windows xp) and choose manage flags. Tick boot. Click Close. Click green check mark to apply. Reboot and try booting to windows.

If you don't have gparted installed you can install it by running in terminal ```
sudo apt-get install gparted
```

---

