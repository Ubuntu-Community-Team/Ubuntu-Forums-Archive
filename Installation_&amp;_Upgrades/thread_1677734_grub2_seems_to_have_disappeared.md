---
title: "grub2 seems to have disappeared"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2011-01-29
Hi,

Could anyone help with this problem, please?

I have just installed Ubuntu 10.10 on a machine which also has Windows 7. Both OS are on a separate hard drive with Windows on the C: drive and Ububtu on the D: drive.

The installation proceeded without problems but when I rebooted after removing the live CD there was a string of error messages - must have been at least 50 - all complaining that there was a syntax error which finally ended with a grub> prompt.

I thought that perhaps I needed to reinstall grub and did:

sudo grub-setup -d /media/disk/boot/grub /dev/sda

and when that didn't work I tried:

sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda

which didn't work either. In both cases the error message was "Grub-setup: error: cannot stat /media/disk/boot/grub"

I tried again, this time substituting MEERKAT for disk but it still would not work

Is there any way round this problem?

---

### Post by Quackers on 2011-01-29
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Chris62 on 2011-01-30
Hello quackers and thanks for your help. I booted with the live CD and have run the script. I was going to copy the output (i.e. the contents of RESULTS.txt) here but I cannot open the file to copy it. Sudo gedit can't open it and su - requires a password so how can I get the file to you? It is fairly large (10 MB) and is too large to go as an attachment

---

### Post by Quackers on 2011-01-30
Just double click on results.txt and it should open, then copy the contents and post them in code tags.

---

### Post by Chris62 on 2011-01-30
I double clicked on results.txt but it wouldn't open. There was a message on a red bar saying "Unable to open document" and beneath that another message saying "File type plain text document (text/plain) is not supported.

---

### Post by Chris62 on 2011-01-30
Hi again,

I have just run the script on a different computer and double clicking the 'results.txt' file opened it so I have re-run the script on the computer that won't boot, obtained a fresh 'results.txt' but still can't open it. The error message is the same as before.

This is probably 'clutching at straws' but is it possible that the inability to open the file is anything to do with the processor? The computer in question has an AMD Athlon processor and is fairly old (in computer terms). I ask this because I had some Windows software that would not run on it and it turned out that it was because the software couldn't function with an AMD Athlon processor

---

### Post by sikander3786 on 2011-01-30
It shouldn't be related to the processor I think. Anyway, can you please attach that file with your post so we would try opening it here on our PCs and try find the problem.

---

### Post by Chris62 on 2011-01-31
Hi sikander, thanks for your message. Here, I hope is the 'results.txt' file as an attachment:

---

### Post by sikander3786 on 2011-01-31
> **Chris62 said:**
> Hi sikander, thanks for your message. Here, I hope is the 'results.txt' file as an attachment:
There is no attachment in your post.

---

### Post by Chris62 on 2011-01-31
hello again sikander,

I am not sure how to send an attachment. I clicked on the attachment button in the reply window and that opened a window headed "Manage attachments". I then put the path to 'results.txt' in the space under "Upload file from your computer", clicked on "Upload" and posted the reply. What have I done wrong and what should I have done?

---

### Post by sikander3786 on 2011-02-01
> **Chris62 said:**
> hello again sikander,

I am not sure how to send an attachment. I clicked on the attachment button in the reply window and that opened a window headed "Manage attachments". I then put the path to 'results.txt' in the space under "Upload file from your computer", clicked on "Upload" and posted the reply. What have I done wrong and what should I have done?
You did nothing wrong but I am not sure why that file didn't get attached :confused:

And that file is not opening up either on your computer. And without seeing it, we can't advise efficiently.

Anyway, you can follow this thread and try reloading Grub2. Simple method first if that doesn't work, try the chroot method.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
courtesy of forum member *drs305*

Good Luck!

---

### Post by Chris62 on 2011-02-01
Thanks for your message. I followed the link that you gave and re-installed grub2. when I re-booted the screen after screen of error messages had gone but unfortunately was replaced by 'grub rescue>'. I tried some of the commands that I found by googling 'grub2 rescue' but they all gave error messages of one sort or another so perhaps the best thing to do would be to format the hard drive containing Ubuntu and, perhaps, start again.

Anyway, thanks for your help - much appreciated. By the way, the name 'Sikander' rings a bell. Was he a friend of Alexander the Great?

---

### Post by kansasnoob on 2011-02-01
> **Chris62 said:**
> hello again sikander,

I am not sure how to send an attachment. I clicked on the attachment button in the reply window and that opened a window headed "Manage attachments". I then put the path to 'results.txt' in the space under "Upload file from your computer", clicked on "Upload" and posted the reply. What have I done wrong and what should I have done?

First of all right click on the RESULTS.txt and select Compress. That will create a tar.gz.

Then click on the paperclip thingy at the top of this reply box and when that window opens click on browse. Navigate to the directory where the RESULTS.txt.tar.gz is located (probably either Desktop or Downloads) then just double click the RESULTS.txt.tar.gz. 

Next click on Upload and wait for the progress bar at the bottom of that window to indicate the upload is complete. Then minimize that window and click on the paperclip thingy again. This time the file should appear so just click on it and it should attach.

---

### Post by amarendra on 2011-02-10
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have the similar problem. I installed Win7 on 10.10 which made  10.10's ext4 partition as unallocated. Later Recovered 10.10 partition suing TestDisk but I'm getting "BOOTMGR missing" error and can't boot into either OS. I want to get the same Ubuntu installation back. All the files/folders are intact on the recovered Ubuntu partition. By mistake I had written the TestDisk to start of HD I guess. 
boot script result( there were many disks connected. I formatted sda3 to ext3 and copied /boot from recovered sda5. sda5 is my Ubuntu 10.10 recovered partition, as visible):

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #8 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 109460673 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2          73,433,115   230,757,659   157,324,545   f W95 Ext d (LBA)
/dev/sda5    *    104,904,513   165,132,128    60,227,616  83 Linux
/dev/sda3                  63       192,779       192,717  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,683,519    15,683,458   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1cacbc9e-7185-46a0-96e4-a892c25e15d5   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1c5aa9a0-8df5-473a-89cf-b0f45ff0111a   ext3       boot-part                     
/dev/sda5        b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7   ext4       ubuntu-10.10                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BC15-545F                              vfat       FAKEER                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4130DD442010141E                       ntfs       Transcend                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        C0EA523FEA523240                       ntfs       Passport                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/1cacbc9e-7185-46a0-96e4-a892c25e15d5 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Transcend         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/Passport          fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d436d96036d943e0
	chainloader +1
}
menuentry "Arch (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0b882b2b-ab64-43bf-aa70-d36e659e25ad
	linux /boot/vmlinuz26 root=/dev/sda2
	initrd /boot/kernel26.img
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=263b8dcd-7517-4230-bd9d-6ae68ccff794 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  63.4GB: boot/grub/grub.cfg
  54.4GB: boot/initrd.img-2.6.32-27-generic
    ??GB: boot/initrd.img-2.6.35-24-generic
  79.3GB: boot/initrd.img-2.6.35-25-generic
  54.0GB: boot/vmlinuz-2.6.32-27-generic
    ??GB: boot/vmlinuz-2.6.35-24-generic
    ??GB: boot/vmlinuz-2.6.35-25-generic
  79.3GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d436d96036d943e0
	chainloader +1
}
menuentry "Arch (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0b882b2b-ab64-43bf-aa70-d36e659e25ad
	linux /boot/vmlinuz26 root=/dev/sda2
	initrd /boot/kernel26.img
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

=================== sda3: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.32-27-generic
    .0GB: boot/initrd.img-2.6.35-24-generic
    .0GB: boot/initrd.img-2.6.35-25-generic
    .0GB: boot/vmlinuz-2.6.32-27-generic
    .0GB: boot/vmlinuz-2.6.35-24-generic
    .0GB: boot/vmlinuz-2.6.35-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 81 00 00 3d 05 00 00  ee 28 ee 4b ee 28 ee 4b  |....=....(.K.(.K|
00000010  39 fd 1d 49 00 00 00 00  00 00 01 00 08 00 00 00  |9..I............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 74 bc 00 00  |............t...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 2a d9 11 3f  00 00 00 00 00 00 00 00  |....*..?........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 94 de d2 3b  00 00 00 00 00 00 00 00  |.......;........|
00000090  ee 28 ee 4b 94 de d2 3b  00 00 00 00 00 00 00 00  |.(.K...;........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 f2 01 00 00  ee 28 ee 4b ee 28 ee 4b  |.........(.K.(.K|
00000110  39 fd 1d 49 00 00 00 00  00 00 01 00 08 00 00 00  |9..I............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 75 bc 00 00  |............u...|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 2b d9 11 3f  00 00 00 00 00 00 00 00  |....+..?........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 94 de d2 3b  00 00 00 00 00 00 00 00  |.......;........|
00000190  ee 28 ee 4b 94 de d2 3b  00 00 00 00 00 00 00 00  |.(.K...;........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 fe  |................|
000001c0  ff ff 83 fe ff ff 26 37  e0 01 20 00 97 03 00 00  |......&7.. .....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-02-11
amarendra,

You have posted in several different threads, It would be best if you had posted in your own thread. We are all volunteers here and you end up with the same or similar answers in different thread when with one thread we can work together for a one better answer.

But you system is really messed up. I normally try to repair over reinstall, but in your case, I suggest you back up whatever you can and start over. Your Vista is missing & you do not seem to be able to get it back with Testdisk. You Ubuntu in sda5 want to boot from sda8 and grub is not installed to boot correct partition. I do not know about Vista, but you can reinstall Ubuntu in about an hours with most system. If you want Vista and have the full install then use gparted to create your partitions. If Vista is just a recover DVD then you have to install it first.

---

### Post by hjboisvert on 2011-03-09
i have the same problem, can you anyone help.  here's my result.txt file.

#

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: _________________________________________________________________________

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

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640   488,460,311   488,050,672  af HFS
/dev/sda3    *    488,722,456   732,747,791   244,025,336   7 HPFS/NTFS
/dev/sda4         733,009,936   956,979,735   223,969,800  83 Linux


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   488,460,311   488,050,672 HFS+
/dev/sda3     488,722,456   732,747,791   244,025,336 Linux or Data
/dev/sda4     733,009,936   956,979,735   223,969,800 Linux or Data
/dev/sda5     957,241,880   976,510,983    19,269,104 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2860-11F4                              vfat       EFI                           
/dev/sda2        b54fdeff-fb54-39c1-b86c-a76843ee7b65   hfsplus    Macintosh HD                  
/dev/sda3        6058549258546934                       ntfs                                     
/dev/sda4        3e2e7df7-b132-4a49-90d6-0977b9cee0a0   ext4                                     
/dev/sda5        c7f1ed5e-7b3b-4f96-8a2e-f561ac42a665   swap                                     
/dev/sda: PTTYPE="gpt" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3e2e7df7-b132-4a49-90d6-0977b9cee0a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3e2e7df7-b132-4a49-90d6-0977b9cee0a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set 3e2e7df7-b132-4a49-90d6-0977b9cee0a0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set 159145aba96ac496
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 159145aba96ac496 uuid
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
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
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
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set 159145aba96ac496
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 159145aba96ac496 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
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
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 384.0GB: boot/grub/core.img
 422.7GB: boot/grub/grub.cfg
 375.8GB: boot/initrd.img-2.6.35-22-generic
 375.6GB: boot/vmlinuz-2.6.35-22-generic
 375.8GB: initrd.img
 375.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

#

---

### Post by oldfred on 2011-03-10
@hjboisvert while you have boot issues just about everyone's is unique. Sometimes the solutions may be the same but configurations are almost always different. You do not have grub in MBR and have gpt. Is this a Mac, if so post the Apple subforum.

You can just try installing grub to the MBR.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If that does not work, Please start your own thread and please post boot script in code tags.
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

