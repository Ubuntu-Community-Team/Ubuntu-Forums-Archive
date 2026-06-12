---
title: "unbootable hot mess with 2 hdd"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by toefungus on 2011-09-18
i have made a huge mess of my desktop and can only boot from the live cd now.  the story from the beginning:

as of yesterday, i had a working dual-boot winxp and ubuntu-7 running on my 250 gb hdd.  the 2 os's lived on separate partitions.  both partitions were running out of space, so i bought a 1 tb hdd which i physically installed without problems.

the 250 gb hdd looks something like this:
```
sda1     /windows     NTFS     20 gb
sda2     /            ext3     20 gb
sda3     /home        ext3    200 gb
sda4     *swap*       swap      1 gb
```

i planned to make several partitions on the new hdd, back up data into one of the partitions, and then install winxp and ubuntu-11 on the remaining available partitions.  i had envisioned the boot menu letting me choose between 2 versions of xp and 2 versions of ubuntu (ie dual bootable win/ubuntu on each hdd).

i accidentally threw in the winxp cd first, and i realized i needed to run gparted first instead, so i exited out of winxp installation. this caused my old winxp to stop fully booting: "insufficient api resources exist to complete the api" right after the splash screen and hitting ok would just reboot ad infinitum.  ubuntu-7 was still booting fine at this point. no biggie, i thought, i'll just run gparted on the new disk and i can worry about the old disk later.

so i run gparted on the 1 tb hdd, using [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) as a template:
```
sde1     NTFS     50 gb     planned for winxp
sde2     ext3      3 gb     "extra" partition
sde3     ext3    100 mb     planned for grub boot
sde5     *swap*    2 gb     planned for swap
sde6     ext4     80 gb     planned for ubuntu-11
sde7     ext3    800 gb     planned for home directory

```
i turn on the boot flag for sde1. i don't know why they didn't enumerate sde4, it doesn't seem to exist.  at this point i have no labels on any of the partitions.

after this i install winxp onto the sde1 partition.  then i try to boot and it says "BOOTMGR is missing, press ctrl-alt-del to restart".  which of course directs me into another infinite reboot loop. i thought maybe i just need to install ubuntu and it will help set up grub, and all will be well.

so then i boot the ubuntu live cd and try to install ubuntu-11.  i tell it to install to sde6, and put the boot partition into sde3.  the installer refuses, then i realize i have to designate the mount point.  so i tell the partitioner to call sde6 "/" and sde7 "/home".  so now ubuntu-11 installs.

i reboot and i still see "BOOTMGR is missing, press ctrl-alt-del to restart".  this is where i am, and i am wary to wade in further and get myself into more trouble.  good news is, i can run the live ubuntu cd and all my files seem intact on the old hdd.

can someone help me out of this mess?  i have no important data on the new 1 tb hdd so i can totally reformat/repartition it if necessary.

and a more specific question:  if i called sde6 "/" and sde7 "/home", what will happen to the old "/" and "/home" (on sda2 and sda3) when i successfully boot into ubuntu-11?> [QUOTE][/QUOTE]

---

### Post by MAFoElffen on 2011-09-18
> **toefungus said:**
> 
so i run gparted on the 1 tb hdd, using [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) as a template:
```
sde1     NTFS     50 gb     planned for winxp
sde2     ext3      3 gb     "extra" partition
sde3     ext3    100 mb     planned for grub boot
sde5     *swap*    2 gb     planned for swap
sde6     ext4     80 gb     planned for ubuntu-11
sde7     ext3    800 gb     planned for home directory

```
> 
 You can have four primary partitions or three primary and one extended.   Logical drives can only be created in an extended partition, and then  you are limited by the number of letters in the alphabet.  You can still  create as many logical drives as you want, you just won't have any more  drive letters available so you would have to start mounting the drives  in/as folders.
I hear the limit on the "MAXIMUM NUMBER of LOGICAL PARTITIONS" of a logical volume in linux is 512... but some still says it's unlimited.

Which means that you are right at your limit on how you have your partitions setup on that drive... That is-- Only if your other partitions are setup as logical partitions in the extended partition.  Do you have 3 primary and one extended?

The partition that you boot Linux from will still have to be marked as bootable.  You said you just marked the XP partition.  Using gparted, move the XP parttiion back one sector and leave that sector unallocated, before you install XP.  That will prevent a lot of issues when trying to do multi-boot.

Here's some other ideas to throw in... Have a home directory, but use an NTFS partition as a Shared DATA Directory.  You can mount in on boot in the fstab, so it's always there for UBUNTU and XP will see it as a lettered drive.  

Another thing might be to organize your 250GB drive as included in that mix...

---

### Post by Hakunka-Matata on 2011-09-18
Welcome;
please post the output of 
```
sudo sfdisk -luS && sudo fdisk -lu
```

---

### Post by toefungus on 2011-09-18
> **MAFoElffen said:**
> I hear the limit on the "MAXIMUM NUMBER of LOGICAL PARTITIONS" of a logical volume in linux is 512... but some still says it's unlimited.

Which means that you are over your limit on how you have your partitions setup on that drive.

Here's some other ideas to throw in... Have a home directory, but use an NTFS partition as a Shared DATA Directory.  You can mount in on boot in the fstab, so it's always there for UBUNTU and XP will see it as a lettered drive.  

Another thing might be to organize your 250GB drive as included in that mix...

to clarify, sde5, sde6, sde7 are all logical partitions under a single extended partition.  am i still over the limit?

---

### Post by toefungus on 2011-09-18
> **Hakunka-Matata said:**
> Welcome;
please post the output of 
```
sudo sfdisk -luS && sudo fdisk -lu
```

```
Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  39070079   39070017   7  HPFS/NTFS
/dev/sda2      39070080  78140159   39070080  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3      78140160 486432134  408291975  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4     486432135 488392064    1959930  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)

Disk /dev/sde: 121601 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1   *      2048 102402047  102400000   7  HPFS/NTFS
/dev/sde2     102402048 108546047    6144000  83  Linux
/dev/sde3     108546048 108750847     204800  83  Linux
/dev/sde4     108752894 1953523711 1844770818   5  Extended
/dev/sde5     108752896 112947199    4194304  82  Linux swap / Solaris
/dev/sde6     112949248 276789247  163840000  83  Linux
/dev/sde7     276791296 1953523711 1676732416  83  Linux

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x324e324d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+   7  HPFS/NTFS
/dev/sda2        39070080    78140159    19535040   83  Linux
/dev/sda3        78140160   486432134   204145987+  83  Linux
/dev/sda4       486432135   488392064      979965   82  Linux swap / Solaris

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000897f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   102402047    51200000    7  HPFS/NTFS
/dev/sde2       102402048   108546047     3072000   83  Linux
/dev/sde3       108546048   108750847      102400   83  Linux
/dev/sde4       108752894  1953523711   922385409    5  Extended
/dev/sde5       108752896   112947199     2097152   82  Linux swap / Solaris
/dev/sde6       112949248   276789247    81920000   83  Linux
/dev/sde7       276791296  1953523711   838366208   83  Linux
```

---

### Post by MAFoElffen on 2011-09-18
> **toefungus said:**
> to clarify, sde5, sde6, sde7 are all logical partitions under a single extended partition.  am i still over the limit?
No... then it's right at the limit...

---

### Post by toefungus on 2011-09-20
> **MAFoElffen said:**
> Using gparted, move the XP parttiion back one sector and leave that sector unallocated, before you install XP.  That will prevent a lot of issues when trying to do multi-boot.

sorry i'm confused about this piece of advice.  currently the xp partition is at the very beginning of the hdd; how can i move it back one sector?  are you saying that i am repartitioning the hdd so that i have 1 unallocated sector prior to the xp partition? and how do i figure out how big one sector is anyhow?

> **MAFoElffen said:**
> You can mount in on boot in the fstab, so it's always there for UBUNTU and XP will see it as a lettered drive.  

i'm not proficient at mounting boot and fstab and am shaky (ie clueless) regarding the mechanics behind these things, which most definitely contributed to the current mess.  i'll try to read more on my own, but in the meantime if you could break it down into n00b terms, i would appreciate it.

---

### Post by toefungus on 2011-09-22
not really sure what is happening on the thread, i posted the output of the requested command, and silence ensued.  is the scenario so awful that it is unfixable and impossible to explain?  or is the solution so obvious and easy that it's not worth responding to?

---

### Post by Hakunka-Matata on 2011-09-22
I'm not really sure what's happening on this thread either.  Maybe you wouldn't mind restating what your goal is, and what is preventing you from going forward.

**Edit:**  Are you still not able to boot normally?

---

### Post by oldfred on 2011-09-22
The chs does not look correct on your sda drive, but drives have not used chs since drive went over 8GB, Is your BIOS set to LBA?

Partitioning on sde looks ok, I do not recommend a separate /boot unless you have a server with RAID or LVM or an old PC that can only boot from the first 137GB.

To see what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by toefungus on 2011-09-23
> **Hakunka-Matata said:**
> I'm not really sure what's happening on this thread either.  Maybe you wouldn't mind restating what your goal is, and what is preventing you from going forward.

**Edit:**  Are you still not able to boot normally?

original goal:  to have 2 hdd, each with dual boot capability, and a boot menu that allows me to choose from 4 different os's.

new temporary goal: to be able to boot into *any* os, to move past the maddening "BOOTMGR is missing" infinite reboot loop.

---

### Post by Hakunka-Matata on 2011-09-23
+1 on oldfred's post# 10.

---

### Post by toefungus on 2011-09-24
pasting results.txt from boot info script prior to rebooting to peek at bios settings...

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sde.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sde2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sde3 
                       and looks at sector 188728808 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive.
    Operating System:  
    Boot files:        

sde4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 242880 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the E:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,070,079    39,070,017   7 NTFS / exFAT / HPFS
/dev/sda2          39,070,080    78,140,159    39,070,080  83 Linux
/dev/sda3          78,140,160   486,432,134   408,291,975  83 Linux
/dev/sda4         486,432,135   488,392,064     1,959,930  82 Linux swap / Solaris


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   102,402,047   102,400,000   7 NTFS / exFAT / HPFS
/dev/sde2         102,402,048   108,546,047     6,144,000  83 Linux
/dev/sde3         108,546,048   108,750,847       204,800  83 Linux
/dev/sde4         108,752,894 1,953,523,711 1,844,770,818   5 Extended
/dev/sde5         108,752,896   112,947,199     4,194,304  82 Linux swap / Solaris
/dev/sde6         112,949,248   276,789,247   163,840,000  83 Linux
/dev/sde7         276,791,296 1,953,523,711 1,676,732,416  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 16.1 GB, 16125001728 bytes
256 heads, 3 sectors/track, 41008 cylinders, total 31494144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          6,160    31,494,143    31,487,984   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AEE49B4AE49B1425                       ntfs       
/dev/sda2        2d165087-444c-445f-8888-3ed7036fc91b   ext3       
/dev/sda3        d0bb9786-e93d-4d89-a2f5-4cfbde4906cb   ext3       
/dev/sda4        e6f0e9b4-2620-49dc-a30a-c1f34b3d9f35   swap       
/dev/sde1        14558024421B648C                       ntfs       
/dev/sde2        cfe6fab5-24fe-4121-a9d8-baba79c486ec   ext3       
/dev/sde3        dc46cee4-088c-4e0d-8083-1d1c3ddd78e3   ext3       
/dev/sde5        ad8961ec-7a0d-42ab-96a7-df5306226706   swap       
/dev/sde6        304224b9-6c36-497b-a37f-4e5c50874cc0   ext4       
/dev/sde7        a45cb4e3-44d4-4cb0-be91-0e9cea2836ff   ext3       
/dev/sdf1        EC96-8C27                              vfat       PATRIOT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/AEE49B4AE49B1425  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/d0bb9786-e93d-4d89-a2f5-4cfbde4906cb ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /media/PATRIOT           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=2d165087-444c-445f-8888-3ed7036fc91b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=d0bb9786-e93d-4d89-a2f5-4cfbde4906cb /home ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=AEE49B4AE49B1425 /windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda4 :
UUID=e6f0e9b4-2620-49dc-a30a-c1f34b3d9f35 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  28.952266693 = 31.087259648   boot/grub/menu.lst                             1
  28.981735229 = 31.118901248   boot/grub/stage2                               2
  28.980705261 = 31.117795328   boot/initrd.img-2.6.22-14-generic              3
  28.941638947 = 31.075848192   boot/initrd.img-2.6.22-14-generic.bak          3
  28.992057800 = 31.129985024   boot/initrd.img-2.6.22-15-generic              5
  28.985130310 = 31.122546688   boot/initrd.img-2.6.22-15-generic.bak          7
  29.004158020 = 31.142977536   boot/initrd.img-2.6.22-16-generic              4
  28.902591705 = 31.033921536   boot/initrd.img-2.6.22-16-generic.bak          3
  28.967636108 = 31.103762432   boot/vmlinuz-2.6.22-14-generic                 2
  28.983375549 = 31.120662528   boot/vmlinuz-2.6.22-15-generic                 2
  28.959819794 = 31.095369728   boot/vmlinuz-2.6.22-16-generic                 2
  29.004158020 = 31.142977536   initrd.img                                     4
  28.992057800 = 31.129985024   initrd.img.old                                 5
  28.959819794 = 31.095369728   vmlinuz                                        2
  28.983375549 = 31.120662528   vmlinuz.old                                    2

=========================== sde6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos6)'
search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos6)'
search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos6)'
	search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=304224b9-6c36-497b-a37f-4e5c50874cc0 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos6)'
	search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=304224b9-6c36-497b-a37f-4e5c50874cc0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos6)'
	search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos6)'
	search --no-floppy --fs-uuid --set=root 304224b9-6c36-497b-a37f-4e5c50874cc0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root AEE49B4AE49B1425
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 7.10, kernel 2.6.22-16-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-16-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
	initrd /boot/initrd.img-2.6.22-16-generic
}
menuentry "Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-16-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
	initrd /boot/initrd.img-2.6.22-16-generic
}
menuentry "Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-15-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
	initrd /boot/initrd.img-2.6.22-15-generic
}
menuentry "Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-15-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
	initrd /boot/initrd.img-2.6.22-15-generic
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=2d165087-444c-445f-8888-3ed7036fc91b ro single
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 7.10, memtest86+ (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 2d165087-444c-445f-8888-3ed7036fc91b
	linux /boot/memtest86+.bin 
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
--------------------------------------------------------------------------------

=============================== sde6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde6 during installation
UUID=304224b9-6c36-497b-a37f-4e5c50874cc0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sde7 during installation
UUID=a45cb4e3-44d4-4cb0-be91-0e9cea2836ff /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e6f0e9b4-2620-49dc-a30a-c1f34b3d9f35 none            swap    sw              0       0
# swap was on /dev/sde5 during installation
UUID=ad8961ec-7a0d-42ab-96a7-df5306226706 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  89.992935181 = 96.629178368   boot/grub/core.img                             1
 114.083091736 = 122.495787008  boot/grub/grub.cfg                             1
  55.683135986 = 59.789312000   boot/initrd.img-2.6.38-8-generic               1
  89.991214752 = 96.627331072   boot/vmlinuz-2.6.38-8-generic                  1
  55.683135986 = 59.789312000   initrd.img                                     1
  89.991214752 = 96.627331072   vmlinuz                                        1

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# Created by generate-pxe-menu! Do NOT edit unless you know what you are doing! 
# Keep those comment "MENU DEFAULT" and "MENU HIDE"! Do NOT remove them.
# Note!!! If "serial" directive exists, it must be the first directive
default vesamenu.c32
timeout 300
prompt 0
noescape 1
MENU MARGIN 5
 MENU BACKGROUND Gsplash.png
# Set the color for unselected menu item and timout message
 MENU COLOR TITLE    1;36;44    #ffffffff #00000000
 MENU COLOR SEL      7;37;40    #FF000000 #FFC0C0C0
 MENU COLOR HOTSEL   1;7;37;40  #FF000000 #FFC0C0C0

# MENU MASTER PASSWD

say **********************************************************************
say GParted.
say Gnome Partition Editor.
say http://gparted.sourceforge.net
say THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK! 
say **********************************************************************

# Allow client to edit the parameters
ALLOWOPTIONS 1

# simple menu title
MENU TITLE http://gparted.sourceforge.net

# Since no network setting in the squashfs image, therefore if ip=frommedia, the network is disabled. That's what we want.
label GParted Live
  MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Default settings)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt  ip=frommedia  nosplash
  TEXT HELP
  * GParted live version: 0.9.0-6. Live version maintainer: Steven Shiau
  * Disclaimer: GParted live comes with ABSOLUTELY NO WARRANTY
  ENDTEXT

MENU BEGIN Other modes of GParted Live
label GParted Live (To RAM)
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (To RAM. Boot media can be removed later)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
  TEXT HELP
  All the programs will be copied to RAM, so you can
  remove boot media (CD or USB flash drive) later
  ENDTEXT

label GParted Live without framebuffer
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Safe graphic settings, vga=normal)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt ip=frommedia nomodeset vga=normal nosplash
  TEXT HELP
  Disable console frame buffer support
  ENDTEXT

label GParted Live failsafe mode
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL GParted Live (Failsafe mode)
  # MENU PASSWD
  kernel /live/vmlinuz
  append initrd=/live/initrd.img boot=live config  noswap noprompt acpi=off irqpoll noapic noapm nodma nomce nolapic nosmp ip=frommedia nomodeset vga=normal nosplash
  TEXT HELP
  acpi=off irqpoll noapic noapm nodma nomce nolapic 
  nosmp nomodeset vga=normal nosplash
  ENDTEXT

MENU END
label local
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL Local operating system in harddrive (if available)
  # MENU PASSWD
  # 2 method to boot local device:
  # (1) For localboot 0, it is decided by boot order in BIOS, so uncomment the follow 1 line if you want this method:
  # localboot 0

  # (2) For chain.c32, you can assign the boot device.
  # Ref: extlinux.doc from syslinux
  # Syntax: APPEND [hd|fd]<number> [<partition>]
  # [<partition>] is optional.
  # Ex:
  # Second partition (2) on the first hard disk (hd0);
  # Linux would *typically* call this /dev/hda2 or /dev/sda2, then it's "APPEND hd0 2"
  #
  kernel chain.c32
  append hd0
  TEXT HELP
  Boot local OS from first hard disk if it's available
  ENDTEXT


# Note! *.bin is specially purpose for syslinux, 
# Do NOT use memtest.bin, use memtest instead of memtest.bin
label memtest
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL Memory test using Memtest86+
  # MENU PASSWD
  kernel /live/memtest
  TEXT HELP
  Run memory test using Memtest86+
  ENDTEXT

--------------------------------------------------------------------------------

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by toefungus on 2011-09-24
> **oldfred said:**
> The chs does not look correct on your sda drive, but drives have not used chs since drive went over 8GB, Is your BIOS set to LBA?

Partitioning on sde looks ok, I do not recommend a separate /boot unless you have a server with RAID or LVM or an old PC that can only boot from the first 137GB.


went through my bios, did not see anywhere in the menus where i could set it to lba.  under the hdd settings in bios, there was "access mode" and "auto" was checked; the alternative to "auto" was "large".  there was also "extended ide drive" under the hdd settings, again "auto" was checked, the alternative to "auto" was "none".

---

### Post by Hakunka-Matata on 2011-09-24
Thanks for running boot_info_script.

Try this, boot to liveCD and run these commands.

```
sudo mount /dev/sde6 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sde
```


[LIST]
[*]Reboot 
[*]Refresh the GRUB 2 menu with sudo update-grub 
[/LIST]

---

### Post by oldfred on 2011-09-24
+1 on Hakunka-Matata's reinstall of grub2's boot loader. You will have choose to boot sde in BIOS or use a one time boot key on BIOS startup (f12 on my system).

Script is not showing any partition issues? LBA is large block allocation, but auto should be ok. I would not change anything now.

Bootmgr missing is a Vista/7 error from the partition boot sector of Windows, but you have XP. If anything an error would be ntldr missing, so where is that error coming from? 

I did use a Win7 repair USB to run chkdsk on my XP install and it did install a Win7 boot sector which I had to change back to an XP boot sector.

---

### Post by toefungus on 2011-09-25
> **oldfred said:**
> +1 on Hakunka-Matata's reinstall of grub2's boot loader. You will have choose to boot sde in BIOS or use a one time boot key on BIOS startup (f12 on my system).

Script is not showing any partition issues? LBA is large block allocation, but auto should be ok. I would not change anything now.

Bootmgr missing is a Vista/7 error from the partition boot sector of Windows, but you have XP. If anything an error would be ntldr missing, so where is that error coming from? 

I did use a Win7 repair USB to run chkdsk on my XP install and it did install a Win7 boot sector which I had to change back to an XP boot sector.

thank you hakuna-matata and oldfred for the suggestions! i'll try reinstalling the boot loader.  one quick question, if i successfully boot into the new hdd, either into xp or into ubuntu-11, how will my old hdd be identified?  in xp, some more lettered drives, correct? but how about unbuntu, for example, how will it distinguish the old hdd "/home" from the new hdd "/home"?  do i need to worry about any of the new os's overwriting data on the old disk?

---

### Post by Hakunka-Matata on 2011-09-25
> **toefungus said:**
> thank you hakuna-matata and oldfred for the suggestions! i'll try reinstalling the boot loader.  one quick question, if i successfully boot into the new hdd, either into xp or into ubuntu-11, how will my old hdd be identified?  in xp, some more lettered drives, correct? but how about unbuntu, for example, how will it distinguish the old hdd "/home" from the new hdd "/home"?  do i need to worry about any of the new os's overwriting data on the old disk?

Linux sees and labels HDDs as devices: /dev/sda, /dev/sdb, etc.  Your Windows drives will be visible and will be / or are in fact the same, either sda1, sda3, or sdb1, something like that.  They won't have any Letter "C:\" designators.

Boot to liveCD, and see for yourself......

---

### Post by oldfred on 2011-09-25
Linux does not auto mount directly, but in Nautilus you will see all your partitions in the left panel. Just by clicking on it, it will mount with a default set of ownership & permissions. It often shows partitions just as 26GB or whatever the size is. I have so many partitions, I cannot keep them straight so I label them. You can use gparted or Disk utility to add labels.

If you want to have it mounted every time you reboot you have to add an entry to fstab. You then can assign any name/label you want (and it does not have to be the same as your label assigned with Disk Utility.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

