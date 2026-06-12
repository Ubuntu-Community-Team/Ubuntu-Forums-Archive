---
title: "Grub Rescue after ubuntu install"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by Matt D on 2011-02-11
I installed ubuntu onto my new pc onto some unalocated free space on my extenal hard drive but after the install my pc rebooted and got the error no such device: 0b1bf457-4057-4581-90dc-12fdcc1dd45a grub rescue. I have had no problem with installing ubuntu in the past but i guess it was because i installed in onto an external hard drive. My pc already has windows 7 installed on it as i wanted a dual boot. I tried editing the munu.lst to make it boot into windows 7 but the file was not in boot/grub and after searching for said file using alt+f2 the file was blank. What can I do I just want to be able to boot into ubuntu and linux.

---

### Post by Hakunka-Matata on 2011-02-11
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

What release Ubuntu did you install?  Current releases use Grub2, which is very different from Grub, no more menu.lst for one thing.

---

### Post by Hakunka-Matata on 2011-02-11
Grub Rescue prompt means you have Grub2 installed

---

### Post by Matt D on 2011-02-11
Yeah its grub 2 as I downloaded 10.04 from a torrent website as i couldn't find 10.10 and the downlaod from the ubuntu website was being realy slow.

---

### Post by Matt D on 2011-02-11
if i boot from the live CD is there anyway of altering the boot setting there such as using the terminal.

---

### Post by Hakunka-Matata on 2011-02-11
Live CD gives you everything an installed system gives you.  Terminal is located under Applications > Accessories

---

### Post by Matt D on 2011-02-11
i know that but how would i go about altering the grub menu so i can boot my pcinto windows and or linux

---

### Post by wilee-nilee on 2011-02-11
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Have the external HD plugged in when you run the script.

---

### Post by Hakunka-Matata on 2011-02-11
> **Matt D said:**
> i know that but how would i go about altering the grub menu so i can boot my pcinto windows and or linux

Sorry, I misunderstood your post.  You've got the expert helping now though, I'll butt out.  Good Luck

---

### Post by Matt D on 2011-02-12
here are the results 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   212,785,151   209,711,104   7 HPFS/NTFS
/dev/sda3         212,785,152   976,771,071   763,985,920   f W95 Ext d (LBA)
/dev/sda5         212,787,200   976,771,071   763,983,872   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,911,576,575 1,911,574,528   7 HPFS/NTFS
/dev/sdb2       1,911,578,622 1,953,517,567    41,938,946   5 Extended
/dev/sdb5       1,911,578,624 1,951,682,559    40,103,936  83 Linux
/dev/sdb6       1,951,684,608 1,953,517,567     1,832,960  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A2252522252435D                       ntfs       WinRE                         
/dev/sda2        3A3E7BCF3E7B82A5                       ntfs                                     
/dev/sda3: PTTYPE="dos"
/dev/sda5        18C4B862C4B84432                       ntfs       Data                          
/dev/sda: PTTYPE="dos"
/dev/sdb1        A60EFA090EF9D1F3                       ntfs       External                      
/dev/sdb2: PTTYPE="dos"
/dev/sdb5        0b1bf457-4057-4581-90dc-12fdcc1dd45a   ext4                                     
/dev/sdb6        16e7bece-311b-46d2-b62c-8e8467bff634   swap                                     
/dev/sdb: PTTYPE="dos"
/dev/sdc         9A6EAD6C6EAD41BD                       ntfs       New Volume                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0b1bf457-4057-4581-90dc-12fdcc1dd45a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0b1bf457-4057-4581-90dc-12fdcc1dd45a ro single
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 0b1bf457-4057-4581-90dc-12fdcc1dd45a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3a3e7bcf3e7b82a5
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=0b1bf457-4057-4581-90dc-12fdcc1dd45a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=16e7bece-311b-46d2-b62c-8e8467bff634 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 983.2GB: boot/grub/core.img
 996.3GB: boot/grub/grub.cfg
 983.3GB: boot/initrd.img-2.6.32-21-generic
 983.3GB: boot/vmlinuz-2.6.32-21-generic
 983.3GB: initrd.img
 983.3GB: vmlinuz

```
I currently have windows 7 and ubuntu on here but it mentions vista and xp not sure why though.

---

### Post by Matt D on 2011-02-13
I tried to do this from the grub rescue page but it came back with error unknown filesystem on the insmod linux command ```
set prefix=(hdX,Y)/boot/grub  # Example: (hd0,1) , (hd1,5)
set root=(hdX,Y)
insmod linux
linux /vmlinuz root=/dev/sdXY ro  # Example: root=/dev/sda1 , /dev/sdb5
initrd /initrd.img
boot
```

---

### Post by wilee-nilee on 2011-02-13
You have grub in the sda hd's mbr it should be in sdb the same hd where Ubuntu is installed. Boot a Ubuntu live cd and run these to commands. Also put the sdb hd first to be read in the bios.
```
sudo mount /dev/sdb5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Reboot to the grub menu choose the Ubuntu install and run
sudo update-grub
in its terminal.

---

### Post by Matt D on 2011-02-14
After doing that the message installation finished no eror reported is displayd but after the reboot the it still goes to the grub rescue screen.

---

