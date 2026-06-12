---
title: "Grub rescue / Please Help Me !!"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Shoala on 2010-09-21
[SIZE=2] Hello Guys ,

I have a laptop running Windows 7 and Ubuntu 10.04

Everything was working fine until I tried to upgrade Ubuntu 10.04.[/SIZE] [SIZE=2]

I did the upgrade from the updater inside Ubuntu, and after completing  the upgrade I cannot boot in to either Windows 7 or Ubuntu.[/SIZE] [SIZE=2]

As soon as I reboot my computer, I get a[/SIZE] [SIZE=2]
[B][COLOR=Red]"grub rescue" 
[/COLOR][/B]
This happened immediately after completing the upgrade.  [/SIZE] [SIZE=2]

Can someone please point me in the direction in order to get my computer  to be able to boot up again?  I have copies of both 7 and 10.04 Live  CD.[/SIZE] [SIZE=2]

Windows 7 was installed first, and Ubuntu 2nd.. but I dont know enough  about mounting and such to know which partition contains windows and  which has ubuntu.  hd0 vs hd1?[/SIZE] [SIZE=2]

Right now I boot from ubuntu 10.04 live CD and I have no clue what else to do .
please tell me step by step what I need to do becuse Im not pro .

[/SIZE][SIZE=2] Any help would be appreciated.[/SIZE]   [SIZE=2]

Thanks[/SIZE]

---

### Post by wilee-nilee on 2010-09-21
Is this a install from within windows=wubi?

---

### Post by Shoala on 2010-09-21
> **wilee-nilee said:**
> Is this a install from within windows=wubi?

First thank you for helping me 
Yes I had my 7 and I installed ubuntu inside the windows , everything was fine untill I updade ubuntu .

---

### Post by wilee-nilee on 2010-09-21
> **Shoala said:**
> First thank you for helping me 
Yes I had my 7 and I installed ubuntu inside the windows , everything was fine untill I updade ubuntu .

This is important information thanks.;) So there are a few members on line at times who are familiar with this problem in it's various forms. If you want to get help you will have to for them to stop by. If this was a regular install I might be more of help. Wubi is good I just haven't spent time in this exact area.

I think it will help the people who do know though if you post the bootscript in my signature. When you post the text in the reply click on the # and put the text in between the code tags. This will give them a good outline to work with.

---

### Post by Shoala on 2010-09-21
> **wilee-nilee said:**
> This is important information thanks.;) So there are a few members on line at times who are familiar with this problem in it's various forms. If you want to get help you will have to for them to stop by. If this was a regular install I might be more of help. Wubi is good I just haven't spent time in this exact area.

I think it will help the people who do know though if you post the bootscript in my signature. When you post the text in the reply click on the # and put the text in between the code tags. This will give them a good outline to work with.

I will do what you said if you just tell me how I can get the info you need ( where should I go to get bootscript info ? ).

Sorry Im ****ing noob :(

---

### Post by Rubi1200 on 2010-09-21
The link is at the bottom of wilee-nilee's post in the signature.

Follow the instructions and post back here.

---

### Post by Shoala on 2010-09-21
> **Rubi1200 said:**
> The link is at the bottom of wilee-nilee's post in the signature.

Follow the instructions and post back here.

How on earth I couldn't see that :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    24,579,449    24,579,387   7 HPFS/NTFS
/dev/sda2          24,579,450   106,510,949    81,931,500   7 HPFS/NTFS
/dev/sda3         106,510,950   488,392,064   381,881,115   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3ce30695-cf97-4a9d-8576-393ae76e7ee6   ext4                                     
/dev/sda1        465EAAF85EAADFC3                       ntfs       Ubuntu                        
/dev/sda2        4A1CB7A01CB7858B                       ntfs       Seven                         
/dev/sda3        02A8B886A8B87A2D                       ntfs       All I have is here :)         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/All I have is here :) fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/Seven             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 465eaaf85eaadfc3
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   5.1GB: boot/grub/core.img
   3.8GB: boot/grub/grub.cfg
   5.6GB: boot/initrd.img-2.6.32-21-generic
   6.9GB: boot/initrd.img-2.6.32-24-generic
   5.6GB: boot/vmlinuz-2.6.32-21-generic
   6.1GB: boot/vmlinuz-2.6.32-24-generic
   6.9GB: initrd.img
   5.6GB: initrd.img.old
   6.1GB: vmlinuz
   5.6GB: vmlinuz.old
```Thanx again .

---

### Post by Shoala on 2010-09-21
Can any one tell me what's next move ? I really need to fix this problem fast .

---

### Post by wilee-nilee on 2010-09-21
What I can do, since you have a W7 disc, is we can reload windows bootloader to the master boot record with the W7 disc if it is a bootable recovery or install dvd. 

I'm fairly sure that Ubuntu wont show in the boot as before, but with the right help it can probably, I say again, probably be gotten back. You can also access the Ubuntu from Windows. If this sounds feasible at the moment then follow these instructions and only run the command that is in bold. there is a link to the W7 forums for direction to the command line in the booted recovery or install dvd for Windows7. 

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

So this will only get windows back, most likely for now, and getting the wubi to boot again will need another helper.

---

### Post by aa-hcl on 2010-09-21
Hi,

I had exactly the same problem with my older laptop:

after rebooting i get only the grub rescue and nothing else.

I then got the following solution:

Solution:  boot with LiveCD, then run:  (need to be ROOT  - type sudo -s first!)

fdisk -l    - this will list you all the partitions - need to find where is the linux and what to repair.

Example:

```

fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb471b471

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22947   184321746    7  HPFS/NTFS
/dev/sda2           22948       38914   128249072    f  W95 Ext'd (LBA)
/dev/sda5           22948       24477    12289693+   7  HPFS/NTFS
/dev/sda6           24478       25450     7812500   82  Linux swap / Solaris
/dev/sda7           25450       38914   108146688   83  Linux

```

If you then need to repair the Linux filesystem on /dev/sda7

then do 

```

fsck -r /dev/sda7

```


and that clears all the errors and everything is fine then.
(-r will force fsck to prompt for any repairs...)

At least the above worked for me several times

---

### Post by wilee-nilee on 2010-09-21
> **aa-hcl said:**
> Hi,

I had exactly the same problem with my older laptop:

after rebooting i get only the grub rescue and nothing else.

I then got the following solution:

Solution:  boot with LiveCD, then run:  (need to be ROOT  - type sudo -s first!)

fdisk -l    - this will list you all the partitions - need to find where is the linux and what to repair.

Example:

```

fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb471b471

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22947   184321746    7  HPFS/NTFS
/dev/sda2           22948       38914   128249072    f  W95 Ext'd (LBA)
/dev/sda5           22948       24477    12289693+   7  HPFS/NTFS
/dev/sda6           24478       25450     7812500   82  Linux swap / Solaris
/dev/sda7           25450       38914   108146688   83  Linux

```

If you then need to repair the Linux filesystem on /dev/sda7

then do 

```

fsck -r /dev/sda7

```


and that clears all the errors and everything is fine then.
(-r will force fsck to prompt for any repairs...)

At least the above worked for me several times

You are completely wrong this is a wubi install.

Edit: Fortunately this was fixed, don't worry I have done the same thing. ;)

---

### Post by Shoala on 2010-09-21
> **wilee-nilee said:**
> What I can do, since you have a W7 disc, is we can reload windows bootloader to the master boot record with the W7 disc if it is a bootable recovery or install dvd. 

I'm fairly sure that Ubuntu wont show in the boot as before, but with the right help it can probably, I say again, probably be gotten back. You can also access the Ubuntu from Windows. If this sounds feasible at the moment then follow these instructions and only run the command that is in bold. there is a link to the W7 forums for direction to the command line in the booted recovery or install dvd for Windows7. 

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

So this will only get windows back, most likely for now, and getting the wubi to boot again will need another helper.

**I dont know how to say thank you **
[B]BootRec.exe /fixmbr was like a miracle , Now I have both seven and ubuntu back with out any broblem, SO FAR :P 
thanx again .


[/B]

---

### Post by wilee-nilee on 2010-09-21
> **Shoala said:**
> **I dont know how to say thank you **
[B]BootRec.exe /fixmbr was like a miracle , Now I have both seven and ubuntu back with out any broblem, SO FAR :P 
thanx again .
[/B]

I looked at the script closer and by comparing it with another thread of similarity and a boot script I had done a wubi install to generate; it looked like Ubuntu would be there. I realized this about 10 min ago, but I thought well we will see what happens. I don't like to promise much especially in a area (Wubi) I'm just not real versed in. 

Yay is what I say.:popcorn:

---

### Post by wilee-nilee on 2010-09-21
In a Wubi set up you see a grub menu, but it is different then a regular setup. So if you see a grub update/upgrade in Ubuntu don't install it to anywhere. That is probably what happened, it shouldn't be that way, but the grub updates don't seem to recognise the wubi environment. Basically some how grub was put in the MBR, probably a update so watch carefully.

---

### Post by Rubi1200 on 2010-09-21
FYI this is apparently becoming an issue with Wubi installs and GRUB updates:
> **[COLOR=Red][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that [COLOR=Red]Grub 2 was installed in the MBR and/or on the  Windows partition[/COLOR]. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections [COLOR=Red]or Grub 2's  failure to recognize a Wubi install[/COLOR], it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Fellow forum member bcbc has reported this and usually advises reinstalling the Windows bootloader as the solution.

---

### Post by Shoala on 2010-09-21
All I can say is thank you .

---

