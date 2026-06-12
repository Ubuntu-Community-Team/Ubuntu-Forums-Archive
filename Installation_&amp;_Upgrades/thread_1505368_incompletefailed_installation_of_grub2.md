---
title: "incomplete/failed installation of grub2"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by Krantarin on 2010-06-09
Grub2 failed to install when I got my first updates on Ubuntu, but it didn't seem like a big deal at first--since then, though, every time I try downloading anything through the software center, it tells me that "Previous installation hasn't been completed. The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

I have attempted to uninstall grub through the ubuntu software center with the exact same error message. Worse yet, when I try to install anything with a different program, it tells me "Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first." and I asked for help in correcting that previously [here,]("http://ubuntuforums.org/showthread.php?p=9433662#post9433662") but I think that this is the underlying problem.

I ran into an interesting dilemma when I ran the command I found [here.]("http://ubuntuforums.org/showthread.php?t=1459800&highlight=Previous+installation+hasn%27t+completed") Upon running ```
sudo dpkg --configure -a
```, it ran for a few moments but quickly showed me a blue terminal with "Package configuration" at the top and a "Configuring grub-pc" in red in the top-center of a lighter blue box. It told me "You chose not to install GRUB to any devices.  If you continue, the boot  &#9474; 
 &#9474; loader may not be properly configured, and when your computer next        &#9474; 
 &#9474; starts up it will use whatever was previously in the boot sector.  If     &#9474; 
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474; 
 &#9474; unable to load modules or handle the current configuration file.          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; If you are already running a different boot loader and want to carry on   &#9474; 
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474; 
 &#9474; boot loader, then you should continue anyway.  Otherwise, you should      &#9474; 
 &#9474; install GRUB somewhere.                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Continue without installing GRUB?
But I don't have a different boot loader (I don't think?) and if I press no, it simply returns me to the same page over and over again. It's a real pain. Should I just press <Yes> to continue without installing grub?

Edit: Or better yet, is there any way for me to get grub without a working software manager?

---

### Post by dino99 on 2010-06-09
your post is very confused :confused:

i've looked the other links you have posted; so i guess you have installed a fresh karmic distro and can load it as you can use control center :confused: or is it from an other linux distro ?

here is a little help on how to install ubuntu:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

if you want to install a package, mainly use synaptic (system admin synaptic) or a terminal (apps accessories terminal) with the command:

sudo apt-get install yourpackagename

for more help, look at links below

---

### Post by kansasnoob on 2010-06-09
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we should be able to put together a series of commands to complete the grub installation.

---

### Post by Krantarin on 2010-06-09
I apologize that my post is so confused, but I can't help it; so am I! I installed the most recent form of Ubuntu with Wubi a couple of days ago. I just had this problem when I connected to the Internet for the first time and tried to update last night. As I said before, I can't install anything using synaptic as you suggest because I've got an incomplete/unfinished/or already running installation.

Upon downloading the boot info script at Kansasnoob's suggestion, I ran these commands with these results: ```
davy@ubuntu:~$ sudo bash [path/to/the/download_folder]/boot_info_script*.sh
[sudo] password for davy: 
bash: [path/to/the/download_folder]/boot_info_script*.sh: No such file or directory
davy@ubuntu:~$ home/davy/downloads/boot_info_script*.sh
bash: home/davy/downloads/boot_info_script*.sh: No such file or directory
davy@ubuntu:~$ home/davy/downloads/boot_info_script055.sh
bash: home/davy/downloads/boot_info_script055.sh: No such file or directory
davy@ubuntu:~$ sudo bash home/davy/downloads/boot_info_script055.sh
bash: home/davy/downloads/boot_info_script055.sh: No such file or directory
davy@ubuntu:~$ 
```So I must have been doing something wrong. I checked the downloads folder to make sure it was there, and sure enough, the boot info script was sitting in my downloads folder at home/davy/downloads/. Any suggestions for my next step? I can't even get the boot info script to work with my limited knowledge of code. :confused:

---

### Post by kansasnoob on 2010-06-09
I'm lazy so I just cd the location:

```
cd Downloads
```

And:

```
sudo bash boot_info_script055.sh
```

Probably just because locations are case sensitive though.

---

### Post by Krantarin on 2010-06-09
OK, thanks. Here's the RESULTS.txt:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

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
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden HPFS/NTFS
/dev/sda2    *     26,626,048    26,830,847       204,800   7 HPFS/NTFS
/dev/sda3          26,830,848   625,140,399   598,309,552   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       117213e2-ffd9-4217-abd5-5be47fb3f38e   ext4                                     
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        32EC5968EC5926FF                       ntfs       SYSTEM RESERVED               
/dev/sda3        DA42609042607365                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set da42609042607365
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set da42609042607365
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set da42609042607365
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set da42609042607365
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 32ec5968ec5926ff
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

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

================= sda3/Wubi: Location of files loaded by Grub: =================


  15.4GB: boot/grub/grub.cfg
   4.6GB: boot/initrd.img-2.6.32-21-generic
   4.6GB: boot/initrd.img-2.6.32-22-generic
   4.5GB: boot/vmlinuz-2.6.32-21-generic
    .4GB: boot/vmlinuz-2.6.32-22-generic
   4.6GB: initrd.img
   4.6GB: initrd.img.old
    .4GB: vmlinuz
   4.5GB: vmlinuz.old

---

### Post by kansasnoob on 2010-06-09
Ah, it's a Wubi install, so in answer to your question:

> Should I just press <Yes> to continue without installing grub?

Yes.

Then see what happens.

---

### Post by Krantarin on 2010-06-09
Well, I just wiped the hard-drive, reinstalled Windows 7, and did an actual Ubuntu partition, not a Wubi one. It all seems to be working fine now. Thanks for all of the help!

---

