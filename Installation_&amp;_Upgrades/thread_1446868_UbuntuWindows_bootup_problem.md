---
title: "Ubuntu/Windows bootup problem"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by jerry950 on 2010-04-04
I just installed ubuntu on WD passport. It boots up okay with ubuntu. But when I 
disconnect the Passport. The Windows Xp laptop will not boot up with windows. I do not 
get the bootup menu choices either unless the passport is connected, I just get a 
GRUB error message. How can I setup booting with windows as the default?

---

### Post by earthpigg on 2010-04-04
0. in the future: at the end of the partitioning phase of the ubuntu install process, there is an 'advanced' button. hit it, and specify where to install grub (ie: on the passport). none of the below will be necessary in the future if you do this.

1. now: priority is making your system not depend on the passport, right? you will need a windows system recovery cd for your version of windows.

ive never used it, so i can't give specific instructions... google for terms like 'windows xp recovery cd' and 'windows xp bootloader restore'. you want to replace grub on your "C Drive" with the windows bootloader.

edit: this ***looks*** like the solution
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)

2. (one solution) next, you will want to install grub onto the passport.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

you will want to "Overwrite the Master Boot Record" on the ***passport***, not on the hard drive in your computer.

2. (alternative solution) reinstall ubuntu from scratch onto the passport, but keep step 0 in mind above.

3. then you will want to set your computer's bios to give USB a higher boot priority than the internal hard drive. thats the 'press [whatever] to enter setup' thing you see when you first turn the computer on. same process you probably used to tell the computer to boot from the Ubuntu LiveCD, except now we are going to tell it to boot from USB (if present and bootable). need help with that, or can you manage? 

end result of all this:
-no boot menu when you turn the computer on.
-if the passport is plugged in, ubuntu will start.
-if the passport is not plugged in, windows will start.

---

### Post by oldfred on 2010-04-04
fixboot repairs the partition boot files (PBR) that windows has, but you also need to run the fixmbr to reinstall the windows boot loader to the MBR of sda.

From linux or a liveCD (with universe turn turned on):
Restore basic windows boot loader (does not install lilo, just uses it)
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

edit:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jerry950 on 2010-04-05
Thank you for the info. But I do not have a floppy drive nor do I have a bootable
XP cd. I am looking now for something I can make that will boot from CD.
I am downloading CDBurnerXP to make a bootable XP CD.
 
I hope someone fixes the default behavior of UBuntu to not modify the bios on the
PC unless it is where Ubuntu is going to be installed. My friend got nailed by the
same problem when installing on external drive. He could not boot his pc either.
He fixed his pc and went with Redhat.
 
And, as I understand from other posts. I am to run:
 
fdisk /mbr

---

### Post by presence1960 on 2010-04-05
> **jerry950 said:**
> Thank you for the info. But I do not have a floppy drive nor do I have a bootable
XP cd. I am looking now for something I can make that will boot from CD.
I am downloading CDBurnerXP to make a bootable XP CD.
 
I hope someone fixes the default behavior of UBuntu to not modify the bios on the
PC unless it is where Ubuntu is going to be installed. My friend got nailed by the
same problem when installing on external drive. He could not boot his pc either.
He fixed his pc and went with Redhat.
 
And, as I understand from other posts. I am to run:
 
fdisk /mbr

Boot into Ubuntu and do this:

Open a terminal and run ```
sudo apt-get install lilo
```Ignore the warning.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```Your lappie will now boot to windows when you start it.

next you need to install GRUB to MBR of the external disk. Then go into BIOS and set the external to boot before the internal disk. Then once that is done when you boot without the external connected windows will boot. When you boot with the external connected you will get GRUB and boot to Ubuntu.

If you don't know how to reinstall GRUB post back

---

### Post by jerry950 on 2010-04-05
I ran your commands and that fixed auto booting into windows. Now I booted with the
9.10 CD and tried running this from an artical I found about re-installing GRUB. It did
not work, so yes, I need help. This is my first time doing anything like this. :


mount | tail -1

/dev/sdb5 on /media/d39fe376-85e3-4b72-a12c-022e00d8acbc type ext4 (rw,nosuid,nodev,uhelper=devkit)

-----------------------------

ls /media/d39fe376-85e3-4b72-a12c-022e00d8acbc/boot

abi-2.6.31-14-generic     initrd.img-2.6.31-14-generic
boot.0800                 memtest86+.bin
coffee.bmp                sarge.bmp
config-2.6.31-14-generic  sid.bmp
debian.bmp                System.map-2.6.31-14-generic
debianlilo.bmp            vmcoreinfo-2.6.31-14-generic
grub                      vmlinuz-2.6.31-14-generic


--------------------------------

sudo grub-install --root-directory=/media/d39fe376-85e3-4b72-a12c-022e00d8acbc /dev/sdb5

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

---

### Post by presence1960 on 2010-04-05
I need more info about your setup so I can give you the exact commands to run to put GRUB on MBR of the external. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by jerry950 on 2010-04-08
```
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa786d6ae
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    40,960,079    40,960,017   7 HPFS/NTFS
/dev/sda2          40,960,080   117,195,119    76,235,040   f W95 Ext d (LBA)
/dev/sda5          40,960,143   117,195,119    76,234,977   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders, total 623769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00035f28
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048   312,416,054   312,414,007   7 HPFS/NTFS
/dev/sdb2         312,416,055   623,755,754   311,339,700   5 Extended
/dev/sdb5         312,416,118   617,795,639   305,379,522  83 Linux
/dev/sdb6         617,795,703   623,755,754     5,960,052  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        0AF8984FF8983AC1                       ntfs       System                        
/dev/sda5        62489A124899E557                       ntfs       DATA                          
/dev/sdb1        5EF6D5D1F6D5A993                       ntfs       My Passport                   
/dev/sdb5        d39fe376-85e3-4b72-a12c-022e00d8acbc   ext4                                     
/dev/sdb6        9a5d6195-7302-4499-a5bb-d79943b039f0   swap                                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/My Passport       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sdb5/boot/grub/grub.cfg: ===========================
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
set root=(hd1,5)
search --no-floppy --fs-uuid --set d39fe376-85e3-4b72-a12c-022e00d8acbc
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd1,5)
 search --no-floppy --fs-uuid --set d39fe376-85e3-4b72-a12c-022e00d8acbc
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d39fe376-85e3-4b72-a12c-022e00d8acbc ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd1,5)
 search --no-floppy --fs-uuid --set d39fe376-85e3-4b72-a12c-022e00d8acbc
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d39fe376-85e3-4b72-a12c-022e00d8acbc ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 0af8984ff8983ac1
 drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=d39fe376-85e3-4b72-a12c-022e00d8acbc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=9a5d6195-7302-4499-a5bb-d79943b039f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb5: Location of files loaded by Grub: ===================

 160.1GB: boot/grub/core.img
 167.2GB: boot/grub/grub.cfg
 160.1GB: boot/initrd.img-2.6.31-14-generic
 160.1GB: boot/vmlinuz-2.6.31-14-generic
 160.1GB: initrd.img
 160.1GB: vmlinuz


```

---

### Post by oldfred on 2010-04-08
Your install is on sdb5:

If partition known
reinstall from live cd

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Some BIOS want a boot flag on a primary partition even though Ubuntu does not need it. You can use the liveCD, gparted, right click on sdb1 and manage flags to add a boot flag.

more info:
Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by presence1960 on 2010-04-08
> **oldfred said:**
> your install is on sdb5:

If partition known
reinstall from live cd

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

some bios want a boot flag on a primary partition even though ubuntu does not need it. You can use the livecd, gparted, right click on sdb1 and manage flags to add a boot flag.

More info:
Short version
[https://help.ubuntu.com/community/grub2#reinstalling%20grub%202]("https://help.ubuntu.com/community/grub2#reinstalling%20grub%202")
full chroot version:
[https://wiki.ubuntu.com/grub2#recover%20grub%202%20via%20livecd](https://wiki.ubuntu.com/grub2#recover%20grub%202%20via%20livecd)

+1

---

### Post by jerry950 on 2010-04-09
All is well. I can now hit F12 on bootup and select Ubuntu boot or just let it boot with
Windows which is the default. I can also disconnect the Passport without the PC 
crashing on bootup.
 
I would like to thank all of you for your input in helping me fix this problem.
I was a little scared there for a moment that I was going to lose my Windows drive.
 
Thanks again,
 
Jerry

---

### Post by presence1960 on 2010-04-09
> **jerry950 said:**
> All is well. I can now hit F12 on bootup and select Ubuntu boot or just let it boot with
Windows which is the default. I can also disconnect the Passport without the PC 
crashing on bootup.
 
I would like to thank all of you for your input in helping me fix this problem.
I was a little scared there for a moment that I was going to lose my Windows drive.
 
Thanks again,
 
Jerry

Glad you got it working, enjoy your dual boot with Ubuntu!

---

### Post by zengzhangsong on 2010-04-09
Maybe you should do this,"sudo gedit /boot/grub/man.lst"

---

### Post by oldfred on 2010-04-09
zengzhangsong

Since 9.10, instructions on repairing grub have to be reviewed to see if the OP has grub legacy (0.97) or grub2 (1.97 beta4 in 9.10) as the way to fix thing is totally different.

And if you are using graphical tools you should use gksudo and use sudo for command line tools. Your command if for grub legacy editing of menu.lst is:
gksudo gedit /boot/grub/menu.lst

and because I make a lot of typos I like to test my commands before posting where possible to make sure they are correct.

---

