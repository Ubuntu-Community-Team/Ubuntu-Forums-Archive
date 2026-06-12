---
title: "/dev/disk/by-uuid/ error after install. How to fix?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by jwally on 2011-01-10
I'm super new to Ubuntu/linux, and am currently trying
to set up a dual boot Windows 7 / Ubuntu box, but have
just stalled and was looking for some guidance.
[B]
BACKGROUND[/B]
I'm on a Sony Viao VPCF114FX (no CD/DVD Drive)
Running Windows 7

**PROBLEM**
Whenever I restart the computer, I'm given a prompt titled
> 
Gnu GRUB VERSION 1.98 - 1ubuntu7 Ubuntu with Linux 2.6.32-27-Generic aec


I select to start Ubuntu, 
cursor blinks for a minute,
then says the following:

> 
Gave up waiting for root device. Common problems:
-      Boot args (cat /proc/cmdline)
-      Check rootdelay= (did the system wait long enough?)
-      Check root= (did the system wait for right device?)
-      Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/e841edb8507-4b4d9ef3-b3533f47d60 does not exist. Dropping to shell!

BusyBox .............


(initramfs)_


Any ideas on how to correct this?

---

### Post by drs305 on 2011-01-10
jwally,

Welcome to Ubuntu and the Ubuntu forums.

Ok, so no CD and not able to connect.

How did you install Ubuntu? Was it supposed to be an installation within Windows (Wubi) or a separate installation?

Do you have any idea, if a separate installation, which partition it was installed on?

At the grub menu, try pressing "c" and then type **ls**. Does it list your partitions? If you know the partition on which Ubuntu was installed (if not Wubi), try: **ls (hdX,Y)/boot**. For example: ls hd(0,5)/boot
Anything?

If you never see the Grub 2 menu, try holding down the SHIFT key during boot.

---

### Post by jwally on 2011-01-10
thanks for the welcome!

I (think) I loaded Ubuntu off a USB Drive which was
set-up through UNetbootin.

When I installed Ubuntu, I wrote down the following
> 
Windows Vista (loader)(/dev/sdb1) - 9.3GB
Windows 7 (loader)(/dev/sdb2) - 104.9MB
/dev/sdb3 - 180.2GB
Free Space - 310.5GB


(I think) I selected the option to install the OS
on the greatest contiguous free space.

let me restart to see what partitions I can get listed.
Again, thanks!

---

### Post by jwally on 2011-01-10
ok,

Rebooted, got to grub menu and hit 'c'
brought up a boot - grub, typed 'ls' and got the following:

> 
(hd0)
(hd0,6)
(hd0,5)
(hd0,3)
(hd0,2)
(hd0,1)


all of them, and even some I made up appeared to return the exact same,
which is as follows:

> 
Device(Null) FileSystem type ext 2 last modification time - 2011-01-10, UUID
e841e5db-8507-4b4d-9ef3-bO3533f47a6O


btw, is there anyway to not handwrite all this?
I'm sure there's something painfully obvious I'm not 
doing, but still can't think of it :D

---

### Post by psusi on 2011-01-10
Boot from the USB stick again, download the script from:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run:

```
cd Downloads
sudo boot_info_script055.sh
gedit RESULTS.txt

```

Then copy and paste the contents of the file that opens here inside [code] tags.

---

### Post by drs305 on 2011-01-10
Also, have you tried booting with or without the USB install device connected? Whichever you have been doing, reverse it. The bootloader may be on a different device than the OS or the BIOS may be looking in the wrong place.

---

### Post by jwally on 2011-01-10
I'm in live CD's ubuntu right now,
I downloaded boot_info_script055.sh
I have a terminal open,
typed cd Downloads
typed the following:

```

sudo boot_info_script055.sh

```

and receive the following:

```

ubuntu@ubuntu:~/Downloads$ sudo boot_info_script055.sh
sudo: boot_info_script055.sh: command not found
ubuntu@ubuntu:~/Downloads$ dir
boot_info_script055.sh
ubuntu@ubuntu:~/Downloads$ 

```

Am I not capitalizing something that should be?

---

### Post by drs305 on 2011-01-10
Run it as:
```
sudo ./boot_info_script055.sh
```

---

### Post by psusi on 2011-01-10
Ooops, I left out the bash:

sudo bash boot_info_script055.sh

---

### Post by jwally on 2011-01-10
figured it out, I needed to
```

sudo bash boot_info_script055.sh

```and the results.txt are:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2100 MB, 2100297728 bytes
2 heads, 63 sectors/track, 32556 cylinders, total 4102144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     4,102,143     4,102,112   6 FAT16


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    18,194,431    18,192,384  27 Hidden HPFS/NTFS
/dev/sdb2    *     18,194,432    18,399,231       204,800   7 HPFS/NTFS
/dev/sdb3          18,399,232   565,122,715   546,723,484   7 HPFS/NTFS
/dev/sdb4         565,123,070   976,773,119   411,650,050   5 Extended
/dev/sdb5         565,123,072   959,999,999   394,876,928  83 Linux
/dev/sdb6         960,002,048   976,773,119    16,771,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        909D-F255                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        44BA24B1BA24A182                       ntfs       Recovery                      
/dev/sdb2        D0CA1AF1CA1AD396                       ntfs       System Reserved               
/dev/sdb3        CC861D1D861D0A1A                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        e841e5db-8507-4b4d-9ef3-b03533f47a60   ext4                                     
/dev/sdb6        5f13fcf9-2bb1-4a52-9ffc-df708df67f67   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
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
search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 44ba24b1ba24a182
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set d0ca1af1ca1ad396
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
UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5f13fcf9-2bb1-4a52-9ffc-df708df67f67 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 377.7GB: boot/grub/core.img
 298.1GB: boot/grub/grub.cfg
 377.5GB: boot/initrd.img-2.6.32-27-generic-pae
 377.7GB: boot/vmlinuz-2.6.32-27-generic-pae
 377.5GB: initrd.img
 377.7GB: vmlinuz

```

---

### Post by psusi on 2011-01-10
Strange; everything looks fine.  Try to boot from the hd again, and when you get to the busybox prompt, type "ls /dev/sd* /dev/disk/by-uuid" and post the results.

---

### Post by drs305 on 2011-01-10
Update. The OP has completely purged and reinstalled Grub2 without success. The boot hangs on "ALERT! /dev/disk/by-uuid/e841... does not exist, dropping to shell" message even though the UUIDs match.

He is attempting to boot from the grub prompt, and if that doesn't work will repost a new copy of RESULTS.txt

Update: Re the next post: [COLOR="Red"]root=/dev/sda[/COLOR] vs **root=/dev/sda5** has been discussed already. Also note that sda and sdb have now reversed. The "set root=" is no longer valid although this is superseded by the manual boot anyway.

---

### Post by jwally on 2011-01-10
Followed the following procedures:

```

1. Reboot
2.  'c'
3. 'ls'                                    # see 6 arrays(?)  (hd0), (hd0,6)...(hd0,1); excluding (hd0,4); and (fd0)
                                            # throws error:fd0 cannot get c/h/s values
4. 'ls (hd0,5)/boot/grub'       # see tons of .mod files
5. 'insmod (hd0,5)/boot/grub/lext2.mod'      # 'ext2' is already loaded
6. 'insmod (hd0,6)/boot/grub/linux.mod'
7. 'set prefix=(hd0,5)/boot/grub'
8. 'set root=(hd0,5)'
9. 'linux (hd0,5)/vmlinuz root=/dev/sda ro'
10. initrd (hd0,5)/initrd.img
11. boot

```

This threw up a lot of text; I've seen similar when I've tried to boot in safe mode in the past
There was a COMRESET Failed (erno -16) I noticed,
and  something about limiting SATA LINK SPEED to 1.5GBPS

and also "Alert /dev/sda5 does not exist"


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1               2,048    18,194,431    18,192,384  27 Hidden HPFS/NTFS
/dev/sda2    *     18,194,432    18,399,231       204,800   7 HPFS/NTFS
/dev/sda3          18,399,232   565,122,715   546,723,484   7 HPFS/NTFS
/dev/sda4         565,123,070   976,773,119   411,650,050   5 Extended
/dev/sda5         565,123,072   959,999,999   394,876,928  83 Linux
/dev/sda6         960,002,048   976,773,119    16,771,072  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2100 MB, 2100297728 bytes
2 heads, 63 sectors/track, 32556 cylinders, total 4102144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,102,143     4,102,112   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        44BA24B1BA24A182                       ntfs       Recovery                      
/dev/sda2        D0CA1AF1CA1AD396                       ntfs       System Reserved               
/dev/sda3        CC861D1D861D0A1A                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e841e5db-8507-4b4d-9ef3-b03533f47a60   ext4                                     
/dev/sda6        5f13fcf9-2bb1-4a52-9ffc-df708df67f67   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        909D-F255                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
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
search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e841e5db-8507-4b4d-9ef3-b03533f47a60
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 44ba24b1ba24a182
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set d0ca1af1ca1ad396
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e841e5db-8507-4b4d-9ef3-b03533f47a60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5f13fcf9-2bb1-4a52-9ffc-df708df67f67 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 377.5GB: boot/grub/core.img
 298.1GB: boot/grub/grub.cfg
 377.5GB: boot/initrd.img-2.6.32-27-generic-pae
 377.7GB: boot/vmlinuz-2.6.32-27-generic-pae
 377.5GB: initrd.img
 377.7GB: vmlinuz

```

---

### Post by psusi on 2011-01-11
I reiterate my previous post.

---

### Post by drs305 on 2011-01-11
Update: Post #7 would have booted but *sda* rather than *sda5* was mistakenly entered in the manual boot from the grub prompt.

The OP has Ubuntu booting. Removing all references to UUIDs in the menuentry (removing 'search' line, changing the 'linux' root value to sda5) allowed him to boot to a low graphics mode. 

The OP stuck a 'non-UUID' menuentry in 40_custom so he would have a reliable menuentry during boot and he is currently updating his system and attempting to install a video driver. Whether or not G2 and initramfs will accept the UUIDs after the update remains to be seen.

---

### Post by jagelove on 2012-04-20
Was this ever resolved? I'm having the exact same problem. Also there's a flash of some error before this error comes up. But I can't quite read it as it's on the screen for a millisecond.

I installed Ubuntu from the Windows installation package, on Windows 7, on my HDD. The boot menu appears ok, but when I choose Ubuntu, the screen is blank for a while and then this same error message comes up.

If this was already resolved, anyone care to point the resolving post? I'm not going through this thread from the beginning.

Thanks.

---

### Post by strask on 2012-04-20
> **jagelove said:**
> If this was already resolved, anyone care to point the resolving post? I'm not going through this thread from the beginning.

The "resolving post" is immediately before your own post. Before you posted, it was at the end of the thread. The end of a thread is usually where things get resolved, so if you really can't read a two-page thread from the beginning, you might just skip to the end and at least read *that* before you post asking someone else to find the answer for you.

---

