---
title: "Lost XP after install of Lucid"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by gwylan_du on 2010-05-02
Hi

I've just tried to install Lucid on a friend's Toshiba NB200. She had three partitions on there: XP, data, and the Vista HDD recovery partition.  I shrank XP, wiped the (empty) data partition, and then created an ext3 partition for Lucid, and another ex3 partition for data. The bootloader was initially installed to /dev/sda. Install goes fine, restart as commanded, run into what eventually turns out to be this problem: [http://ubuntuforums.org/showthread.php?t=1467481](http://ubuntuforums.org/showthread.php?t=1467481) Before I figured out that this was the cause of those woes, I did another install in which the bootloader went to /dev/sda2. Ubuntu is now working, but windows is not. 

Windows shows up in grub, but when I select it, it goes to "Cannot boot properly - do you want your normal config or safe mode". Either way, when I select it, it takes me back to the grub menu. The Vista recovery HDD gives me "ERROOR: Setenv file P:\Setenv.ini not found!". When I boot using the Lucid USB, it shows me the XP partition and its files. It's just that it won't boot into it.

Here is the output of boot info script
```

                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 39850216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065    39,078,564    39,062,500   7 HPFS/NTFS
/dev/sda2          39,079,936    62,515,199    23,435,264  83 Linux
/dev/sda3         309,893,850   312,576,704     2,682,855  17 Hidden HPFS/NTFS
/dev/sda4          62,517,246   309,893,119   247,375,874   5 Extended
/dev/sda5          62,517,248    66,420,735     3,903,488  82 Linux swap / Solaris
/dev/sda6          66,422,784   309,893,119   243,470,336  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders, total 3911616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,911,039     3,910,977   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2EAAF3AFAAF37227                       ntfs       XP                            
/dev/sda2        1b44dac8-4edf-4832-803b-7ece45411882   ext3                                     
/dev/sda3        3222F72922F6F129                       ntfs       HDDRecovery                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        826e9767-5679-455e-81e9-10278604a7d4   swap                                     
/dev/sda6        5348dd9b-f86c-454a-a78b-2637d93d2e46   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        487D-6655                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/5348dd9b-f86c-454a-a78b-2637d93d2e46 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/1b44dac8-4edf-4832-803b-7ece45411882 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/XP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /forceresetreg

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b44dac8-4edf-4832-803b-7ece45411882 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b44dac8-4edf-4832-803b-7ece45411882 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1b44dac8-4edf-4832-803b-7ece45411882
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2eaaf3afaaf37227
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 3222f72922f6f129
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=1b44dac8-4edf-4832-803b-7ece45411882 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=826e9767-5679-455e-81e9-10278604a7d4 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  20.4GB: boot/grub/core.img
  20.3GB: boot/grub/grub.cfg
  20.4GB: boot/initrd.img-2.6.32-21-generic
  20.3GB: boot/vmlinuz-2.6.32-21-generic
  20.4GB: initrd.img
  20.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 18 83 0e 00 00  |........;.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

If anyone can help me, I'd much appreciate it. I'm sure she'll be perfectly fine with just linux, but she'd quite like the security blanket of being able to go back to windows. :) Sod's law of course: my own upgrade worked absolutely flawlessly and it's the install for a potential convert that has problems...

---

### Post by dino99 on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by oldfred on 2010-05-02
I do not see anything obvious in the boot script. The windows partition usually starts at 63 (yours at sector 16065), but I do not think that should make any difference unless it got moved and you need to run repairs to windows. Did you have another partition before the windows one? The boot.ini is looking for partition 1 so it should be ok.

I would try a manual boot and delete the search line to see if just a simple chainload to the windows PBR works.

---

### Post by gwylan_du on 2010-05-02
No go. But then I don't have that error message. RESULTS.txt shows /dev/sda1, which is XP, as being happy.

Following the instructions in here: [http://ubuntuforums.org/showthread.php?t=1468931](http://ubuntuforums.org/showthread.php?t=1468931) didn't work either. I don't have that actual error message. The message bout core.img shows up in my /dev/sda2 entry, which is ubuntu. The windows one is nominally fine. When I followed those instructions, backupBS didn't appear and the Backup BS was listed as bad. :(

---

### Post by recluce on 2010-05-02
Did you check out the Windows XP partition to verify that the data is still there and at least appears to make sense? I have a suspicion that something went wrong with the shrinking of that partition.

What tool did you use to change the partitions?

---

### Post by gwylan_du on 2010-05-02
Yes, XP is still there and visible. I had to shrink it using the ubuntu installer. I tried shrinking it using partition magic but it wouldn't let me.

---

### Post by oldfred on 2010-05-02
I have to then agree that the partition changes moved the XP partition and something is not right. Normally XP & Ubuntu start at 63 and Vista.7 start at 2048. Yours starts at 16065.

I would run XP repairs. I do not know if now you should go back and move windows to 63??

---

