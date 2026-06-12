---
title: "grub2 can not boot windows 7"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by jtrol on 2010-12-10
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3850d16450d12980
    chainloader +1
}

This is automaticly genarated after installed ubuntu 10.10. It shows black screen with a flashing cursor after press enter. 
Grub 0.97 also does this with:
title win7
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

But the wierd thing is my usb stick can boot windows 7 succesfully with the same configuration. Whats wrong with that? How can do with grub.cfg?

---

### Post by wilee-nilee on 2010-12-10
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Have the thumb plugged in when you run the script as well.

---

### Post by jtrol on 2010-12-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for (,msdos9)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 13.1.0
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 13.1.0
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,926,604    62,926,542   7 HPFS/NTFS
/dev/sda2          62,926,666   121,980,927    59,054,262   5 Extended
/dev/sda5          62,926,668    63,986,894     1,060,227  82 Linux swap / Solaris
/dev/sda6          63,987,712    84,885,503    20,897,792  83 Linux
/dev/sda7          84,887,552    95,041,535    10,153,984  83 Linux
/dev/sda8          95,043,584   105,392,127    10,348,544  83 Linux
/dev/sda9         105,394,176   121,980,927    16,586,752  83 Linux
/dev/sda3         121,981,545   249,907,139   127,925,595  83 Linux
/dev/sda4         249,907,140   312,575,759    62,668,620  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3850D16450D12980                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        874ce887-4895-40cb-badb-8e924887dd7a   ext4                                     
/dev/sda4        7ab9c801-acd8-46c6-8b40-6d0816a0dd59   ext4                                     
/dev/sda5        9610d65f-dd13-42ce-b648-2e1fca367630   swap                                     
/dev/sda6        55a36557-13da-4dc5-b341-f6538fc83e31   ext4                                     
/dev/sda7        5d038e9d-d212-4c0d-8c07-c8655b661998   ext4                                     
/dev/sda8        964daf68-ab9f-4d03-bac6-e1da729cbc74   ext4                                     
/dev/sda9        5e5a4076-c8e1-4029-a952-7d3aac12498d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /1                       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /3                       ext4       (rw,commit=0)
/dev/sda4        /4                       ext4       (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=============================== sda6/etc/fstab: ===============================

/dev/sda5        swap             swap        defaults         0   0
/dev/sda6        /                ext4        defaults         1   1
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0
/dev/sda4       /4               ext4  defaults  0       1
/dev/sda3       /3               ext4  defaults  0       1
/dev/sda1       /1               ntfs-3g  defaults  0       1
=================== sda6: Location of files loaded by Grub: ===================


  39.3GB: boot/vmlinuz
  39.3GB: boot/vmlinuz-huge-smp-2.6.33.4-smp

=============================== sda7/etc/fstab: ===============================

/dev/sda5        swap             swap        defaults         0   0
/dev/sda7        /                ext4        defaults         1   1
/dev/sda3        /3               ext4        defaults         1   2
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0
/dev/sda4       /4               ext4  defaults  0       1
/dev/sda9       /9               ext4  defaults  0       1
/dev/sda6       /6               ext4  defaults  0       1

=================== sda7: Location of files loaded by Grub: ===================


  45.9GB: boot/vmlinuz
  45.9GB: boot/vmlinuz-huge-smp-2.6.33.4-smp

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=5e5a4076-c8e1-4029-a952-7d3aac12498d ro vga=791 splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os 
{
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=5e5a4076-c8e1-4029-a952-7d3aac12498d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}

menuentry 'slackinstall' {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    linux /slackware/bzImage
    initrd    /slackware/initrd.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 5e5a4076-c8e1-4029-a952-7d3aac12498d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3850d16450d12980
    chainloader +1
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 55a36557-13da-4dc5-b341-f6538fc83e31
    linux /boot/vmlinuz-huge-smp-2.6.33.4-smp root=/dev/sda6 vga=791
}
menuentry "Slackware Linux (Slackware 13.1.0) (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 55a36557-13da-4dc5-b341-f6538fc83e31
    linux /boot/vmlinuz-huge-smp-2.6.33.4-smp root=/dev/sda7 vga=791 ro splash
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

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=5e5a4076-c8e1-4029-a952-7d3aac12498d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=226ffbb1-68bb-480f-a0d2-c6f688c9ab0d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /1              ntfs-3g  defaults  0       1
/dev/sda3       /3              ext4  defaults  0       1
/dev/sda4       /4               ext4  defaults  0       1

=================== sda9: Location of files loaded by Grub: ===================


  54.4GB: boot/grub/core.img
  55.0GB: boot/grub/grub.cfg
  54.8GB: boot/initrd.img-2.6.35-22-generic-pae
  57.3GB: boot/initrd.img-2.6.35-23-generic-pae
  54.4GB: boot/vmlinuz-2.6.35-22-generic-pae
  55.7GB: boot/vmlinuz-2.6.35-23-generic-pae
  57.3GB: initrd.img
  54.8GB: initrd.img.old
  55.7GB: vmlinuz
  54.4GB: vmlinuz.old

```

---

### Post by wilee-nilee on 2010-12-10
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /**grldr** /ntldr 
                       /NTDETECT.COM


So this was a XP to W7 upgrade, and the highlighted grldr can cause problems, but I also see people with no problems with grldr. It may be a combination of so many boot files in this area if one gets corrupted it can probably cause some thing wrong to happen.

Have you reloaded the mbr with the MS bootloader to make sure W7 is working I can give you the command and a link to a recovery disc if needed.

It sounds also like you have tried grub-legacy and grub2, so I assume you have run in Ubuntu
sudo update grub as well.

Is your grub menu at startup Ubuntu then slackware? Just curious I believe slackware is lilo generally, and I see two sda6, sda7 both with just etc/fstab entries in the last stanza of each partition listing.

---

### Post by jtrol on 2010-12-10
Yes, i am in Ubuntu. All Linux os on disk can boot up normally.  XP was installed on sda4 and has already been removed.
W7 can boot up with grub4dos in usb stick and is working, but can't boot from disk's mbr. 

Grub-lagacy is installed on slackware partition. Ubuntu never installed grub-lagacy.

I tried remove grldr on sda1 and got the same result.

---

### Post by wilee-nilee on 2010-12-10
> **jtrol said:**
> Yes, i am in Ubuntu. All Linux os on disk can boot up normally.  XP was installed on sda4 and has already been removed.
W7 can boot up with grub4dos in usb stick and is working, but can't boot from disk's mbr. 

Grub-lagacy is installed on slackware partition. Ubuntu never installed grub-lagacy.

I tried remove grldr on sda1 and got the same result.

So with XP gone I would fix that boot in W7, if you have a recovery disc just run the repair 3 times with the  booted recovery or I have the commands if you want them.
W7 recovery disc if needed.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I think your plenty savvy here so I will just give you the whole W7 Vista list. So it is the repair or the commands, personally I like the commands.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

So you can run the repair or the commands on sda1. If you run the the bootrec.exe /fixmbr or the 3 repairs you will have to reload grub2 but it seems your ahead on this already in knowing how.

---

### Post by sikander3786 on 2010-12-10
@**jtrol:**

I doubt if your Windows copy is Legit? It just seems like a pirated copy. Why? Because of presence of /grldr on the Windows partition. Can you explain please?

---

### Post by jtrol on 2010-12-10
Oh, i am sorrry i forget to tell you i have no cdrom now, and my usb stick was not working a few days ago.
I was thinking just do sth with grub.cfg it will be ok.
Do you have Linux way to fix the problem? 
I just wonder why my usb stick can boot w7 and disk mbr doesn't.

---

### Post by jtrol on 2010-12-10
[sikander3786]("http://ubuntuforums.org/member.php?u=806649"):
Write grldr to boot.ini can add an item of grub into ntldr startup menu.

---

### Post by sikander3786 on 2010-12-10
> **jtrol said:**
> [sikander3786]("http://ubuntuforums.org/member.php?u=806649"):
Write grldr to boot.ini can add an item of grub into ntldr startup menu.
Might be ;-)

We are not hesitant in helping you but there is [Forum COC.]("http://ubuntuforums.org/index.php?page=policy")

You definitely need to boot a Windows Disc/USB in order to repair your startup and **wilee-nilee** have provided you with all the information you need.

---

### Post by jtrol on 2010-12-11
thank you [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")

---

