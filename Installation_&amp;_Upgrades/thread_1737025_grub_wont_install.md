---
title: "grub wont install"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by rpm13 on 2011-04-22
Hi.

I have two disks

1. a 500G Sata disk with a working linux (/dev/sdb)
2. a 160G Ata onto which I want to replicate the linux (/dev/sda)

[If that works I can use these disks in different computers]

As far as I can see the replication has gone fine upto grub but grub
install wont work.

By replication I mean
[LIST=a]
[*]Copy out the root boot home etc partitions from sdb(500) to sda(160)
[*]Adjust the fstab in sda to be self contained
[*]Install grub on sda
[*]Physically disconnent sdb and reboot (from sda)
[/LIST]
[Note: Ive used labels instead of uuids to make this more human-readable]
ie on my working disk I have this entry in grub.cfg which boots my
working linux:
```

menuentry "Ubuntu 500" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --label --set Ubuntu500G
        linux   /vmlinuz root=LABEL=Ubuntu500G ro
        initrd  /initrd.img
}

```
I add an entry below which now boots the copied
```

menuentry "Ubuntu 160 handedited" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd1,5)
        search --no-floppy --label --set Ubuntu160D
        linux   /vmlinuz root=LABEL=Ubuntu160D ro
        initrd  /initrd.img
}

```
FYI devices are like this
```

/dev/sdb2 Label Boot500G
/dev/sdb5 Label Ubuntu500G
/dev/sda5 Label Boot160D
/dev/sda7 Label Ubuntu160D

```

The partitions have been copied over from 500 to 160 in the obvious way.

Now the problem:
If the 500G (sdb) is connected the that grub works and I can boot to
the 160G disk's ubuntu

If I disconnect the 500G, I get
No bootable device -- insert boot disk and press any key.

Ive tried
1. Booting into the 160(sda) (via the 500G working grub) and then
1.a dpkg-reconfigure grub-pc and select sda
1.b grub-install /dev/sda

2. Boot from ubuntu live usb
Mount root, boot, chroot and do the above

But none of it works: I keep getting
No bootable device...


I ran boot_info_script. Its results (relevant parts) are as follows:

```

=========== Boot Info Summary: ==========

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
   partition #5 for (,msdos5)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
   partition #2 for /grub.

```

So grub seems to be in sda as well as sdb

[Can someone explain the (,msdos5) in one and not the other?]

```

sda5: _________________________________________________

   File system:       ext4
   Boot sector type:  Grub 2
   Boot sector info:  Grub 2 is installed in the boot sector of sda5 and
                      looks at sector 84018242 of the same hard drive for
                      core.img, core.img is at this location on /dev/sda and
                      looks on partition #5 for (,msdos5)/grub.
   Operating System:
   Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img


sdb2: ______________________________________________

   File system:       ext2
   Boot sector type:  -
   Boot sector info:
   Operating System:
   Boot files/dirs:   /grub/grub.cfg /grub/core.img

```

---

### Post by wilee-nilee on 2011-04-22
Post the whole bootscript text file.

---

### Post by rpm13 on 2011-04-23
Ok here it is

---

### Post by oldfred on 2011-04-23
I could not get your compressed file to open.

Just post it here and use code tags to make it easier to read.

Code tags are the # in the edit panel above your post. Highlight entire results.txt after copying into post and click on #.
Or click on # then paste between the code tags entered automatically.

---

### Post by rpm13 on 2011-04-23
> **oldfred said:**
> I could not get your compressed file to open.

Just post it here and use code tags to make it easier to read.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 84018242 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for (,msdos5)/grub.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 84018242 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for (,msdos5)/grub.
    Operating System:  Debian GNU/Linux wheezy/sid
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux wheezy/sid
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb14: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb14 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    46,874,623    46,872,576   7 HPFS/NTFS
/dev/sda2          46,874,624    64,452,607    17,577,984  83 Linux
/dev/sda3          64,452,608    83,984,383    19,531,776  83 Linux
/dev/sda4          83,984,384   312,581,807   228,597,424   f W95 Ext d (LBA)
/dev/sda5    *     84,000,768    84,764,671       763,904  83 Linux
/dev/sda6          84,766,720   132,812,799    48,046,080  83 Linux
/dev/sda7         132,814,848   164,063,231    31,248,384  83 Linux
/dev/sda8         164,065,280   179,687,423    15,622,144  83 Linux
/dev/sda9         179,689,472   210,937,855    31,248,384  83 Linux
/dev/sda10        210,939,904   257,812,479    46,872,576  83 Linux
/dev/sda11        257,814,528   292,968,447    35,153,920  83 Linux
/dev/sda12        292,970,496   296,873,983     3,903,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    69,625,709    69,625,647   7 HPFS/NTFS
/dev/sdb2    *     69,634,048    70,043,647       409,600  83 Linux
/dev/sdb3          70,043,648   119,195,647    49,152,000  83 Linux
/dev/sdb4         119,197,695   976,773,119   857,575,425   5 Extended
/dev/sdb5         119,197,696   170,397,695    51,200,000  83 Linux
/dev/sdb6         170,399,744   203,167,743    32,768,000  83 Linux
/dev/sdb7         203,169,792   233,889,791    30,720,000  83 Linux
/dev/sdb8         233,891,840   266,659,839    32,768,000  83 Linux
/dev/sdb9         266,661,888   410,021,887   143,360,000  83 Linux
/dev/sdb10        410,023,936   614,823,935   204,800,000  83 Linux
/dev/sdb11        614,825,984   840,105,983   225,280,000  83 Linux
/dev/sdb12        840,108,032   852,396,031    12,288,000  82 Linux swap / Solaris
/dev/sdb13        852,398,080   874,926,079    22,528,000  83 Linux
/dev/sdb14        874,928,128   914,063,359    39,135,232   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       8d706935-4deb-4ec2-93fc-e808accc75b1   ext4       DataDir160D                   
/dev/sda11       8f11b15d-fe99-4620-8870-54854f1dfd89   ext4       WindowData160D                
/dev/sda12       c2d39104-25e1-43d4-b2ad-7b32a2026e4e   swap                                     
/dev/sda2        4e1dd7c8-627e-4b75-8f71-66b0db2fc12c   ext4       Ubuntu160D                    
/dev/sda3        bbffd2cf-65b3-46a4-bc87-bbcce74286ca   ext2       BSD4.3                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c85b87b3-7b28-4f49-a0f7-cfab152fb320   ext4       Boot160D                      
/dev/sda6        a7940ffc-e896-46a2-8955-ca638d5e9d38   ext4       Home160D                      
/dev/sda7        339fd7af-b06e-45d3-bf21-6e6036f8f9f4   ext4       Debian160D                    
/dev/sda8        16cdfe77-0998-4494-bbf4-869d67e6a02a   ext4       Opt160D                       
/dev/sda9        99c7f4b0-10bd-4b60-8d39-9c126b87a3fb   ext4       Download160D                  
/dev/sda: PTTYPE="dos" 
/dev/sdb10       ce154941-3e09-4819-8e2c-0e9afcc8bdb1   ext4       Download500G                  
/dev/sdb11       43eb2ec3-1b0d-4547-9b85-93c8ff492c3a   ext4       DataDir500G                   
/dev/sdb12       26555b6e-e600-4b14-9263-59d0cdfba56c   swap                                     
/dev/sdb13       fcbc0404-b0d1-48de-98c2-f4f3dc33d411   ext4       Opt500G                       
/dev/sdb14       8CACA408ACA3EAC2                       ntfs       WindowsData                   
/dev/sdb1        A40CED6C0CED39C6                       ntfs                                     
/dev/sdb2        2ff3b4df-2cec-42e0-ac3e-4c165a446189   ext2       Boot500G                      
/dev/sdb3        658119f6-db4e-4980-a054-19f5ec0b0d4a   ext4       Home500G                      
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        f0f0647c-39c9-4624-af1a-46082f9a27c7   ext4       Debian500G                    
/dev/sdb6        a94f07a6-a5da-4029-9933-9181c3e7c5c9   ext4       Ubuntu500G                    
/dev/sdb7        589986ff-2a3d-4384-b3f9-4c42e228b92d   ext4       Linux1                        
/dev/sdb8        fe8d04d2-1e60-4952-9639-fc82063ed28d   ext4       Linux2                        
/dev/sdb9        f0a1fb7f-4c7c-428b-85f9-2042bd898f8d   ext4       Src500G                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb13       /opt                     ext4       (rw,commit=0)
/dev/sdb3        /home                    ext4       (rw,commit=0)
/dev/sdb9        /src                     ext4       (rw,commit=0)
/dev/sdb10       /download                ext4       (rw,commit=0)
/dev/sdb11       /dataDir                 ext4       (rw,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
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
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro   
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro single 
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a40ced6c0ced39c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro resume=/dev/sda12
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro single
	initrd /boot/initrd.img-2.6.32-5-686
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
LABEL=Ubuntu500G /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
#UUID=2ff3b4df-2cec-42e0-ac3e-4c165a446189 /boot           ext2    defaults        0       2
# swap was on /dev/sda12 during installation
UUID=26555b6e-e600-4b14-9263-59d0cdfba56c none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  30.5GB: boot/grub/core.img
  30.5GB: boot/grub/grub.cfg
  30.5GB: boot/initrd.img-2.6.31-14-generic
  30.5GB: boot/vmlinuz-2.6.31-14-generic
  30.5GB: initrd.img
  30.5GB: vmlinuz

============================= sda5/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda15 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,13)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Chainload into GRUB 2
root		(hd0,13)
kernel		/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.32-5-686
root		(hd0,13)
kernel		/vmlinuz-2.6.32-5-686 root=/dev/hda15 ro 
initrd		/initrd.img-2.6.32-5-686

title		Debian GNU/Linux, kernel 2.6.32-5-686 (single-user mode)
root		(hd0,13)
kernel		/vmlinuz-2.6.32-5-686 root=/dev/hda15 ro single
initrd		/initrd.img-2.6.32-5-686

title		Debian GNU/Linux, kernel 2.6.32-3-686
root		(hd0,13)
kernel		/vmlinuz-2.6.32-3-686 root=/dev/hda15 ro 
initrd		/initrd.img-2.6.32-3-686

title		Debian GNU/Linux, kernel 2.6.32-3-686 (single-user mode)
root		(hd0,13)
kernel		/vmlinuz-2.6.32-3-686 root=/dev/hda15 ro single
initrd		/initrd.img-2.6.32-3-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#Trying ubunti kernel rpm: 20-10-07
title		Ubuntu kernel imported
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic.bak
savedefault

============================= sda5/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c85b87b3-7b28-4f49-a0f7-cfab152fb320
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c85b87b3-7b28-4f49-a0f7-cfab152fb320
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/vmlinuz-2.6.32-5-686 root=UUID=339fd7af-b06e-45d3-bf21-6e6036f8f9f4 ro  
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-5-686
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set c85b87b3-7b28-4f49-a0f7-cfab152fb320
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/vmlinuz-2.6.32-5-686 root=UUID=339fd7af-b06e-45d3-bf21-6e6036f8f9f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a40ced6c0ced39c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
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

=================== sda5: Location of files loaded by Grub: ===================


  43.0GB: grub/core.img
  43.0GB: grub/grub.cfg
  43.0GB: grub/menu.lst
  43.0GB: grub/stage2
  43.0GB: initrd.img-2.6.32-5-686
  43.0GB: vmlinuz-2.6.32-5-686

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=339fd7af-b06e-45d3-bf21-6e6036f8f9f4 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=339fd7af-b06e-45d3-bf21-6e6036f8f9f4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2	/mnt/win           vfat    rw,user        0       2
#UUID=46BF-45F6	/mnt/win           vfat    rw,user        0       2
LABEL=Debian160D	/               ext4    defaults,errors=remount-ro 0       1
LABEL=Boot160D	/boot           ext4    defaults        0       2
LABEL=Opt160D	/opt		ext4	defaults	0	2
LABEL=Home160D	/home           ext4    defaults        0       2
#LABEL=Src500G	/src		ext4    defaults        0       2
LABEL=Download160D	/download	ext4    defaults        0       2
LABEL=DataDir160D	/dataDir	ext4    defaults        0       2
UUID=c2d39104-25e1-43d4-b2ad-7b32a2026e4e      none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1	/media/usb	vfat	rw,user,noauto

=================== sda7: Location of files loaded by Grub: ===================


  77.3GB: boot/grub/core.img
  77.3GB: boot/grub/grub.cfg
  77.3GB: boot/grub/stage2
  74.1GB: boot/initrd.img-2.6.32-5-686
  77.3GB: boot/vmlinuz-2.6.32-5-686
  74.1GB: initrd.img
  77.3GB: vmlinuz

============================= sdb2/grub/grub.cfg: =============================

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
set root=(hd0,6)
search --no-floppy --label --set Debian500G
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
menuentry "Debian 500 handedited" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --label --set Debian500G
	linux	/vmlinuz root=LABEL=Debian500G ro
	initrd	/initrd.img
}


menuentry "Debian 160 handedited" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --label --set Debian160D
	linux	/vmlinuz root=LABEL=Debian160D ro
	initrd	/initrd.img
}

menuentry "Debian 500->160 load configfile" {
	search --set --label Debian160D
	configfile boot/grub/grub.cfg
}
menuentry "Debian 500->500 configfile" {
	search --set --label Debian500G
	configfile /boot/grub/grub.cfg
}
menuentry "Ubuntu 500->500 configfile" {
	search --set --label Ubuntu500G
	configfile /boot/grub/grub.cfg
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2ff3b4df-2cec-42e0-ac3e-4c165a446189
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2ff3b4df-2cec-42e0-ac3e-4c165a446189
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

menuentry "Windows NT/2000/XP (on /dev/sda1 (80G))" {
        insmod part_msdos
        insmod ntfs
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set a40ced6c0ced39c6
        drivemap -s (hd0) (hd1)
        chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb1 (500G))" {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set a40ced6c0ced39c6
        drivemap -s (hd0) $root
        chainloader +1
}

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb2: Location of files loaded by Grub: ===================


  35.7GB: grub/core.img
  35.7GB: grub/grub.cfg
  35.6GB: initrd.img-2.6.31-14-generic
  35.6GB: vmlinuz-2.6.31-14-generic

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda15 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,13)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Chainload into GRUB 2
root		(hd0,13)
kernel		/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.32-5-686
root		(hd0,13)
kernel		/vmlinuz-2.6.32-5-686 root=/dev/hda15 ro 
initrd		/initrd.img-2.6.32-5-686

title		Debian GNU/Linux, kernel 2.6.32-5-686 (single-user mode)
root		(hd0,13)
kernel		/vmlinuz-2.6.32-5-686 root=/dev/hda15 ro single
initrd		/initrd.img-2.6.32-5-686

title		Debian GNU/Linux, kernel 2.6.32-3-686
root		(hd0,13)
kernel		/vmlinuz-2.6.32-3-686 root=/dev/hda15 ro 
initrd		/initrd.img-2.6.32-3-686

title		Debian GNU/Linux, kernel 2.6.32-3-686 (single-user mode)
root		(hd0,13)
kernel		/vmlinuz-2.6.32-3-686 root=/dev/hda15 ro single
initrd		/initrd.img-2.6.32-3-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#Trying ubunti kernel rpm: 20-10-07
title		Ubuntu kernel imported
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic.bak
savedefault

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro  resume=/dev/sda12
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set a40ced6c0ced39c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2	/mnt/win           vfat    rw,user        0       2
#UUID=46BF-45F6	/mnt/win           vfat    rw,user        0       2
LABEL=Debian500G	/               ext4    defaults,errors=remount-ro 0       1
#LABEL=Boot500G	/boot           ext2    defaults        0       2
LABEL=Opt500G	/opt		ext4	defaults	0	2
LABEL=Home500G	/home           ext4    defaults        0       2
LABEL=Src500G	/src		ext4    defaults        0       2
LABEL=Download500G	/download	ext4    defaults        0       2
LABEL=DataDir500G	/dataDir	ext4    defaults        0       2
UUID=26555b6e-e600-4b14-9263-59d0cdfba56c      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1	/media/usb	vfat	rw,user,noauto

=================== sdb5: Location of files loaded by Grub: ===================


  83.3GB: boot/grub/core.img
  65.4GB: boot/grub/grub.cfg
  83.3GB: boot/grub/menu.lst
  83.3GB: boot/grub/stage2
  66.9GB: boot/initrd.img-2.6.32-5-686
  62.2GB: boot/vmlinuz-2.6.32-5-686
  66.9GB: initrd.img
  62.2GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
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
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro   
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set a94f07a6-a5da-4029-9933-9181c3e7c5c9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a94f07a6-a5da-4029-9933-9181c3e7c5c9 ro single 
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
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a40ced6c0ced39c6
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "'Debian GNU/Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro resume=/dev/sda12
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "'Debian GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os { (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f0f0647c-39c9-4624-af1a-46082f9a27c7
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=f0f0647c-39c9-4624-af1a-46082f9a27c7 ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
LABEL=Ubuntu500G /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
#UUID=2ff3b4df-2cec-42e0-ac3e-4c165a446189 /boot           ext2    defaults        0       2
# swap was on /dev/sda12 during installation
UUID=26555b6e-e600-4b14-9263-59d0cdfba56c none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  89.7GB: boot/grub/core.img
  89.8GB: boot/grub/grub.cfg
  89.8GB: boot/initrd.img-2.6.31-14-generic
  89.8GB: boot/vmlinuz-2.6.31-14-generic
  89.8GB: initrd.img
  89.8GB: vmlinuz


```

---

### Post by oldfred on 2011-04-23
Did you manually edit grub.cfg? From your grub2 grub.cfg you seem to have two entires in sda5, I do not think that is normal even with separate /boot?:

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c85b87b3-7b28-4f49-a0f7-cfab152fb320

For standard desktops I find the separate /boot just adds to the difficulty of keeping partitions separate and adds to the repair issues.

You have boot flags on Linux partitions. Grub does not use boot flag. Some BIOS need one. But windows has to have a boot flag on the primary NTFS partition it boots from. Only required if you directly boot windows or want to repair windows.

You have grub legacy & grub2 in some partitions. Sometimes that causes confusion and we normally chroot & uninstall both and cleaning reinstall grub2.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You have installed grub2 to partitions. That can lead to long term issues if you are using that to chainload. Otherwise it does not matter as the PBR - partition boot sector is not used by grub.

---

### Post by rpm13 on 2011-04-23
> **oldfred said:**
> 
You have installed grub2 to partitions. That can lead to long term issues if you are using that to chainload. Otherwise it does not matter as the PBR - partition boot sector is not used by grub.

I did this when nothing worked and dpkg-reconfigure grub-pc said it is best to install grub to all partitions.

It still did not work :-k
How do I remove it?

> 
You have boot flags on Linux partitions. Grub does not use boot flag. Some BIOS need one. But windows has to have a boot flag on the primary NTFS partition it boots from. Only required if you directly boot windows or want to repair windows.

Similar to above. Added it recently in my attempts to get it to work.
However the message: No bootable device
suggests (to me) that however properly grub is installed bios is not seeing it like that.  Obviously Ive fished around in BIOS (intel board) to see if something needs to be enabled but dont see anything obvious.

> 
Did you manually edit grub.cfg? 

Yes the idea was to replicate the disks and then again move to an automated grub.cfg
Ive done it many times before successfully...

> 
From your grub2 grub.cfg you seem to have two entires in sda5, I do not think that is normal even with separate /boot?:

Is it the recovery boot you are referring to? Or something else?

> 
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 339fd7af-b06e-45d3-bf21-6e6036f8f9f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c85b87b3-7b28-4f49-a0f7-cfab152fb320

For standard desktops I find the separate /boot just adds to the difficulty of keeping partitions separate and adds to the repair issues.

Yes I see your point
I like a separate boot when there are a number of different OSes multibooting and they tread on each other's toes when upgrading.
I asked this on the grub list [link]("http://lists.gnu.org/archive/html/help-grub/2011-01/msg00017.html")

Is there is something suspicious in the above fragment?

> 
You have grub legacy & grub2 in some partitions. Sometimes that causes confusion and we normally chroot & uninstall both and cleaning reinstall grub2.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Ok I'll attend to that.

Thanks.

---

### Post by oldfred on 2011-04-23
If the error is no bootable device on an Intel board that is because the boot flag is not on a primary partition. Intel must only think windows is booted although Lilo also uses the boot flag.

I do not propose having just one boot, but leaving the boot inside the root partition. Yes having one boot partition and attempting to install multiple system into that one is a problem.

---

### Post by rpm13 on 2011-04-23
> **oldfred said:**
> If the error is no bootable device on an Intel board that is because the boot flag is not on a primary partition. Intel must only think windows is booted although Lilo also uses the boot flag.

Thanks -- That did it (putting on a bootable flag on a spurious partition :D 

Anyhow I think that that should be reported as a bug somewhere....

Grub-pc maybe?
Given that it says installation was successful -- no problem etc but that is not so

> 
I do not propose having just one boot, but leaving the boot inside the root partition. Yes having one boot partition and attempting to install multiple system into that one is a problem.

---

### Post by oldfred on 2011-04-24
Have you tried booting from both drives. The chroot uninstall & reinstall should make it bootable. 

Do you get any error messages, grub rescue, boot menu and then nothing. Or if only one system found initially it will not show menu unless you hold shift key down from BIOS until menu appears. Then black screen is often video issue.

If you still think it is a boot and not video repost boot script to see what has changed.

---

### Post by rpm13 on 2011-04-24
> **oldfred said:**
> Have you tried booting from both drives. The chroot uninstall & reinstall should make it bootable. 

Yes they are both bootable as long as a primary/extended partition is marked bootable

> 
Do you get any error messages, grub rescue, boot menu and then nothing. Or if only one system found initially it will not show menu unless you hold shift key down from BIOS until menu appears. Then black screen is often video issue.

If you still think it is a boot and not video repost boot script to see what has changed.

??? Video???
I repeat its working (thanks to your post :D ) as long as a primary/extended partition is marked bootable

---

### Post by oldfred on 2011-04-24
Somewhere I missed it was working. Glad to hear it is solved.

---

