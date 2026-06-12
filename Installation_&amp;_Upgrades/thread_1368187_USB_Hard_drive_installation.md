---
title: "USB Hard drive installation"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by richard.scott-ettrick on 2009-12-30
I have Ubuntu Karmic Koala installed on a Philips USB Hard drive. Since updating it from version 15 to 16 generic it will not start. It shows Grub then after choosing one of the options it shows the white Ubuntu logo. I then shows a black screen as if trying to start but it goes no further. Can anyone please help me with this?:confused:

---

### Post by presence1960 on 2009-12-30
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by richard.scott-ettrick on 2009-12-30
============================= Boot Info Summary: ==============================

```
 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks for 
    (UUID=1aec1e92-e75a-4444-ba20-f848cf74b6d3)/boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 168200550.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75349890

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   488,395,119   457,593,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a73b7ca

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   157,967,144   157,967,082  83 Linux
/dev/sdb2         157,967,145   168,200,549    10,233,405   5 Extended
/dev/sdb5         157,967,208   168,200,549    10,233,342  82 Linux swap / Solaris
/dev/sdb3         168,200,550   488,392,064   320,191,515   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
sda2: UUID="36F8A821F8A7DD7D" LABEL="RECOVERY" TYPE="ntfs" 
sda3: UUID="9414ABD814ABBB9C" LABEL="OS" TYPE="ntfs" 
sdb1: UUID="1aec1e92-e75a-4444-ba20-f848cf74b6d3" TYPE="ext4" 
sdb5: UUID="96b189f4-d58a-4b69-abd2-83fde114ab10" TYPE="swap" 
sdb3: LABEL="FAT32USB" UUID="2E7E-A4A6" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-16-generic root=/dev/sde1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-16-generic root=/dev/sde1 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sde1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sde1 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 20f4af3af4af10d8
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sdc1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sdc1 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdc1)" {
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 74a7a888-a25e-4674-bbe7-5faa107efb2b
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
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
# / was on /dev/sdd1 during installation
UUID=1aec1e92-e75a-4444-ba20-f848cf74b6d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=70730c1e-c0cb-47cc-89f3-13e9ae352f8a none            swap    sw              0       0
# swap was on /dev/sdd5 during installation
UUID=96b189f4-d58a-4b69-abd2-83fde114ab10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by presence1960 on 2009-12-30
Two things I noticed- your fstab says / was on sdd1 during installation but is now on sdb1. That really should not matter too much because the UUID is correct.

But your grub.cfg is messed up. In the Linux OS section your karmic kernel 2.6.31-16 does not have a (hd1,1) designation or line in it's stanzas. Then for whatever reason your karmic kernels 2.6.31-14 thru 16 are showing up in the OS prober section.

I would reinstall GRUB2. Boot the Live CD & choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```
This will mount your ubuntu root partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

This will install GRUB2 to MBR of external disk (sdb) and generate a new grub.cfg

reboot without the Live CD & try booting into Ubuntu.

---

### Post by richard.scott-ettrick on 2009-12-30
This operation appears to have failed. Grub loads quicker but after the ubuntu logo I get a blank screen.

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb 
Installation finished. No error reported. 
This is the contents of the device map /mnt//boot/grub/device.map. 
Check if this is correct or not. If any of the lines is incorrect, 
fix it and re-run the script `grub-install'. 

(hd0)	/dev/sda 
(hd1)	/dev/sdb 
(hd2)	/dev/sdc 
(hd3)	/dev/sdd 
ubuntu@ubuntu:~$ 
```
Above is trhe output from the terminal screen. Anything else I can try?

---

### Post by bwallum on 2010-01-02
From what I can see from the above you have probably complicated the mount and added a "/" at the end of the designated grub directory. You don't need to create a directory if it exists either.

Remember that grub2 does a lot of things automatically. You only need to tell it the drive (to install to the mbr) which is typically sda and the partition which contains the os boot up information, typically sda1 (the first partition on the first hard drive). You can also use labels. My boot up Ubuntu drive is labelled "Ubuntu0" so to restore grub on my first hard drive sda I use the command ```
sudo grub-install --root-directory=/media/Ubuntu0 /dev/sda
```

You'll need to be careful when updating your external usb drive. If updates include changes to Grub2 you will find that you lose the Grub2 configuration for your internal drives. If you then run the above to correct the Grub2 configuration on your internal drives AND you leave the usb external drive attached, you will no longer have a good configuration on the external drive. So, I recommend that you detach the external drive prior to resetting the Grub2 configuration on your internal drives.

I learnt from this link, it works for me. Welcome to the forum!
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jenaniston on 2010-01-02
The boot_info_script044.sh I just downloaded works great in this Ubuntu 9.04 1GB USB boot-up.
Thanks for the link - this will now be handy for troubleshooting another computer.

Now, I'm about to restart and see if I can figure out the command in Fedora terminal . . .

cd into directory RESULTS.txt gets put . . 
> 
[root@localhost Download]# bash boot_info_script044.shThanks again.

---

### Post by presence1960 on 2010-01-02
> **richard.scott-ettrick said:**
> This operation appears to have failed. Grub loads quicker but after the ubuntu logo I get a blank screen.

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb 
Installation finished. No error reported. 
This is the contents of the device map /mnt//boot/grub/device.map. 
Check if this is correct or not. If any of the lines is incorrect, 
fix it and re-run the script `grub-install'. 

(hd0)	/dev/sda 
(hd1)	/dev/sdb 
[COLOR="Red"](hd2)	/dev/sdc 
(hd3)	/dev/sdd [/COLOR]
ubuntu@ubuntu:~$ 
```
Above is trhe output from the terminal screen. Anything else I can try?

Where did sdc & sdd come from? They were not in the results.txt file produced by the boot info script? What type of device are sdc & sdd?

---

### Post by richard.scott-ettrick on 2010-01-05
I think they must have come from the pc that the usb disk was originaly set up on which has 3 hard drives in it.

---

### Post by richard.scott-ettrick on 2010-01-05
Thanks to all who hel[ped with this topic. I now have it sorted.

---

