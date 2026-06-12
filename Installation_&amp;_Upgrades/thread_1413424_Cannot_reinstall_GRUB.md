---
title: "Cannot reinstall GRUB"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by JNied on 2010-02-22
I installed Windows after I already had Linux, and it wiped out GRUB, so now I can only boot Windows.

I've tried a few tutorials and walkthroughs for reinstalling GRUB, but none of them have worked.

Here's what I've tried:

Super GRUB Boot Disc
I tried the option to reinstall GRUB, and I get a "file not found" error.

Using the grub command:
I don't have the exact output, but basically it's looking for "stage1" and it can't find it.

Using the grub-install command:```
ubuntu@ubuntu:/$ grub-install hd0
Probing devices to guess BIOS drives. This may take a long time.
sed: can't read /boot/grub/device.map: No such file or directory
Could not find device for /boot: Not found or not a block device.
```And finally I tried getting it from [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/) but I could not find any specific installation notes. I tried the following (Forgive my noobishness, I have no idea if I'm doing this right):```
ubuntu@ubuntu:/media/External One/Temp/multiboot-0.6.96$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /media/External: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
configure: creating ./config.status
config.status: creating Makefile
config.status: creating docs/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

ubuntu@ubuntu:/media/External One/Temp/multiboot-0.6.96$ sudo make
make  all-recursive
make[1]: Entering directory `/media/External One/Temp/multiboot-0.6.96'
Making all in docs
make[2]: Entering directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[2]: Entering directory `/media/External One/Temp/multiboot-0.6.96'
make[2]: Leaving directory `/media/External One/Temp/multiboot-0.6.96'
make[1]: Leaving directory `/media/External One/Temp/multiboot-0.6.96'

ubuntu@ubuntu:/media/External One/Temp/multiboot-0.6.96$ sudo make install
Making install in docs
make[1]: Entering directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[2]: Entering directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/info" || /bin/mkdir -p "/usr/local/share/info"
 /usr/bin/install -c -m 644 './multiboot.info' '/usr/local/share/info/multiboot.info'
 install-info --info-dir='/usr/local/share/info' '/usr/local/share/info/multiboot.info'
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
make[2]: Leaving directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[1]: Leaving directory `/media/External One/Temp/multiboot-0.6.96/docs'
make[1]: Entering directory `/media/External One/Temp/multiboot-0.6.96'
make[2]: Entering directory `/media/External One/Temp/multiboot-0.6.96'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/media/External One/Temp/multiboot-0.6.96'
make[1]: Leaving directory `/media/External One/Temp/multiboot-0.6.96'
```

---

### Post by darkod on 2010-02-22
DON'T USE super grub. Often it will create more problems than it solves.

First of all, did you have 9.10 clean install? In that case you are using grub2 and you should follow instructions ONLY for grub2.

Boot with your ubuntu cd, Try Ubuntu option and once the live desktop loads in terminal execute:

sudo fdisk -l

Post the output here so we can see the partitions on your hdd and I can give you the commands to reinstall grub2 to the MBR of the hdd.

---

### Post by kansasnoob on 2010-02-22
I think it would be best to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It always takes a lot of guess work out of things :)

---

### Post by JNied on 2010-02-23
> **darkod said:**
> DON'T USE super grub. Often it will create more problems than it solves.

First of all, did you have 9.10 clean install? In that case you are using grub2 and you should follow instructions ONLY for grub2.

Boot with your ubuntu cd, Try Ubuntu option and once the live desktop loads in terminal execute:

sudo fdisk -l

Post the output here so we can see the partitions on your hdd and I can give you the commands to reinstall grub2 to the MBR of the hdd.It was originally a clean 9.10 install, but had been updated since.  I don't know for sure what version I was using before I lost GRUB.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7fa5472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9331    74951226   83  Linux
/dev/sda2   *        9332        9344      102400    7  HPFS/NTFS
/dev/sda3            9344       18662    74847656+   7  HPFS/NTFS
/dev/sda4           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79ea3d1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001    7  HPFS/NTFS
```> **kansasnoob said:**
> I think it would be best to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It always takes a lot of guess work out of things ```
Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7fa5472

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   149,902,514   149,902,452  83 Linux
/dev/sda2    *    149,903,360   150,108,159       204,800   7 HPFS/NTFS
/dev/sda3         150,108,160   299,803,472   149,695,313   7 HPFS/NTFS
/dev/sda4         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79ea3d1b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0bd2f3e5-481b-4d29-8150-0e8befa2eba8   ext4                                     
/dev/sda2        80B25A2CB25A26C6                       ntfs       System Reserved               
/dev/sda3        3E8A5E0B8A5DBFD7                       ntfs                                     
/dev/sda5        e4475568-df01-42a0-bd20-0d6ae8813771   swap                                     
/dev/sdb1        2ADE5050DE501703                       ntfs       External One                  

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/External One      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0bd2f3e5-481b-4d29-8150-0e8befa2eba8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 80b25a2cb25a26c6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e4475568-df01-42a0-bd20-0d6ae8813771 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  23.1GB: boot/grub/core.img
  23.1GB: boot/grub/grub.cfg
  23.1GB: boot/grub/menu.lst
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.8GB: boot/initrd.img-2.6.31-16-generic
    .7GB: boot/initrd.img-2.6.31-17-generic
  23.0GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-16-generic
    .9GB: boot/vmlinuz-2.6.31-17-generic
   3.9GB: boot/vmlinuz-2.6.31-19-generic
  23.0GB: initrd.img
    .7GB: initrd.img.old
   3.9GB: vmlinuz
    .9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc
```

---

### Post by JNied on 2010-03-15
I'm sorry, I don't mean to revive the dead, but this is still a problem I'm having.  I responded to the questions asked of me but never received any more feedback.  Any help or advice any has would be greatly appreciated.

---

### Post by lindsay7 on 2010-03-16
I just used this to get Ubuntu booting again after a new Windows 7 install.

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by oldefoxx on 2010-03-16
There is a simple tool out there for Windows users who are willing to continue to live with Boot.int and just have boots to their other operating systems added to it.  You might even prefer this method, in which tell the Ubuntu installer to write the Grub start-up process to a different partition besides (hd0).

This tool is called bootpart.exe, and it is easily found with a web search.  It only has a few elements to it.  It shows you what is in your boot.ini file now. if scans all your partitions and puts an asteric (*) in front of any with a bootable system on it, and you tell it which ones you want to add to boot.ini.

It does one other thing: For each of those partitions, it writes a small binary boot file the C:\, and when you pick a partition, it executes the binary file and takes you right there.  Not much in the way of instructions, but it has been used enough that other found links can explain it pretty well.

If you set it up one way, you first go through the Windows boot screen, and if you pick one that you label something like "Grub Boot Method (Next Screen)", picking that one will take you to grub, with whatever choices it offers.  Certainly worth looking at. and Boot.ini is way easier to edit as well.  Just use Attrib first to get rid of its attributes.

attrib -r -s -h boot.ini

After the edit is saved, you use Attrib with plus signs to set them back.

---

### Post by JNied on 2010-03-16
Lindsay, I tried that and it seemed to work, but I got this when I rebooted: > GRUB loading.
error: file not found
grub rescue>I get that "file not found" error with every GRUB recovery I've tried.  It doesn't say which file it's trying to find, only that it can't.

Oldefoxx, I will go ahead and try that next time I'm in Windows and see how it works.

Thank you both for your information.

---

### Post by Turbojoe on 2010-03-16
I've been dealing with the exact same problem since I installed Windows 7 back in October. No suggested fixes I've gotten have worked for me. I'm watching this thread with hopes you find something that works. Maybe it'll work for me too.

Joe

---

### Post by presence1960 on 2010-03-16
> **JNied said:**
> Lindsay, I tried that and it seemed to work, but I got this when I rebooted: I get that "file not found" error with every GRUB recovery I've tried.  It doesn't say which file it's trying to find, only that it can't.

Oldefoxx, I will go ahead and try that next time I'm in Windows and see how it works.

Thank you both for your information.

Can you run another boot info script again since you made some changes. I noticed you have both a menu.lst (GRUB Legacy) and a grub.cfg (GRUB 2) in your ubuntu boot files/directories. How did that happen? Did you do a dist-upgrade from 9.04 and never run the command to convert to GRUB 2. Or did you try to install Legacy GRUB at one point?

EDIT: this from your menu.lst on sda1:

```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

[COLOR="Red"]title        Chainload into GRUB 2
root        0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel        /boot/grub/core.img[/COLOR]
```

You did not do a clean install of 9.10 because you have a chainload to GRUB2 entry in menu.lst. When you do a clean install of 9.10 GRUB 2 is the default and there will be no menu.lst.

---

### Post by JNied on 2010-03-17
I've done a lot of upgrades, updates and mods after installing my system, so I don't remember for sure.  I remember trying to simply install GRUB from aptitude at some point.

The disc I had said 9.10 on it, but I think I originally installed 9.04 and later when asked to install Ubuntu on a friend's computer I grabbed a 9.10 disc.

In any case, I'm not entirely sure how I got those files or what all I've upgraded.

Here's the boot info script again:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7fa5472

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   149,902,514   149,902,452  83 Linux
/dev/sda2    *    149,903,360   150,108,159       204,800   7 HPFS/NTFS
/dev/sda3         150,108,160   299,803,472   149,695,313   7 HPFS/NTFS
/dev/sda4         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4499be5b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79ea3d1b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0bd2f3e5-481b-4d29-8150-0e8befa2eba8   ext4                                     
/dev/sda2        80B25A2CB25A26C6                       ntfs       System Reserved               
/dev/sda3        3E8A5E0B8A5DBFD7                       ntfs       test                          
/dev/sda5        e4475568-df01-42a0-bd20-0d6ae8813771   swap                                     
/dev/sdb1        4A820911820902E5                       ntfs       External Backup               
/dev/sdc1        2ADE5050DE501703                       ntfs       External One                  

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=jason)
/dev/sdc1        /media/External One      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/External Backup   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0bd2f3e5-481b-4d29-8150-0e8befa2eba8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		0bd2f3e5-481b-4d29-8150-0e8befa2eba8
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 0bd2f3e5-481b-4d29-8150-0e8befa2eba8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 80b25a2cb25a26c6
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0bd2f3e5-481b-4d29-8150-0e8befa2eba8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e4475568-df01-42a0-bd20-0d6ae8813771 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  26.2GB: boot/grub/grub.cfg
  23.1GB: boot/grub/menu.lst
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.8GB: boot/initrd.img-2.6.31-16-generic
    .7GB: boot/initrd.img-2.6.31-17-generic
  23.0GB: boot/initrd.img-2.6.31-19-generic
  26.7GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-16-generic
    .9GB: boot/vmlinuz-2.6.31-17-generic
   3.9GB: boot/vmlinuz-2.6.31-19-generic
  22.8GB: boot/vmlinuz-2.6.31-20-generic
  26.7GB: initrd.img
  23.0GB: initrd.img.old
  22.8GB: vmlinuz
   3.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by presence1960 on 2010-03-17
Ok it looks like you did a dist-upgrade to 9.10 because you do have menu.lst with a chainload to GRUB 2 entry. You probably never ran the terminal command to completely convert to GRUB 2.

This is what I would do. Boot a 9.04 Live CD & choose "try ubuntu without any changes". When the destop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
3. Type "root (hd0,0)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

See if this fixes it. This is one misgiving I have about upgrades to 9.10 is that you have the option of keeping Legacy GRUB with a chainload to GRUB 2 entry in menu.lst. You then have to run a command in terminal to convert fully to GRUB 2 after trying the chainload command. IMHO if GRUB 2 is the default for 9.10 there should be no choice, but I don't make the decisions.

---

### Post by rabbitfarmer on 2010-03-21
Hey i'm having this same problem, and i've tried what presence said but i get

root@john-laptop:~# find /boot/grub/stage1
find: &#8216;/boot/grub/stage1&#8217;: No such file or directory

I have Ubuntu 9.10 and recently had to reinstall vista
 my fdisk -l command is:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fa50e1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27355   219729006    7  HPFS/NTFS
/dev/sda2           27356       38913    92839635    5  Extended
/dev/sda5           37579       38850    10217308+  83  Linux
/dev/sda6           38851       38913      506016   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc4684b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by lemming465 on 2010-03-21
I run a lot of complicated multi-boot setups, and what I like to do after windows has usurped the MBR away from the Grub-du-jour is boot a live CD, chroot into the ubuntu install which I want owning the boot menu, and reinstall grub from there.  For rabbit farmer this would look like:```
sudo -i
mkdir /media/sda5
mount /dev/sda5 /media/sda5
cd /media/sda5
for f in sys dev proc; do mount -o bind /$f $f; done
chroot .
update-grub
exit
cd /
umount /media/sda5
```
It helps a lot if you boot a live CD that matches your installed Ubuntu version.  (You can check the current version with *lsb_release -a*.)

JNied can do the same thing, but should use sda1 instead of sda5, e.g. *mkdir /media/sda1; mount /dev/sda1 /media/sda1; cd /media/sda1* etc.

---

### Post by rabbitfarmer on 2010-03-21
well i have the live cd but when i do that it can't find grub, so right now i'm by passing windows by using super grub live cd. I tried what you said but it didn't seem to change anything and after i also tried the method by presence again and got:

grub> find /boot/grub/stage1

Error 15: File not found


so i'm guessing i need that file to reinstall grub but honestly i have no idea. thanks for the tries so far and i'm new to linux so simple instructions are best! thanks! I'll check back often if anyone needs me to run anything or has more suggestions

---

### Post by oldfred on 2010-03-22
rabbitfarmer - IF you installed your Karmic clean you do not have old grub legacy but grub2. This is why we prefer those with different problems post new threads as the solutions are different and in the same thread it gets confusing for all of us which response is for which problem.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by rabbitfarmer on 2010-03-22
Wow, no idea how i missed that thread. yea you were correct old fred, i followed the link and everything worked great. Thanks for help everyone hope i didn't mislead to many people. now to enjoy the first time my dual booting has worked in two weeks!

---

### Post by JNied on 2010-03-29
> **presence1960 said:**
> ...This is what I would do. Boot a 9.04 Live CD & choose "try ubuntu without any changes". When the destop loads open a terminal and do this:...```
grub> find /boot/grub/stage1

Error 15: File not found
```This is the error that always stops me in every grub-reinstall tutorial I've tried.


> **oldfred said:**
> ...How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)I get the same "file not found" error, but it does it when I try to boot.  I get that error and then a grub prompt and can't get past that point.

---

### Post by lemming465 on 2010-03-30
JNied, your fairly detailed disk layout and file stuff from about a week ago shows both sda1:/boot/grub/menu.lst and sda1:/boot/grub/grub.cfg.  The menu.lst is from grub1, probably from the original 9.04 install.  The grub.cfg is from grub2, which is either from upgrading 9.04 -> 9.10 plus some post-install reconfiguration, or from doing an overlay install of 9.10 atop 9.04 without reformating the root partition along the way.

Did you try my chroot suggestion above?  That should work for either grub1 or grub2; in your case probably grub2.  Boot a live 9.10 CD, mount /dev/sda1, chroot into it, and run update-grub from inside the chroot.  That usually fixes things for me when windows is fighting over who gets to control the MBR, and I want Linux to win.

---

### Post by JNied on 2010-03-30
Yes, I tried the chroot from the suggestion above.  All of the commands executed successfully but then I get this when I try to boot:```
GRUB loading
error: file not found
grub restore>
```

I get this error on every GRUB restoration tutorial I've tried.  It either happens during the process (for example, I enter a command and it returns that error) or all of the commands are good but then I get it when I try to boot.

---

