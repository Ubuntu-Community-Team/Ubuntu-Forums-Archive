---
title: "GRUB Problem after 10.04 LTS upgrade to latest kernel"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by cspaltro on 2010-11-27
I've read through similar posts and solutions posted by bcbc, they look quite simple.  However, I am having a very similar problem but I do not have a Wubi install.  I'm running a dual boot system with WinXP on sda1 and Ubuntu 10.04LTS (kernel 2.6.32-26-generic) on sda5.  After running the upgrade my grub is jacked.  My system will not boot into either system and just gives me the grub-rescue> prompt.  When I boot into the Ubuntu Live CD the system acts like /dev is not mounted but it clearly is because I can browse it using the "Places" window.
 
I noticed something odd when I ran *grub-rescue>ls*
*(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1)*
 
In the past my drives were represented by hd0,5.  I'm confused as to where this msdos5 came from and I can't find any posts about it.
 
My grub error reads
*error: symbol not found: 'grub_putchar'.*
 
I assume that my grub.cfg file is incorrect or one of the templates responsible for generating the cfg file.  I try to re-install GRUB 2 but I can't access sda5 because the system thinks that I'm not mounted to it or it can't find it.
 
I'm a beginner but capable of interpreting the technical instructions... can anyone identify my problem or help me fix this.  I'm also curious as to why this happens every time I upgrade my kernel... I've been through this before but can't seem to find the applicable code to fix what is wrong in the forum.
 
Thank you

---

### Post by carl4926 on 2010-11-27
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by sikander3786 on 2010-11-27
If you can't figure it out from the link posted above, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your boot setup and we'll be able to advise more efficiently.

Please wrap the output using proper code # tags from the post menu. [/code] at the end and [code] at the beginning.

Thanks.

---

### Post by drs305 on 2010-11-27
> **cspaltro said:**
> I noticed something odd when I ran *grub-rescue>ls*
*(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1)*
 
In the past my drives were represented by hd0,5.  I'm confused as to where this msdos5 came from and I can't find any posts about it.


This is the new way Grub2 identifies partitions using the MS-DOS partition table. It's normal with recent versions of Grub2.

My guess is you are going to have to reinstall Grub2 by 'chrooting' into your Ubuntu partition from the LiveCD. We can wait for your RESULTS.txt, but the link I'd provide for the chroot procedure is in my signature line: G2-Chroot.

---

### Post by garvinrick4 on 2010-11-27
Put in a live Cd (install cd and choose try ubuntu) get internet working and open a terminal and copy and paste these commands. They just get you into root (chroot) of sda5 with internet and fix dependencies, install grub in sda looking in sda5 for grub files, update and upgrade and then unmount sda5. Without internet connection you can install grub and update-grub just cannot update and upgrade:

```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt 
``````
grub-install --recheck --root-directory=/media/mnt /dev/sda
``````
dpkg --configure -a
``````
update-grub
``````
apt-get update && apt-get upgrade
``````
exit
```                       ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```Now shutdown and restart and boot into Ubuntu and:
```
sudo update-grub
```

---

### Post by cspaltro on 2010-11-27
garvinrick4... trying your instructions and ran into a problem.
 
I booted to a live CD, achieved internet connectivity, and opened a terminal windo.  I successfully executed the first line of code.  However the second line
 
```
 
grub-install --recheck --root-directory=/media/mnt /dev/sda

```
 
resulted in the following response:
 
```
 
mkdir: cannot create directory '/media/mnt/boot': No such file or directory

```
 
I double checked my entry and it is exactly as you posted.
 
This is getting very frustrating.  Thank you everyone for your help... any ideas now?

---

### Post by sikander3786 on 2010-11-27
> **cspaltro said:**
> garvinrick4... trying your instructions and ran into a problem.
 
I booted to a live CD, achieved internet connectivity, and opened a terminal windo.  I successfully executed the first line of code.  However the second line
 
```
 
grub-install --recheck --root-directory=/media/mnt /dev/sda

```
 
resulted in the following response:
 
```
 
mkdir: cannot create directory '/media/mnt/boot': No such file or directory

```
 
I double checked my entry and it is exactly as you posted.
 
This is getting very frustrating.  Thank you everyone for your help... any ideas now?
Insteading of guessing your setup, I would still like to see the output of bootinfoscript as mentioned above.

Or if you don't want to post that, try this great tutorial here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by cspaltro on 2010-11-27
I'll grab it... just a few minutes... working on two computers here since my problem computer won't boot into anything.

---

### Post by cspaltro on 2010-11-27
Here are the results of my boot_info_script
 
[HTML] 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 41885285 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   117,210,239    76,244,490   5 Extended
/dev/sda5          40,965,813   112,262,219    71,296,407  83 Linux
/dev/sda6         112,262,283   117,210,239     4,947,957  82 Linux swap / Solaris

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 8019 MB, 8019509248 bytes
102 heads, 38 sectors/track, 4041 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *          2,192    15,663,103    15,660,912   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        3C743B27743AE376                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ea114f50-e47c-4ef0-841e-bfddc26d7925   ext4                                     
/dev/sda6        851b4f52-7ae2-477f-ab1b-427e5e9ede23   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9CCE-F377                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)
/dev/pts         /mnt/dev/pts             none       (rw,bind)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda5/boot/grub/grub.cfg: ===========================
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux /boot/vmlinuz-2.6.32-26-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 echo 'Loading Linux 2.6.32-26-generic ...'
 linux /boot/vmlinuz-2.6.32-26-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux /boot/vmlinuz-2.6.32-24-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 echo 'Loading Linux 2.6.32-24-generic ...'
 linux /boot/vmlinuz-2.6.32-24-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux /boot/vmlinuz-2.6.32-22-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 echo 'Loading Linux 2.6.32-22-generic ...'
 linux /boot/vmlinuz-2.6.32-22-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro   quiet splash
 initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 echo 'Loading Linux 2.6.31-21-generic ...'
 linux /boot/vmlinuz-2.6.31-21-generic root=UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set ea114f50-e47c-4ef0-841e-bfddc26d7925
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set 3c743b27743ae376
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ea114f50-e47c-4ef0-841e-bfddc26d7925 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=851b4f52-7ae2-477f-ab1b-427e5e9ede23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================

  21.2GB: boot/grub/core.img
  22.0GB: boot/grub/grub.cfg
  28.6GB: boot/initrd.img-2.6.31-21-generic
  30.7GB: boot/initrd.img-2.6.32-22-generic
  31.6GB: boot/initrd.img-2.6.32-24-generic
  32.9GB: boot/initrd.img-2.6.32-26-generic
  27.2GB: boot/vmlinuz-2.6.31-21-generic
  30.6GB: boot/vmlinuz-2.6.32-22-generic
  31.3GB: boot/vmlinuz-2.6.32-24-generic
  29.5GB: boot/vmlinuz-2.6.32-26-generic
  21.4GB: grub/core.img
  32.9GB: initrd.img
  31.6GB: initrd.img.old
  29.5GB: vmlinuz
  31.3GB: vmlinuz.old

[/HTML]

---

### Post by sikander3786 on 2010-11-27
The problems seems to lie here.

```
sda5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  [B]Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 41885285 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.[/B]
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

```

Taking the chroot and purging and re-installing Grub would definitely fix the problem. And that is well explained in the thread I linked above. [COLOR="Red"]**drs305's**[/COLOR] signature > [G2-Chroot]("http://ubuntuforums.org/showthread.php?t=1581099").

---

### Post by garvinrick4 on 2010-11-27
#I agree has grub/core.img in sda5. Should not be there.
Should have let sikander and drs305 see bootscript first.
#Seems like grub2 was installed in sda5 instead of sda previously
and does need to be purged from there and reinstalled in sda
#Needed a grub purge && install command in my code before the grub installed in sda
Would have known that if looked at bootscript first. I errored by not
looking at it first.
# I apoligize cspaltro should be no problem repairing your Grub:

#sda5: location of files loaded by Grub
  21.2GB: boot/grub/core.img
  22.0GB: boot/grub/grub.cfg
  28.6GB: boot/initrd.img-2.6.31-21-generic
  30.7GB: boot/initrd.img-2.6.32-22-generic
  31.6GB: boot/initrd.img-2.6.32-24-generic
  32.9GB: boot/initrd.img-2.6.32-26-generic
  27.2GB: boot/vmlinuz-2.6.31-21-generic
  30.6GB: boot/vmlinuz-2.6.32-22-generic
  31.3GB: boot/vmlinuz-2.6.32-24-generic
  29.5GB: boot/vmlinuz-2.6.32-26-generic
 [COLOR=Red] 21.4GB: grub/core.img[/COLOR]
  32.9GB: initrd.img
  31.6GB: initrd.img.old
  29.5GB: vmlinuz
  31.3GB: vmlinuz.old

---

### Post by cspaltro on 2010-11-27
That worked.  I figured that I had to reinstall GRUB 2 but couldn't figure out how to get it installed on my "real" Ubuntu installation while booted into the LiveCD.  Thank you very much for your help!
 
I am curious though... why does this happen every time I do a kernel upgrade?  Do I have my GRUB 2 files installed in the wrong place or am I applying the updates incorrectly?  I use the update manager in Ubuntu to automatically download and install updates and upgrades.

---

### Post by oldfred on 2010-11-27
I did not think grub2 remembered where to install. Did you by any chance install to sda5 on the original install?

enter thru the first couple of screens:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive - sda, sdb etc, enter to accept, do not choose partitions like sda5, sdb1 etc.

---

### Post by cspaltro on 2010-11-27
> **oldfred said:**
> I did not think grub2 remembered where to install. Did you by any chance install to sda5 on the original install?
 
enter thru the first couple of screens:
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive - sda, sdb etc, enter to accept, do not choose partitions like sda5, sdb1 etc.
 
I may have installed to sda5, I don't remember.  I know for a fact that I installed to sda this time.  I guess I'll have to wait and see what happens on my next update.

---

### Post by lalop on 2011-06-07
Sorry for the bump, but could someone advise me on what is essentially the exact same problem?  (Downgrading to 10.04 from natty.)  My own boot_info_script gives: ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda7 and looks at sector 192545282 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 7 for /grub.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..........V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 520 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,443,199    27,441,152  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,443,200   178,184,855   150,741,656   7 NTFS / exFAT / HPFS
/dev/sda3         178,193,104   625,141,759   446,948,656   5 Extended
/dev/sda5         566,548,480   625,141,759    58,593,280  83 Linux
/dev/sda6         178,193,106   192,522,959    14,329,854  82 Linux swap / Solaris
/dev/sda7         192,524,288   192,815,103       290,816  83 Linux
/dev/sda8         530,708,480   566,548,479    35,840,000  83 Linux
/dev/sda9         192,817,152   530,706,431   337,889,280  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders, total 3963904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,963,903     3,963,872   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       0d449045-bdbd-43da-ba19-e9076e0d1b85   ext3       
/dev/sda1        02104AE8104AE1F1                       ntfs       Recovery
/dev/sda2        BC8EE3B28EE3637E                       ntfs       
/dev/sda5        6dd391ab-6c42-4a66-965a-a3cb9bd48083   ext4       
/dev/sda6                                               swap       
/dev/sda7        31ae9413-fe3c-441b-a38c-3ac50a22cc78   ext4       
/dev/sda8        5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e   ext4       
/dev/sda9        916ca90f-d80a-46a3-9399-c8e2261ce4f6   ext4       
/dev/sdb1        C2F8-E4F2                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda7/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro   quiet splash
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    linux    /vmlinuz-2.6.35-28-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro   quiet splash
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /vmlinuz-2.6.35-28-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    linux    /vmlinuz-2.6.32-28-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro   quiet splash
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /vmlinuz-2.6.32-28-generic root=UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 31ae9413-fe3c-441b-a38c-3ac50a22cc78
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 02104ae8104ae1f1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set bc8ee3b28ee3637e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  91.812768936 = 98.583209984   grub/core.img                                  1
  91.814949989 = 98.585551872   grub/grub.cfg                                  1
  91.888618469 = 98.664652800   initrd.img-2.6.32-28-generic                   1
  91.934593201 = 98.714017792   initrd.img-2.6.35-28-generic                   2
  91.855981827 = 98.629609472   initrd.img-2.6.38-8-generic                    1
  91.861443520 = 98.635473920   vmlinuz-2.6.32-28-generic                      1
  91.939592361 = 98.719385600   vmlinuz-2.6.35-28-generic                      1
  91.830386162 = 98.602126336   vmlinuz-2.6.38-8-generic                       2

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=5fd16bf7-ba8c-4831-9b14-e79e99d7ea1e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=31ae9413-fe3c-441b-a38c-3ac50a22cc78 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=6dd391ab-6c42-4a66-965a-a3cb9bd48083 /home           ext4    defaults        0       2
# /random was on /dev/sda9 during installation
UUID=916ca90f-d80a-46a3-9399-c8e2261ce4f6 /random         ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  e2 ab 4d b3 03 1e 67 90  14 e1 c4 01 6c e7 09 6f  |..M...g.....l..o|
00000010  02 d8 57 ef 2d f8 79 f3  78 ce 99 f6 5f 92 41 bd  |..W.-.y.x..._.A.|
00000020  5d 9e 22 9a de 7b f3 32  4f 2f 2e 5b c9 bb fd f4  |]."..{.2O/.[....|
00000030  f2 ad 17 df 9c e4 08 c9  6a 3c 65 71 90 20 fc 54  |........j<eq. .T|
00000040  7b 53 cb 30 54 22 82 98  f8 de 88 12 81 2a 20 8d  |{S.0T".......* .|
00000050  59 77 24 df d4 8d 5e b6  c9 d0 23 26 cf ba 02 6a  |Yw$...^...#&...j|
00000060  e7 3e 8d f8 d0 3b 19 c8  67 bf 15 3e 9f d7 48 d3  |.>...;..g..>..H.|
00000070  db 01 7e 25 47 b0 02 bd  5c c4 5a f3 4b 50 72 48  |..~%G...\.Z.KPrH|
00000080  42 e2 b2 cf d1 93 e8 da  6c 15 e1 30 3a 27 1f df  |B.......l..0:'..|
00000090  e8 62 76 7f 9b 94 ce 64  80 44 ca 67 0b ad f5 fc  |.bv....d.D.g....|
000000a0  58 a3 78 a1 27 fa 3d 7b  b9 ce fa de 47 46 cc b7  |X.x.'.={....GF..|
000000b0  4c 65 41 29 36 b8 a5 ae  90 50 9f ff 92 67 11 1a  |LeA)6....P...g..|
000000c0  73 cc f2 4f 35 0c af f7  57 64 1c 40 70 4e 99 99  |s..O5...Wd.@pN..|
000000d0  e5 f9 87 77 8b 65 a3 93  06 bd dd a1 ae 44 6c ee  |...w.e.......Dl.|
000000e0  76 7f 5e 0e c4 d2 e8 d9  d4 31 84 95 e6 41 ed 9d  |v.^......1...A..|
000000f0  5b 3d ab c9 d8 3e 8e c9  97 b6 25 f6 c4 b4 b7 55  |[=...>....%....U|
00000100  4d 3f b3 bc ed c8 68 7f  2f 78 03 e6 4e c6 cc 17  |M?....h./x..N...|
00000110  df f5 9d 3c 3f 06 a0 77  55 dd 98 0e 29 4c a2 f0  |...<?..wU...)L..|
00000120  48 44 eb ff 25 57 cb 33  33 a3 d2 ed 29 00 48 c8  |HD..%W.33...).H.|
00000130  61 dc e9 18 57 8b 8b 24  ee 04 ed 3e 22 c6 d1 63  |a...W..$...>"..c|
00000140  4d 05 a4 57 9a 76 b3 6b  df 07 fd d6 a4 bd cc ae  |M..W.v.k........|
00000150  f8 25 54 83 14 08 1e 03  01 5f 49 4f 90 00 dd c1  |.%T......_IO....|
00000160  94 5e 7a 09 78 f4 07 ac  69 cc e7 07 24 0e ae 99  |.^z.x...i...$...|
00000170  f7 60 8d 06 86 16 24 14  2c 5c ca d7 f6 ff 93 ba  |.`....$.,\......|
00000180  6b 73 df 28 48 7c ff 5d  f8 a5 da 7f 6d 2c 04 81  |ks.(H|.]....m,..|
00000190  f1 0a 65 e0 a4 14 b8 7e  61 c9 30 5b e7 fc e9 ce  |..e....~a.0[....|
000001a0  ef 37 5d a6 2c ca 7d e5  77 2a 41 7c 9b 65 18 68  |.7].,.}.w*A|.e.h|
000001b0  53 df cb c7 8f 1c ba f8  c6 08 c9 0f 30 dc 00 fe  |S...........0...|
000001c0  ff ff 83 fe ff ff 30 d5  25 17 00 10 7e 03 00 fe  |......0.%...~...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 ff a7 da 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```As a (probably) related question, I made a /boot directory about 2 installations ago: it is sda7 above.  I can't remember what I did that installation, but the next time, when I installing natty, I installed grub into sda, but it came up with a similar boot error and I recall I had to chroot into sda7 [if this makes no sense, then I'm remembering wrong and it was sda8, the / directory] to fix it.  This is why, this time, I told the installer to install grub into sda7 (and probably also why there are two grubs in the above code).  Was this a mistake, and what should I have done?

---

### Post by drs305 on 2011-06-07
lalop,

Do you want a separate /boot partition now (sda7) or not? And just confirm you want Lucid and not Natty, and that Lucid installed completely (other than the bootloader)? Depending on your answers we can help you sort things out.

---

### Post by lalop on 2011-06-13
> **drs305 said:**
> lalop,

Do you want a separate /boot partition now (sda7) or not? And just confirm you want Lucid and not Natty, and that Lucid installed completely (other than the bootloader)? Depending on your answers we can help you sort things out.

Sorry for the lateness of my reply; I've been working out the dare and have since fixed the issue by following the [instructions linked in this thread](http://ubuntuforums.org/showthread.php?t=1581099) for chrooting into sda and installing the bootloader there.

In general, though, I would still like to know where I should be installing the bootloader in future versions.  (To answer, I did downgrade to lucid due to screen tearing in videos, and I do still want the /boot partition sda7.)

Thanks a lot!

---

### Post by drs305 on 2011-06-13
> **lalop said:**
> In general, though, I would still like to know where I should be installing the bootloader in future versions.  (To answer, I did downgrade to lucid due to screen tearing in videos, and I do still want the /boot partition sda7.)

Thanks a lot!

For future installations, if you want a /boot partition:
If you do an online upgrade, your current /boot partition will be mounted and everything should be done automatically. Any new Grub files should be placed in the correct location (whatever the partition is mounted as /boot).

If you do an installation from a CD, when you get to the partitioning screen you should designate the /boot partition (the same screen where you would designate / and /home). At the end of the installation if it asks where you want Grub installed you should designation the *drive* the installation is on. Don't specify a partition - the installer will know where the Grub files are located and really just wants to know if it should write to the drive MBR or to a partition's boot record.

---

