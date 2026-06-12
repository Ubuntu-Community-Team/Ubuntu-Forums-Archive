---
title: "Grub 2 help Dual boot with XP on hardware raid"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by LinuxTAd on 2010-03-30
Edit for solve:

1) I removed dmraid as I had never configured it. This does 2 things, removed "probed" additions that would never boot up. And also prevented the automounting of "fakeraid" partitions that I now see after upgrading to Ubuntu 9.10. An example of the "fakeraid" entry located during the probe script: ```
menuentry "Microsoft Windows XP Professional (on /dev/mapper/isw_bhgjhiieaj_Volume11)"
```

2) With the help of oldfred ;) I slowly went through many tests and attempts to find what would work and what would not. This entails a lot of rebooting. Make a backup before you start if you have data you wish to keep.

3) I have many drives but there are 3 HDD's in use for the operating systems.
[LIST=1]
[*]sde is the linux HDD
[*]  sdc and sdd are the "fakeraid" or the Intel hardware raid 0 array (2 500 GIG HDD's +raid 0 array = 1 TB HDD)
[*]  I was able to boot to either one of these systems by changing the primary boot drive in the system bios.
[/LIST]

**My old (legacy) grub menu.lst looked like this:**

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP or Windows Vista
root (hd2,0)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
chainloader +1
makeactive

### END XP/Vista LIST
```

From grub, it would kick me into the Vista bootloader where I had used BCDedit to create an additional entry for XP. It was not pretty, but *it worked*.

**I found that the following worked for me using Grub 2:**

```
sudo nano /etc/grub.d/50_windows
```

and entered:

```
#! /bin/sh -e
echo "Adding Windows XP">&2
cat << EOF
menuentry "Windows XP (loader) (on /dev/sdc)" {
set root=(hd2,1)
drivemap -s (hd2) (hd0)
chainloader +1
}
EOF
```

**notes: **

Grub 2 now starts the numbering of partitions at 1, and not 0 as it did in grub.

**drivemap -s (hd2) ${root}** did not work it just placed "drivemap -s (hd2)" into the generated grub.cfg. *I did obtain at one point an error that stated "to few arguments". 
**insmod ntfs** did not work.
**search --no-floppy --fs-uuid --set #############**  did not work.
**chainloader (hd2,1)+1** did not work.
**40_custom** and the header used in it does some unexpected things to grub.cfg, when a person is not familiar with grub 2, it can be hard to track down.

The best can put it, is that I am still telling Grub2 (just as I did in Grub) exactly where my boot partition is on my windows drive. And then swapping the drives around so windows is "happy" when the baton is passed to its boot loader.

 I believe the major obstacle is that Grub2 is new and there are bits of information scattered all over, and some is not accurate/up to date. Grub 2 is *not* a consistent release across all Linux distros. From my experience alone the differences between Ubuntu 9.04 and 9.10 releases of grub 2 are vast. It is more complicated than grub, it would be easier if the files were all in one folder.



##### Original post #####

First off, if anyone reads this looking to find out if Grub 2 is ready, the answer is NO. It should not even be labeled "Beta" it is "Alpha".

No matter what I did with this upgrade path, the entire process has left me frustrated, and a bit annoyed at Ubuntu. So please keep this in mind :)

Why am I annoyed? Well lack of documentation for starters. Secondly, not having Grub2 Jaunty repos updated, pull the damn application if you are not going to support it (missing bug fixes and modules!) having it in the repos for Jaunty is doing no one any good in its current state. This will certainly ruin the Linux experience for any new people that accidently stumble upon it and install it. Thirdly, (censored) :p.

ok the problem at hand now that my mini rant is over :)

I have 1 HD on SATA II as my Ubutntu Drive. I also have 2 HDDs on SATA II with intel raid, partitions 1,Unallocated(Vista removed due to frustration),3,4. I am able to changed boot drives in Bios and boot into Ubuntu and Windows XP, so as it sits, both OS's work independently of each other.

With Grub (Legacy [insert grumble about changing the name]) here is the menu.lst that my entire system worked as expected on.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP or Windows Vista
root (hd2,0)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
chainloader +1
makeactive

### END XP/Vista LIST
```


```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Windows XP Professional" >&2
menuentry "Windows XP Professional" {
insmod ntfs
set root=(hd2,1)
chainloader (hd2,1)+1
# parttool (hd2,1) boot+ (notes removed.. censored!)
# No work in Grub2 for my sytem drivemap hd0 hd2
# No work in Grub2 for my sytem drivemap hd2 hd0
}

```

Has anyone got this to work and or have any ideas? I would appreciate it some help  :) I end up with a black screen and a cursor blinking at me in the upper left most of the time. I can type e to edit the boot entry and get some error feedback as well (HDD or partition does not exist etc.).

Best regards,
Tom

ps I will post the results of the boot_info_script055.sh that I have found in other threads in the next post.

---

### Post by LinuxTAd on 2010-03-30
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/mapper/isw_bhgjhiieaj_Volume1

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sde6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

isw_bhgjhiieaj_Volume11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

isw_bhgjhiieaj_Volume12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

isw_bhgjhiieaj_Volume13: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe76445f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    68,228,054    68,227,992   7 HPFS/NTFS
/dev/sda2          68,228,055   156,296,384    88,068,330   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x074bda75

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27366e90

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63    78,124,094    78,124,032  83 Linux
/dev/sde2          78,124,095   488,392,064   410,267,970   f W95 Ext d (LBA)
/dev/sde5         480,359,565   488,392,001     8,032,437  82 Linux swap / Solaris
/dev/sde6          78,124,221   480,359,564   402,235,344  83 Linux


Drive: isw_bhgjhiieaj_Volume1 ___________________ _____________________________________________________

Disk /dev/mapper/isw_bhgjhiieaj_Volume1: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb966f2c0

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bhgjhiieaj_Volume11   *             63   209,712,509   209,712,447   7 HPFS/NTFS
/dev/mapper/isw_bhgjhiieaj_Volume12        419,425,020   629,137,529   209,712,510   7 HPFS/NTFS
/dev/mapper/isw_bhgjhiieaj_Volume13        629,137,530 1,953,520,064 1,324,382,535   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_bhgjhiieaj_Volume11 826802746802676F                       ntfs       BOOT                          
/dev/mapper/isw_bhgjhiieaj_Volume12 DCEC187DEC18545C                       ntfs       PROGRAMS                      
/dev/mapper/isw_bhgjhiieaj_Volume13 7ABC161ABC15D20D                       ntfs       STORAGE                       
/dev/sda1        365C173B5C16F4F9                       ntfs       TEMP                          
/dev/sda2        4AA8110CA810F861                       ntfs       mIRC                          
/dev/sda                                                silicon_medley_raid_member                               
/dev/sdb1        4248F91448F90805                       ntfs       MY DOCUMENTS                  
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
/dev/sde1        cb5874c1-9494-4260-9256-dedaf31a71d8   ext4                                     
/dev/sde5        8614e542-cb08-42ac-aeb5-85532ef310cc   swap                                     
/dev/sde6        1407bae0-0e9b-4e75-a683-b00ee0512ebd   ext4                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bhgjhiieaj_Volume1
isw_bhgjhiieaj_Volume11
isw_bhgjhiieaj_Volume12
isw_bhgjhiieaj_Volume13

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde1        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/MYDOCUMENTS       fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/TEMP              fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/mIRC              fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde6        /home                    ext4       (rw,relatime)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=thomas)


================================ sda1/menu.lst: ================================

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
##hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8dd53db3-9cfa-49df-a222-65a93a95a2b4

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8dd53db3-9cfa-49df-a222-65a93a95a2b4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8dd53db3-9cfa-49df-a222-65a93a95a2b4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP or Windows 7 Ultimate
root (hd2,0)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
chainloader +1
makeactive

### END XP/Vista LIST


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: menu.lst

=========================== sde1/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cb5874c1-9494-4260-9256-dedaf31a71d8

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
# howmany=2

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		cb5874c1-9494-4260-9256-dedaf31a71d8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro quiet splash
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		cb5874c1-9494-4260-9256-dedaf31a71d8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
uuid		cb5874c1-9494-4260-9256-dedaf31a71d8
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro quiet splash
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		cb5874c1-9494-4260-9256-dedaf31a71d8
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, memtest86+
uuid		cb5874c1-9494-4260-9256-dedaf31a71d8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP or Windows Vista
root (hd2,0)
map (hd0,0) (hd2,0)
map (hd2,0) (hd0,0)
chainloader +1
makeactive

### END XP/Vista LIST

=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root=(hd4,1)
search --no-floppy --fs-uuid --set cb5874c1-9494-4260-9256-dedaf31a71d8
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd4,1)
	search --no-floppy --fs-uuid --set cb5874c1-9494-4260-9256-dedaf31a71d8
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd4,1)
	search --no-floppy --fs-uuid --set cb5874c1-9494-4260-9256-dedaf31a71d8
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.28-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd4,1)
	search --no-floppy --fs-uuid --set cb5874c1-9494-4260-9256-dedaf31a71d8
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu, Linux 2.6.28-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd4,1)
	search --no-floppy --fs-uuid --set cb5874c1-9494-4260-9256-dedaf31a71d8
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 ro single 
	initrd	/boot/initrd.img-2.6.28-18-generic
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
menuentry "Windows 7 (loader) (on /dev/mapper/isw_bhgjhiieaj_Volume11)" {
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Windows XP Professional" >&2
menuentry "Windows XP Professional" {
insmod ntfs
set root=(hd2,1)
chainloader (hd2,1)+1
# parttool (hd2,1) boot+ (notes removed.. censored!)
# No work in Grub2 for my sytem drivemap hd0 hd2
# No work in Grub2 for my sytem drivemap hd2 hd0
}
### END /etc/grub.d/40_custom ###

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdf1 during installation
UUID=cb5874c1-9494-4260-9256-dedaf31a71d8 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdf6 during installation
UUID=1407bae0-0e9b-4e75-a683-b00ee0512ebd /home           ext4    relatime        0       2
# swap was on /dev/sdf5 during installation
UUID=8614e542-cb08-42ac-aeb5-85532ef310cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
UUID=4248F91448F90805 /media/MYDOCUMENTS ntfs-3g nls=iso8859-1,uid=1000,umask=000,user 0 0
# UUID=C658F87158F8621B /media/TEMP ntfs-3g nls=iso8859-1,uid=1000,umask=000,user 0 0
UUID=365C173B5C16F4F9 /media/TEMP ntfs-3g nls=iso8859-1,uid=1000,umask=000,user 0 0
UUID=4AA8110CA810F861 /media/mIRC ntfs-3g nls=iso8859-1,uid=1000,umask=000,user 0 0
#UUID=2D5F-30C2 /media/TRANSFER vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

=================== sde1: Location of files loaded by Grub: ===================


   4.0GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
   4.0GB: boot/grub/menu.lst
   4.1GB: boot/grub/stage2
  11.1GB: boot/initrd.img-2.6.28-18-generic
  13.9GB: boot/initrd.img-2.6.31-21-generic
   4.1GB: boot/vmlinuz-2.6.28-18-generic
   5.7GB: boot/vmlinuz-2.6.31-21-generic
  13.9GB: initrd.img
  11.1GB: initrd.img.old
   5.7GB: vmlinuz
   4.1GB: vmlinuz.old

====================== isw_bhgjhiieaj_Volume11/boot.ini: ======================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde5

00000000  23 b5 6c 31 67 56 cf 72  a3 18 35 a5 b8 bb 8e 48  |#.l1gV.r..5....H|
00000010  18 b1 8a 4b 4f 69 6c fc  67 94 e8 bc 8f 88 9e 9d  |...KOil.g.......|
00000020  de 76 4e ce 2e ae 59 18  fb 31 7a 68 00 52 45 81  |.vN...Y..1zh.RE.|
00000030  26 9c 0b 5b 6a b4 a4 65  ca 94 c4 87 6a a8 ee 5b  |&..[j..e....j..[|
00000040  b8 8f 22 3e 7a 07 86 a8  dc da 5e a2 d9 13 22 7c  |..">z.....^..."||
00000050  34 3a 53 8e 00 14 85 28  d2 e6 62 f2 79 0e 23 43  |4:S....(..b.y.#C|
00000060  dd d2 ba 38 fb 66 38 a3  72 ae 26 c4 dc c7 2e db  |...8.f8.r.&.....|
00000070  51 5a 13 2d 52 40 e3 de  0c c9 2f c9 9c f2 8f b9  |QZ.-R@..../.....|
00000080  e9 85 4b ec af 41 58 e0  78 84 e4 c6 f3 6c 2b de  |..K..AX.x....l+.|
00000090  70 fc 55 ba 1c ef 31 36  2a 4a 46 65 8d 19 af 1c  |p.U...16*JFe....|
000000a0  83 e0 51 11 3f 63 e2 4e  14 ab dc 2e eb e2 86 80  |..Q.?c.N........|
000000b0  82 98 3c 89 00 1f 69 06  94 a2 87 51 92 85 ab 4e  |..<...i....Q...N|
000000c0  c8 e3 15 4b 2d 61 52 c6  43 da 8b 18 fd c1 17 ba  |...K-aR.C.......|
000000d0  73 ec 50 58 5b 85 0c f7  c0 18 4c 95 ee 62 61 7e  |s.PX[.....L..ba~|
000000e0  75 ae 9c 61 71 8e 47 e1  49 75 1b 7a a3 6c c7 bf  |u..aq.G.Iu.z.l..|
000000f0  a7 24 63 94 7a 28 9b 6c  40 03 83 52 43 dc 18 33  |.$c.z(.l@..RC..3|
00000100  f9 6b c4 97 29 d7 4d 0b  77 9e c4 5a 45 cf 79 40  |.k..).M.w..ZE.y@|
00000110  09 03 9e df 7a ea 9c 48  6c 9e 54 5e 25 a1 90 ab  |....z..Hl.T^%...|
00000120  92 96 e3 ee 51 af 82 c5  af 37 5d 13 65 d4 9a 76  |....Q....7].e..v|
00000130  e6 d6 5a a0 3c 2b fb 56  f7 99 26 a4 44 fe e1 c1  |..Z.<+.V..&.D...|
00000140  c7 73 c7 ca 7a 8f 20 39  9c a1 d9 b7 90 b7 35 e9  |.s..z. 9......5.|
00000150  de 2b b4 0a a4 63 68 21  12 dc ad 66 1f ee 08 ab  |.+...ch!...f....|
00000160  b7 10 20 e3 21 54 87 fe  90 16 a2 63 7d 3b 88 62  |.. .!T.....c};.b|
00000170  37 ce a5 09 b7 ee a4 82  48 de 00 24 0e 5a 69 5c  |7.......H..$.Zi\|
00000180  40 42 67 3e b5 f3 6d 58  5d 3c 9e 36 97 66 f3 06  |@Bg>..mX]<.6.f..|
00000190  bd d4 d5 a9 43 11 35 3d  df 24 d4 ba c6 5f 05 14  |....C.5=.$..._..|
000001a0  04 0c f0 bb 3d d6 26 3e  b5 1b 8e aa 32 bb 0a b6  |....=.&>....2...|
000001b0  cc e8 22 ad bc 26 32 a6  3c ae a2 ba 16 c5 b1 56  |.."..&2.<......V|
000001c0  2c 31 69 6c de 90 81 e1  dd 7c 8f 0d ef e3 e3 eb  |,1il.....|......|
000001d0  a8 b7 d7 0f bf 6b 6c 90  02 82 64 ed bc 49 3f 4d  |.....kl...d..I?M|
000001e0  4d 73 ba 14 75 df f3 a2  8f 34 f7 d4 26 a5 fe fc  |Ms..u....4..&...|
000001f0  ce ab ec f7 ea 1f e2 6c  62 c2 a3 38 53 c5 22 c0  |.......lb..8S.".|
00000200
```

 I "manually" cleaned up a few files left over from the "complete removal" process lol :)

---

### Post by oldfred on 2010-03-30
I would replace your entry with this entry but confirm that I updated partitions and UUID.

menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 4a6077fc6077ed57
    drivemap -s (hd2) ${root}
    chainloader +1
}

Drivemap is the new map command -s means switch.

I also have seen where grub 2 does not work with drives that once were raid members as hidden info still is in the drive. Also grub2 and grub do not coexist well, you must have one or the other. Ubuntu supports raid thru the server install but not without additions on the desktop install.

---

### Post by LinuxTAd on 2010-03-30
oldfred, 

Thank you for taking the time to reply, and again I apologize for my frustration. In retrospect, I did get rather lucky with my ATI drivers with the move to 9.10 in that aside some cosmetic issues at boot, everything is perfect :)

The suggestion above did not work unfortunately, I have tried a few others and am trying not to get "confused" haha.

The initial command you provided gave me the following immediately in terminal:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/mapper/isw_bhgjhiieaj_Volume11
grub-probe: error: no mapping exists for `isw_bhgjhiieaj_Volume11'
done
```

During the boot process (after selecting the new XP entry) I received the following:

```
Error: Invalid Signature 
```

I am now trying to remove portions of the uuid line to see if that eases up on the restrictions or just presents more problems.

The current entry in my 40_custom is:

```
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy #removed to see if that helps
drivemap -s (hd2) ${root}
chainloader +1
}
```

---

### Post by oldfred on 2010-03-30
Your windows is not really in hd2,1 is it. That is my documents?

grub2 found it
/dev/mapper/isw_bhgjhiieaj_Volume11

I do not know raid but someone said you have to download additional raid mods that are usually with the server version. But I just looked and have 3 different raid mods in grub.

This is a question
should the ?
insmod ntfs
be 
insmod raid
I also have raid5rec and a raid6rec as mods in my grub directory.

What entry did the update to grub add?

---

### Post by LinuxTAd on 2010-03-31
> **oldfred said:**
> Your windows is not really in hd2,1 is it. That is my documents?

That is one thing I am seeing, is that the HDD's are having different mappings applied. 

For instance, /dev/mapper/isw_bhgjhiieaj_Volume11 is shown in Gparted however, so are the following HDD's:

[LIST]
[*]SDC
[*]SDD
[/LIST]

SDC and SDD are both 500 GIG HDD's and actually ARE the components that make up /dev/mapper/isw_bhgjhiieaj_Volume1 (isw_bhgjhiieaj_Volume11 is actually BOOT or C: of my raid 0 array as seen in Windows).

However in device.map I see the following:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

So I suppose I am questioning how one can "combine" device.map and dev/mapper. My experience in device.map and dev/mapper is very limited, it just appears that they are two unique systems and are not working in tandem to create an accurate system map.

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb966f2c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13054   104856223+   7  HPFS/NTFS
/dev/sdc2           26109       39162   104856255    7  HPFS/NTFS
/dev/sdc3           39163      121601   662191267+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8150000

Disk /dev/sdd doesn't contain a valid partition table
```

> **oldfred said:**
> grub2 found it
/dev/mapper/isw_bhgjhiieaj_Volume11

I do not know raid but someone said you have to download additional raid mods that are usually with the server version. But I just looked and have 3 different raid mods in grub.

This is a question
should the ?
insmod ntfs
be 
insmod raid
I also have raid5rec and a raid6rec as mods in my grub directory.

What entry did the update to grub add?

It is locating it, I just wish I could debug it so I new exactly what it was doing and what errors it was having when trying to boot.

Within /boot/grub , the following "raid" mods are as follows:

[LIST]
[*]mdraid.mod
[*]raid.mod
[*]raid5rec.mod
[*]raid6rec.mod
[/LIST]

The entry that was entered into /boot/grub/grub.cfg :

```
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
insmod ntfs
set root=(hd2,1)
search --no-floppy #removed to see if that helps
drivemap -s (hd2) ${root}
chainloader +1
}### END /etc/grub.d/40_custom ###
```

And this is the part where I remind everyone that I have all my data backed up so IF I kill my system I can recover ;) Attached is some additional info form Gparted and some of the directories.

Thank you again :)

---

### Post by LinuxTAd on 2010-03-31
I think I may be onto something here. And I just need to perform a few more reboots to test my findings.

Notes:

At boot the lines prior to grub loading that are flashed very quickly are:
echo "Adding Windows XP">&2
cat << EOF  

Or something to that effect, it happens fast.


Using the following in /etc/grub.d/40_custom:

```
#! /bin/sh -e
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Windows XP">&2
cat << EOF
menuentry "Windows XP (loader) (on /dev/sdc)" {
set root=(hd2,1)
drivemap -s (hd2) (hd0)
chainloader +1
}
EOF
```

the new grub.cfg generation is presented as this:

```
Using Generating grub.cfg ...
Found Debian background: Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

And the entry is made in grub.cfg as such:

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

**(Shortened down)**


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

[COLOR="Red"]echo "Adding Windows XP">&2[/COLOR]
[COLOR="red"]cat << EOF[/COLOR]
menuentry "Windows XP (loader) (on /dev/sdc)" {
set root=(hd2,1)
drivemap -s (hd2) (hd0)
chainloader +1
}
[COLOR="red"]EOF[/COLOR]

### END /etc/grub.d/40_custom ###
```

You can see the errors it generates, and I know that I obtained this code sample from the internet, from where exactly I do not remember now so, part of the problem is incorrect/incomplete information floating around. Possibly here: [https://wiki.ubuntu.com/Grub2#User-defined Entries]("https://wiki.ubuntu.com/Grub2#User-defined Entries")

In any case, do not add the code (highlighted in red) into any of the script files located in /etc/grub.d witch are used to create grub.cfg. Or at least not in the ones that contain "exec tail -n +3 $0". For some reason (that is beyond me) it yields undesirable effects in the Grub.cfg file as noted above.

As a test you can create your own scripts in /etc/grub.d as sudo user. I created one named 50_windows and also made it executable. within that file I placed the following code:

```
#! /bin/sh -e
echo "Adding Windows XP">&2
cat << EOF
menuentry "Windows XP (loader) (on /dev/sdc)" {
set root=(hd2,1)
drivemap -s (hd2) (hd0)
chainloader +1
}
EOF
```

Running sudo update-grub yielded the following:

```
Generating grub.cfg ...
Found Debian background: Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found memtest86+ image: /boot/memtest86+.bin
Adding Windows XP
done
```

and resulted in the following entry in the grub.cfg file:

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

**(Shortened down)**


### BEGIN /etc/grub.d/50_windows ###
menuentry "Windows XP (loader) (on /dev/sdc)" {
set root=(hd2,1)
drivemap -s (hd2) (hd0)
chainloader +1
}
### END /etc/grub.d/50_windows ###
```

As you can see without the entries in the 40_custom file, the same code is now correctly applied to the brub.cfg file. :KS

---

### Post by LinuxTAd on 2010-03-31
Thank you oldfred! I truly appreciate your help   :popcorn:

---

### Post by oldfred on 2010-03-31
Glad you got it working. 

Sorry I did not make it clear that those extra lines should not be in the file. I have seen them posted but I think that is if you are manually typing from a command line to add the text to a file, but should not be part of the file.

---

