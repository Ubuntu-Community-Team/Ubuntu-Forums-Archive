---
title: "Bootmgr is missing - please help"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-02
After the computer being shut down for 9 hours, I restarted the computer after receiving the following message:
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

But when the computer restarts, it gives me the same message.
When I put in the Ubuntu 10.04 LTS live CD, it only gives me the option to restall everything or to run it as a tryout session.

Can anybody help me to fix the Bootmgr. Thanks.

---

### Post by khamil8686 on 2011-02-02
do you have a memory stick inserted into your computer when you are booting and it gives you that error?

---

### Post by F8M on 2011-02-02
At first I had the pen drive inserted.
But now, after unplugging the computer and making sure nothing was in the computer (CD/DVD, or chip, or perdrives), I restart the computer and have the same response.

---

### Post by khamil8686 on 2011-02-02
try reinstalling grub2 to see if it fixes it
[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

hope this helps :)

---

### Post by F8M on 2011-02-02
After trying all three methods from the Grub2 website, none worked when rebooted. Any other suggestions. thanks

---

### Post by lindsay7 on 2011-02-02
Do you windows on this computer, if so do you have the installation disk? If you do which version of windows do you have?

you can repair or reinstall the mbr using the windows install disk.

Or, you can take a look at this and see if this will fix your mbr.

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId928097](http://www.dedoimedo.com/computers/grub-2.html#mozTocId928097)

---

### Post by F8M on 2011-02-02
This computer has no windows on it. It only has Ubuntu 10.04 LTS.
Any other suggestions would be appreciated. thanks

---

### Post by khamil8686 on 2011-02-02
when i research the error youre having the only posts i can find are about dual booting windows 7 or vista and ubuntu so im not quite sure where to go next
did you have vista or windows 7 on the hard drive ever before?
also is 
"BOOTMGR is missing
Press Ctrl+Alt+Del to restart"
the entire error message that you are receiving?

---

### Post by lindsay7 on 2011-02-02
You can try this,
[http://www.ehow.com/how_6503785_fix-boot-manager-ubuntu.html](http://www.ehow.com/how_6503785_fix-boot-manager-ubuntu.html)

or try the Supergrub link I gave you before,

Did this computer ever have windows on it, if so what version.

This is another explanation of reinstalling grub and it may be useful.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by F8M on 2011-02-02
After checking my Ubuntu file system, it show my `mnt` file folder to be empty

---

### Post by lindsay7 on 2011-02-02
that does not mean anything at all. My system is fine and my mnt folder is empty too.

---

### Post by F8M on 2011-02-02
Just a little note of history about this computer. When I bought this computer last year, it came with Vista. After having constant problems, I totally reformatted the computer when I install Ubuntu 10.04LTS with some bios changes.
I`m still searching for a solution to fix my desktop computer. Any other suggestions would be helpful. Thanks

---

### Post by F8M on 2011-02-02
After typing in `sudo grub-install --root-directory=/mnt /dev/sda`
I have the following error
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by lindsay7 on 2011-02-02
Ok, I do not know what is going on with not being able to run those commands, but here is the way to reinstall the mbr for vista which you need any way. We can address the ubuntu installation later.

You can use your original vista install disk if you have it, if not download the startup disk form this site.  [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)  then follow this guide

[http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/](http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/)

When you reinstall the windows mbr you will have to reinstall grub. So we will work on that after the mbr is back, Grub will need to be reinstall using the info and links that you have already.

---

### Post by JC Cheloven on 2011-02-02
Ok, seems strange. My first impression is that you may have missed some step when reinstalling grub2. To start somewhere, you said you tried all three methods [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). Let's focus on method 3 ("chroot"). Did you bind-mounted the /dev branch of the filesystem? Your previous post suggests you didn't. 

Also, to review things, could you please post (from live) the output of ```
sudo fdisk -l
```, stating if possible whether you had a separate /home partition or not, and other pertinent info that could help in identifiyng your partitions?

One last question: you are able to navigate the filesystem in the hard disk from the live session, and access your documents, right? If so, please backup them from the live session, before something weird happens ;)

EDIT: @Lindsay: you posted while I wrote :) . Anyway, I think the OP said he hasn't windows in this pc.

---

### Post by lindsay7 on 2011-02-02
to JC:

He had vista installed at one time so he still has the vista mbr on the drive even though he formatted it. I am suggesting that he repair the vista mbr and then reinstall grub from scratch since the mbr repair will wipe it out.

And you are correct, we need to see the output of fdisk.

---

### Post by F8M on 2011-02-02
After typing in fdisk -l and using method 3 of the Grub2 website the is the result.The 1st(100 GB) is my storing drive and the 2nd(320 GB) is my boot drive.
Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12162    97682420    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38165   306554880   83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ run df -Th
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev  /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts  /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys  /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
ls: cannot access /media/100GB Drive: No such file or directory
ls: cannot access /media/100GB Drive: No such file or directory
ls: cannot access /media/100GB Drive: No such file or directory
ls: cannot access /media/100GB Drive: No such file or directory
done
root@ubuntu:/# update-grub
Good night---I will see which root to take tomorrow.Thanks for the help.

---

### Post by Quackers on 2011-02-02
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by F8M on 2011-02-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   613,111,807   613,109,760  83 Linux
/dev/sda2         613,113,854   625,141,759    12,027,906   5 Extended
/dev/sda5         613,113,856   625,141,759    12,027,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   195,366,887   195,364,840   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0b54f8c5-9c78-4c95-8494-bb38cfacdf98   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b71c468a-fdb9-4bfa-9ce7-1368550ca01b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5842DB8842DB6970                       ntfs       100GB Drive                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0b54f8c5-9c78-4c95-8494-bb38cfacdf98
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0b54f8c5-9c78-4c95-8494-bb38cfacdf98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b71c468a-fdb9-4bfa-9ce7-1368550ca01b none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
  52.7GB: boot/grub/grub.cfg
  51.7GB: boot/initrd.img-2.6.32-24-generic
  51.8GB: boot/initrd.img-2.6.32-27-generic
  51.8GB: boot/initrd.img-2.6.32-28-generic
  51.6GB: boot/vmlinuz-2.6.32-24-generic
  51.6GB: boot/vmlinuz-2.6.32-27-generic
  51.8GB: boot/vmlinuz-2.6.32-28-generic
 124.6GB: grub/core.img
 124.6GB: grub/grub.cfg
  51.8GB: initrd.img
  51.8GB: initrd.img.old
  51.8GB: vmlinuz
  51.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ba 9b 5d 68 93 3c 9b 3c  c7 09 eb 91 22 39 d3 69  |..]h.<.<...."9.i|
00000010  53 88 bd 9f 01 c1 e9 38  6a 4a 8c 60 06 d8 60 0d  |S......8jJ.`..`.|
00000020  99 67 43 0c e9 b8 ce 36  ae bd ab af 1d 17 3b 8c  |.gC....6......;.|
00000030  1b 10 eb ba d1 38 a4 b6  97 e1 61 b9 b6 05 f1 4d  |.....8....a....M|
00000040  ec b7 93 4f 84 c8 e7 d8  b4 28 7b 83 d3 00 e9 b4  |...O.....({.....|
00000050  2f 82 80 1f 88 06 34 07  bd 9c 07 4d 3e bc 63 8e  |/.....4....M>.c.|
00000060  cf 1b 11 6c 7a 91 e7 bc  4c aa 41 29 41 29 88 51  |...lz...L.A)A).Q|
00000070  99 67 44 0c 09 b9 ff 17  77 7d fb f9 fd b8 a1 90  |.gD.....w}......|
00000080  23 5a 10 3e cf f1 a6 d6  d4 96 36 40 9b 6c 45 98  |#Z.>......6@.lE.|
00000090  16 3f e2 ef e4 1a e3 ce  92 01 22 a6 a2 4e f1 bd  |.?........"..N..|
000000a0  ce ad a9 7a 6c 00 96 67  84 2c 8e 0a 13 3b 11 32  |...zl..g.,...;.2|
000000b0  11 64 39 10 44 03 f2 b5  e6 a1 27 13 9b 35 a1 41  |.d9.D.....'..5.A|
000000c0  99 67 45 0c 90 36 41 79  2c 4e 30 4b b1 b9 82 71  |.gE..6Ay,N0K...q|
000000d0  07 81 90 36 45 34 82 43  b1 13 4b 63 3c e1 a7 80  |...6E4.C..Kc<...|
000000e0  90 36 da 21 60 a8 68 d0  22 96 72 ae 93 f0 90 36  |.6.!`.h.".r....6|
000000f0  92 30 07 e9 b1 51 45 21  f4 51 c1 07 00 36 49 85  |.0...QE!.Q...6I.|
00000100  c2 87 06 8b c3 42 00 36  0e c6 f6 00 00 00 00 00  |.....B.6........|
00000110  99 67 46 0c f8 af e7 8f  e5 f8 e4 f6 47 73 2f 33  |.gF.........Gs/3|
00000120  37 af df 25 9a ff 17 f5  37 7a d6 d6 93 aa 56 45  |7..%....7z....VE|
00000130  ff 2b fd ff 7f b9 d5 cf  d6 db 45 4b 73 5f f2 2f  |.+........EKs_./|
00000140  e4 4f e4 1d fb 3a b9 32  c2 63 66 51 1c bb 66 76  |.O...:.2.cfQ..fv|
00000150  2c 51 8e 86 5a 15 f0 b4  41 5c 47 0d 82 85 74 c0  |,Q..Z...A\G...t.|
00000160  99 67 47 0c ef af 5e c8  fa b1 e7 fa 11 db b4 ee  |.gG...^.........|
00000170  ce 81 fb 2f e3 1b d2 47  34 9f 57 42 0b 31 8d c4  |.../...G4.WB.1..|
00000180  09 2b fb 60 22 a5 99 d4  ea f3 61 b0 e7 1d 0e 2c  |.+.`".....a....,|
00000190  ff c6 7d f9 4d 24 27 50  00 14 0a 10 25 3d d3 52  |..}.M$'P....%=.R|
000001a0  b9 93 03 03 ac 28 e7 3b  03 c3 38 17 03 85 1c 71  |.....(.;..8....q|
000001b0  99 67 48 0c ec 20 1c 70  bc 9c 4e 2d 5a 50 00 fe  |.gH.. .p..N-ZP..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 88 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc

```

---

### Post by oldfred on 2011-02-03
Do you still have BIOS set to boot from 100GB drive first as that is sdb? sdb had windows in the MBR but  you have not windows install.

If you set BIOS to boot the sda 320GB drive, it should boot.

---

