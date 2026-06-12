---
title: "GRUB rescue:  unknown filesystem"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by moonsnow on 2010-12-28
Hello everyone,

I am a newbie have recently decided to install Ubuntu 10.04 on my laptop.  I installed it on a new empty 640 GB external hard drive and let Ubuntu set up a 160 GB filesystem on it so my Windows installation would remain safe no matter what.  During installation, it was listed as "sdb" and the boot loader was also installed on it.  The installation went fine.  However, when I tried to boot Ubuntu, the screen was black and said "unknown filesystem" followed by the GRUB rescue prompt on the following line.  I have tried to do this several times in the past and each time I run into this same problem.  I have looked around on this forum, and have tried several suggested solutions, but they do not fix my problem, such as running the following commands in the terminal:

```

sudo fdisk -l 
sudo mount -t ext4 /dev/sdb1/ /dev/sdb 
sudo grub-install --root-directory=/mnt/ /dev/sdb
```That did not fix my problem.  I also noticed that there can be problems with booting from certain distances from the front or the end of a drive and the Boot Info Script seems to be very beneficial to solving boot problems so here are the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    17,299,455    17,297,408  27 Hidden HPFS/NTFS
/dev/sda2    *     17,299,456   488,395,119   471,095,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         937,428,992 1,250,263,039   312,834,048  83 Linux
/dev/sdb2    *         16,126   937,428,991   937,412,866   5 Extended
/dev/sdb5              16,128   924,108,408   924,092,281   7 HPFS/NTFS
/dev/sdb6         924,108,800   937,428,991    13,320,192  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6A02839A02836A41                       ntfs       Recovery                      
/dev/sda2        AC1C474E1C4712AE                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        19fd2248-be65-4a33-9c84-29aadf0f380b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        2BBE654529E33D97                       ntfs       FreeAgent Drive               
/dev/sdb6        3bda01b2-9e55-4d7f-8314-fa5a648affee   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/19fd2248-be65-4a33-9c84-29aadf0f380b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=19fd2248-be65-4a33-9c84-29aadf0f380b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=19fd2248-be65-4a33-9c84-29aadf0f380b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19fd2248-be65-4a33-9c84-29aadf0f380b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6a02839a02836a41
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set ac1c474e1c4712ae
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=19fd2248-be65-4a33-9c84-29aadf0f380b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=3bda01b2-9e55-4d7f-8314-fa5a648affee none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 512.4GB: boot/grub/core.img
 523.0GB: boot/grub/grub.cfg
 512.4GB: boot/initrd.img-2.6.32-24-generic
 512.4GB: boot/vmlinuz-2.6.32-24-generic
 512.4GB: initrd.img
 512.4GB: vmlinuz

```So far, all my knowledge on Linux has mostly come from books, and I have not read one that addressed this problem.  Let me know if more information is needed.

Sincerely,
moonsnow

---

### Post by oldfred on 2010-12-28
Welcome the the forums.

If this an older system? I do not see anything wrong with boot script. grub is in the MBR of sdb and it is trying to boot from sdb1. Older systems have a 137GB limit on location of the boot partition on the system. Your install also found the windows installs and added them to your grub boot menu.

If you in BIOS select the internal drive 250GB does windows boot ok? It looks like it should. 

You have already run my first suggestion which is to just reinstall grub with the two line mount and reinstall. Sometimes that does not work and the full chroot into your system from a liveCD does. You just would not have to uninstall grub legacy but should uninstall grub2 (grub-pc) and reinstall.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You should read drs305 instructions. I have  taken the notes on each line out, so you can copy & paste these lines. Besure to reinstall grub to sdb when given the option.

```
sudo mkdir /mnt/temp 
sudo mount /dev/sdb1 /mnt/temp  

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  
sudo chroot /mnt/temp

apt-get update
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub 
exit

for i in /dev/pts /dev /proc /sys /boot / ; do sudo umount /mnt/temp$i ; done


```I often suggest while in chroot to run all the other updates. But that is optional as booting is the real requirement and once you boot then you can run the updates. No sudo required in chroot enviroment.

apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade

---

### Post by moonsnow on 2010-12-28
First of all, the computer system  isn't old, nor is the external hard drive I'm trying to install on.  Windows also boots all right every single time; I've checked and it's booting from the Windows Boot Manager.  Next, I've done chroot & grub unistall/reinstall. Then, I rebooted and the problem still exists.  I'm not sure if something is wrong, but some lines in the terminal caught my eye while uninstalling/reinstalling grub, so the all the output is posted below:
```

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
mkdir: cannot create directory `/mnt/temp': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/temp 
mount: /dev/sdb1 already mounted or /mnt/temp busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf 
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release [38.5kB]
Get:3 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com lucid Release [57.2kB]
Get:6 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]      
Get:7 http://security.ubuntu.com lucid-security/main Packages [114kB]         
Get:8 http://us.archive.ubuntu.com lucid/main Packages [1,386kB]
Get:9 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:10 http://security.ubuntu.com lucid-security/main Sources [38.2kB]        
Get:11 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:12 http://security.ubuntu.com lucid-security/universe Packages [53.4kB]   
Get:13 http://security.ubuntu.com lucid-security/universe Sources [15.3kB]
Get:14 http://security.ubuntu.com lucid-security/multiverse Packages [2,003B]  
Get:15 http://security.ubuntu.com lucid-security/multiverse Sources [660B]     
Get:16 http://us.archive.ubuntu.com lucid/restricted Packages [6,208B]         
Get:17 http://us.archive.ubuntu.com lucid/main Sources [659kB]                 
Get:18 http://us.archive.ubuntu.com lucid/restricted Sources [3,775B]          
Get:19 http://us.archive.ubuntu.com lucid/universe Packages [5,448kB]          
Get:20 http://us.archive.ubuntu.com lucid/universe Sources [3,165kB]           
Get:21 http://us.archive.ubuntu.com lucid/multiverse Packages [180kB]          
Get:22 http://us.archive.ubuntu.com lucid/multiverse Sources [119kB]           
Get:23 http://us.archive.ubuntu.com lucid-updates/main Packages [375kB]        
Get:24 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B] 
Get:25 http://us.archive.ubuntu.com lucid-updates/main Sources [141kB]         
Get:26 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:27 http://us.archive.ubuntu.com lucid-updates/universe Packages [158kB]    
Get:28 http://us.archive.ubuntu.com lucid-updates/universe Sources [61.4kB]    
Get:29 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [7,366B] 
Get:30 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [3,677B]  
Fetched 12.1MB in 1min 47s (112kB/s)                                           
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 181 not upgraded.
After this operation, 6,603kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122909 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 181 not upgraded.
Need to get 2,148kB of archives.
After this operation, 6,603kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-common 1.98-1ubuntu9 [1,510kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-pc 1.98-1ubuntu9 [638kB]
Fetched 2,148kB in 17s (120kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 122634 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu9_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu9_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98-1ubuntu9) ...

Setting up grub-pc (1.98-1ubuntu9) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
ls: cannot access /media/FreeAgent Drive: No such file or directory
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot / ; do sudo umount /mnt/temp$i ; done
umount: /mnt/temp/boot: not mounted

```

Previously, I had already mounted, but I wasn't expecting commands to be run right after I pasted them, so I exited and tried to redo the commands.  The lines that concerned me were the parts about "ls: cannot access /media/FreeAgent Drive: No such file or directory" after memtest. Should I try the Grub Rescue Prompt Megathread now?  Thanks for helping.

---

### Post by oldfred on 2010-12-28
I thought with the larger drives it was newer, but old systems cannot boot from partitions beyond 137GB. 

It says it cannot parse your sdb5 NTFS drive.

```
/dev/sdb5        2BBE654529E33D97                       ntfs       FreeAgent Drive
```

From windows I would see if it sees you sdb5, of course it will call it D: or E: and see if you can run chkdsk on that partition.

Rerun chkdsk until there are no errors as it does not fix all of them on each pass.
Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by moonsnow on 2010-12-29
I have run CHKDSK with the /f and /r options on the partition and it seems that there are no problems with it.

```

CHKDSK is verifying files (stage 1 of 5)...
  3008 file records processed.
File verification completed.
  0 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 5)...
  3178 index entries processed.
Index verification completed.
  0 unindexed files processed.
CHKDSK is verifying security descriptors (stage 3 of 5)...
  3008 security descriptors processed.
Security descriptor verification completed.
  85 data files processed.
CHKDSK is verifying file data (stage 4 of 5)...
  2992 files processed.
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
  114021328 free clusters processed.
Free space verification is complete.
Windows has checked the file system and found no problems.

 462046136 KB total disk space.
   5876604 KB in 2864 files.
      1160 KB in 87 indexes.
         0 KB in bad sectors.
     83056 KB in use by the system.
     65536 KB occupied by the log file.
 456085316 KB available on disk.

      4096 bytes in each allocation unit.
 115511534 total allocation units on disk.
 114021329 allocation units available on disk.

```

---

### Post by oldfred on 2010-12-30
It just may be the space??

FreeAgent Drive

Linux does not like spaces. I would use gparted and right click on the partition and change the label to:

FreeAgentDrive

---

