---
title: "Grub is killing me"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Babyd3k on 2010-04-11
I have a dell inspirion 6000, I upgraded it to a 320Gb drive. I wanted to dual boot XP and Karmic on it so I had to *partition* it into 4 *partitions* to get around the 128Gb BIOS limit. Part 1 is a 10Gb ext3 part for boot (I know it's larger then necessary but I was trying some things), Part 2 is a 50 Gb ext4 part for Karmic, part 3 is a 5Gb swap and 4 is 243Gb NTFS for XP. 

Now everything was working great. Then suddenly XP just stopped booting. Whenever I go to XP in Grub 1.97 beta 4 I get the error, NO SUCH DEVICE: (address). The address matches the *partition* I want to boot. I have checked the drive for errors it's fine. I can write to and from the drive in Karmic. I have tried sudo rebuild grub and sudo rebuild grub2 they both work fine but nothing changes. I don't want to reformat I'd rather just fix this. Anyone have any ideas?

---

### Post by ubun2warrior on 2010-04-11
I would suggest that you format and do a fresh install of XP first and then install Karmic inside XP. The installation inside XP will be very fast also. I have also faced similar problems and after doing a lot of search I found that this setup is much better when you dual boot with XP. Also one more advice, don't perform updates when you have a dual boot setup as it reconfigures the grub and dual boot fails.
I know that reformatting is very troublesome but then its very simple.

---

### Post by wilee-nilee on 2010-04-11
Before you start reformatting post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This will give a read out of your partitions and where grub has been installed and MBR info.

---

### Post by wilee-nilee on 2010-04-11
> **ubun2warrior said:**
> I would suggest that you format and do a fresh install of XP first and then install Karmic inside XP. The installation inside XP will be very fast also. I have also faced similar problems and after doing a lot of search I found that this setup is much better when you dual boot with XP. Also one more advice, don't perform updates when you have a dual boot setup as it reconfigures the grub and dual boot fails.
I know that reformatting is very troublesome but then its very simple.

Running a stable OS in one that is plagued with problems may work for you but is not a good idea. Also what you describe is not a true dual-boot it is a pseudo virtual setup. It would be better if you go this route to actually use a virtual, you can save the whole setup backed up off the computer and just load it to run again.

Don't get me wrong I have XP and W7 but I would never rely on them to run my Linux setup that just leaves so many obstacles in case of problems.

---

### Post by Babyd3k on 2010-04-11
Well I need XP to sync several devices and for my work. I use Ubuntu for day to day stuff because it is superior.

Here is the out-put of that script.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d617a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     2,040,254     2,040,192  83 Linux
/dev/sda2           2,040,255   104,438,564   102,398,310  83 Linux
/dev/sda3         104,438,565   114,671,969    10,233,405  82 Linux swap / Solaris
/dev/sda4    *    114,671,970   625,137,344   510,465,375   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6490ebc9-495d-49cc-b8df-0005ab1a3c21   ext3                                     
/dev/sda2        df635039-47cf-4709-b5b9-a27839c31205   ext4                                     
/dev/sda3        e41d5bf9-f42e-4036-8ccc-629c2663c086   swap       Swap                          
/dev/sda4        ACF47512F474E04E                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext3       (rw)
/dev/sda4        /home/dennisl/Windows_XP_HD fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set df635039-47cf-4709-b5b9-a27839c31205
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
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-20-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro   quiet splash
    initrd    /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-20-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro single 
    initrd    /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-19-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro   quiet splash
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-19-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro single 
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-17-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-17-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-16-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro   quiet splash
    initrd    /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-16-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro single 
    initrd    /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-14-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6490ebc9-495d-49cc-b8df-0005ab1a3c21
    linux    /vmlinuz-2.6.31-14-generic root=UUID=df635039-47cf-4709-b5b9-a27839c31205 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set acf47512f474e04e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .7GB: grub/core.img
    .7GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: initrd.img-2.6.31-17-generic
    .1GB: initrd.img-2.6.31-19-generic
    .0GB: initrd.img-2.6.31-20-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .1GB: vmlinuz-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-20-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=df635039-47cf-4709-b5b9-a27839c31205 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6490ebc9-495d-49cc-b8df-0005ab1a3c21 /boot           ext3    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=e41d5bf9-f42e-4036-8ccc-629c2663c086 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

UUID=ACF47512F474E04E /home/dennisl/Windows_XP_HD ntfs defaults 0 0


=================== sda2: Location of files loaded by Grub: ===================


   1.0GB: initrd.img
   1.1GB: initrd.img.old
   1.1GB: vmlinuz
   1.1GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

