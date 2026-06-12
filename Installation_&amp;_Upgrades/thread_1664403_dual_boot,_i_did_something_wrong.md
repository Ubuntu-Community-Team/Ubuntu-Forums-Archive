---
title: "dual boot, i did something wrong?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by ppm123 on 2011-01-10
i have dual core processor, 2gb ram, and win7 prof.installed. 
for dual boot with ubuntu10.10 
made following preparation
with gparted live made --
1)in extended partition- made a)/ 4.88gib,--ext4 b)swap 4gib c)home 10gib--ext4
then selected manual option for install and the proces went on
at the end it said completed.was told to reboot the system. on remving the ubuntu live cd. there was sscreen with lot of info. , could not read whole thing, but it started with failed due to pwdid or something, and then the sreen vanished. 
on rebooting pc went on to reboot normally and showed my window7
there was no boot option screen. 
how do i check what is wrong. 
tried to boot again with live cd. 
tried to mount sda5-which is my root partition -i could mount it and it showed various folers in the log folder tried to look for any errors --could not understand further. 
help required to find the fault please-ppm

---

### Post by Rubi1200 on 2011-01-11
Hi and welcome to the forums :)

Use the LiveCD to boot the computer, choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we can get a better overview of your current setup.

Thanks.

---

### Post by ppm123 on 2011-01-11
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   122,882,047   122,880,000   7 HPFS/NTFS
/dev/sda2         122,886,142   248,723,455   125,837,314   5 Extended
/dev/sda5         122,886,144   139,270,143    16,384,000  83 Linux
/dev/sda6         139,272,192   147,464,191     8,192,000  82 Linux swap / Solaris
/dev/sda7         147,466,240   167,946,239    20,480,000  83 Linux
/dev/sda8         167,948,288   248,723,455    80,775,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   122,882,047   122,880,000   7 HPFS/NTFS
/dev/sdb2         122,882,048   819,202,047   696,320,000   5 Extended
/dev/sdb5         122,884,096   184,324,095    61,440,000   7 HPFS/NTFS
/dev/sdb6         184,326,144   307,206,143   122,880,000   7 HPFS/NTFS
/dev/sdb7         307,208,192   819,202,047   511,993,856   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7D26587E12CA604C                       ntfs       vol c                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3417b034-274f-466f-955a-4cdf94b59197   ext4                                     
/dev/sda6        a123dd91-6d42-4166-b67c-bd04fea07edd   swap       swap                          
/dev/sda7        72b87480-7a0c-430a-8769-718d303ad215   ext4                                     
/dev/sda8        24A51739785031CC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        79BA36A40CA7A728                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        675729F34158B180                       ntfs                                     
/dev/sdb6        158DD48236551780                       ntfs                                     
/dev/sdb7        70F720505FF67DD6                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/79BA36A40CA7A728  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3417b034-274f-466f-955a-4cdf94b59197 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3417b034-274f-466f-955a-4cdf94b59197 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3417b034-274f-466f-955a-4cdf94b59197
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d26587e12ca604c
    chainloader +1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3417b034-274f-466f-955a-4cdf94b59197 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=72b87480-7a0c-430a-8769-718d303ad215 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a123dd91-6d42-4166-b67c-bd04fea07edd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  67.6GB: boot/grub/core.img
  67.6GB: boot/grub/grub.cfg
  68.1GB: boot/initrd.img-2.6.35-22-generic
  63.6GB: boot/vmlinuz-2.6.35-22-generic
  68.1GB: initrd.img
  63.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  01 00 30 30 30 30 63 22  20 65 6e 63 6f 64 69 6e  |..0000c" encodin|
00000010  67 3d 22 62 61 73 65 36  34 22 20 76 61 6c 75 65  |g="base64" value|
00000020  3d 22 63 67 42 6c 41 47  63 41 61 77 42 6c 41 48  |="cgBlAGcAawBlAH|
00000030  6b 41 4b 41 41 6e 41 45  67 41 53 77 42 46 41 46  |kAKAAnAEgASwBFAF|
00000040  6b 41 58 77 42 44 41 45  77 41 51 51 42 54 41 46  |kAXwBDAEwAQQBTAF|
00000050  4d 41 52 51 42 54 41 46  38 41 55 67 42 50 41 45  |MARQBTAF8AUgBPAE|
00000060  38 41 56 41 42 63 41 47  49 41 59 51 42 30 41 47  |8AVABcAGIAYQB0AG|
00000070  59 41 61 51 42 73 41 47  55 41 4a 77 41 70 41 41  |YAaQBsAGUAJwApAA|
00000080  41 41 22 2f 3e 0a 20 20  20 20 20 20 20 20 3c 53  |AA"/>.        <S|
00000090  65 74 4b 65 79 56 61 6c  75 65 20 70 61 74 68 3d  |etKeyValue path=|
000000a0  22 5c 52 65 67 69 73 74  72 79 5c 6d 61 63 68 69  |"\Registry\machi|
000000b0  6e 65 5c 53 63 68 65 6d  61 5c 77 63 6d 3a 2f 2f  |ne\Schema\wcm://|
000000c0  4d 69 63 72 6f 73 6f 66  74 2d 57 69 6e 64 6f 77  |Microsoft-Window|
000000d0  73 2d 73 68 65 6c 6c 33  32 3f 76 65 72 73 69 6f  |s-shell32?versio|
000000e0  6e 3d 36 2e 31 2e 37 36  30 30 2e 31 36 36 34 34  |n=6.1.7600.16644|
000000f0  26 61 6d 70 3b 6c 61 6e  67 75 61 67 65 3d 6e 65  |&amp;language=ne|
00000100  75 74 72 61 6c 26 61 6d  70 3b 70 72 6f 63 65 73  |utral&amp;proces|
00000110  73 6f 72 41 72 63 68 69  74 65 63 74 75 72 65 3d  |sorArchitecture=|
00000120  78 38 36 26 61 6d 70 3b  70 75 62 6c 69 63 4b 65  |x86&amp;publicKe|
00000130  79 54 6f 6b 65 6e 3d 33  31 62 66 33 38 35 36 61  |yToken=31bf3856a|
00000140  64 33 36 34 65 33 35 26  61 6d 70 3b 76 65 72 73  |d364e35&amp;vers|
00000150  69 6f 6e 53 63 6f 70 65  3d 6e 6f 6e 53 78 53 26  |ionScope=nonSxS&|
00000160  61 6d 70 3b 73 63 6f 70  65 3d 61 6c 6c 55 73 65  |amp;scope=allUse|
00000170  72 73 5c 6d 65 74 61 64  61 74 61 22 20 6e 61 6d  |rs\metadata" nam|
00000180  65 3d 22 40 5f 6c 65 67  61 63 79 48 61 6e 64 6c  |e="@_legacyHandl|
00000190  65 72 22 20 74 79 70 65  3d 22 30 78 31 30 30 30  |er" type="0x1000|
000001a0  30 30 30 35 22 20 65 6e  63 6f 64 69 6e 67 3d 22  |0005" encoding="|
000001b0  62 61 73 65 36 34 22 20  76 61 6c 75 65 3d 00 fe  |base64" value=..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 fa 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  fa 00 00 08 7d 00 00 00  |............}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2011-01-11
For some reason, GRUB has not been installed to the MBR of the drive. The partition boot files seem to be okay.

Here is what you need to do:

From a LiveCD, reinstall GRUB. I am assuming sda is set as first device (if not change the command to use sdb).

```
sudo mount /dev/sda5 /mnt

```
```
sudo grub-install --root-directory=/mnt/ /dev/sda

```
Run ```
sudo update-grub
``` back in Ubuntu to pick up the Windows install.

If you need more help, let me know.

---

### Post by ppm123 on 2011-01-11
i can manually select and mount sda5
but not with the command you told
tried few things and this is what i got 
---------------------

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5/mnt
mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo grub-install --root directory=mnt//dev/sda
Unrecognized option `--root'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ sudo update grub
sudo: update: command not found
ubuntu@ubuntu:~$ su update grub
Unknown id: update
ubuntu@ubuntu:~$ /dev/sda5/mnt
bash: /dev/sda5/mnt: Not a directory
ubuntu@ubuntu:~$ sudo mount/dev/sda5/mnt
sudo: mount/dev/sda5/mnt: command not found
ubuntu@ubuntu:~$ 
---------------
should i go for reformat and reinstall ?

---

### Post by Quackers on 2011-01-11
spaces are just as important as any character in Linux. You have missed a space in the first command. There should be a space betweeen /dev/sda5 and /mnt  It is better to copy/paste the commands given in to your terminal screen one at a time, pressing enter after each line.

---

### Post by ppm123 on 2011-01-13
as per the advise, tried again to do it, and this is what what i got
===============


ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 
==========================
now what do i do?

---

### Post by Quackers on 2011-01-13
Reboot and, hopefully, Ubuntu will boot up. If it does, open a terminal and run ```
sudo update-grub
``` which should then pick up your Windows installation on sda1. If it does, reboot and you should have a grub menu with the choice of operating system to boot from.

---

### Post by ppm123 on 2011-01-13
success,
after carefully pasting the commands , as advised with correct spacing, something did happen right
and on rebooting i did see, the long expected dual boot screen. 

now can ask one more query?
i use my windows part to write in indian language-particularly marathi(with devnagari script)
earlier i was using a regional software ==lipik== with true type fonts such as lpk-marathi

later on started using microsoft indic language input tool 
can i install some indian language fonts in ubuntu? so i can read/write using these indian fonts?

---

### Post by Quackers on 2011-01-13
You can ask as many questions as you want :-)
Glad you got the original problems sorted out!
I don't know the answer to your current question, but there are many on here who may do :-) Hopefully somebody will be along shortly.

---

### Post by Rubi1200 on 2011-01-13
Glad things worked out for you with reinstalling GRUB.

I have not done this, but I assume it will work for installing the fonts you want:
[http://linux-myubuntu.blogspot.com/2010/11/installing-marathi-fonts-in-ubuntu-and.html](http://linux-myubuntu.blogspot.com/2010/11/installing-marathi-fonts-in-ubuntu-and.html)

---

