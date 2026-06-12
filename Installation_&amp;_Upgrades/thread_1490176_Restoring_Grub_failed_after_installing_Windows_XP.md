---
title: "Restoring Grub failed after installing Windows XP"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by jackflamer on 2010-05-21
Hi All, I am pretty new to ubuntu, and not sure if this question has been solved by anyone, I tried search this forum, but didn't find enough information. The closest thread I found here was this one:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

As I could not solve my problem by searching the forum, I post my problem here hoping someone can help, thanks in advance.

Here is my situation, I have installed Ubuntu 9.04 a few days ago with an old Live CD, after running it pretty well, I upgraded it to 9.10 with the online update tool. (I guess this makes sure I was using Grub 1, the legacy Grub). After updated to 9.10, I installed a Windows XP on my hard drive, obviously, it wiped off my Grub from the MBR. So I tried to restore the Grub back to the MBR, but failed, please see below:

I first run the fdisk

```

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1bde1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    b  W95 FAT32
/dev/sda2            6080       60801   439554465    f  W95 Ext'd (LBA)
/dev/sda3           12750       25497   102398278+   b  W95 FAT32
/dev/sda5   *        6080       12401    50781402   83  Linux
/dev/sda6           12402       12749     2795278+  82  Linux swap / Solaris
/dev/sda7           25498       38245   102398278+   b  W95 FAT32
/dev/sda8           38246       60801   181181038+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

```Then tried run grub commands to restore the grub to MBR, but failed with the following error message:

```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 
 (hd0,5)

grub> root (hd0,5)          

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/g
rub/menu.lst"... failed

Error 12: Invalid device requested

grub> 



```

Thank you again, and any suggestion is welcomed!

---

### Post by wilee-nilee on 2010-05-21
Post this script in code tags it will give the details that are needed. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also tell us what is going on when you try to boot into Ubuntu or XP.

---

### Post by hansdown on 2010-05-21
Welcome to the forum jackflamer.

It appears, that you have 2 boot flags, (*).

I'm trying to remember how to edit this.

---

### Post by wilee-nilee on 2010-05-21
> **hansdown said:**
> Welcome to the forum jackflamer.

It appears, that you have 2 boot flags, (*).

I'm trying to remember how to edit this.

That is a obvious problem but there are others lets see the bootscript before we suggest fixes blindly. ;)

---

### Post by jackflamer on 2010-05-21
Wow! Thank you all quick reply, here is my boot script , also, when I try to boot the computer, it loads the windows ntloader, and give my 2 options, first is the windows XP, second it something called " unrecognizable operating system on C:" , but this option can't load ubuntu.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe1bde1bd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    97,659,134    97,659,072   b W95 FAT32
/dev/sda2          97,659,135   976,768,064   879,108,930   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5    *     97,659,261   199,222,064   101,562,804  83 Linux
/dev/sda6         199,222,128   204,812,684     5,590,557  82 Linux swap / Solaris
/dev/sda7         409,609,368   614,405,924   204,796,557   b W95 FAT32
/dev/sda8         614,405,988   976,768,064   362,362,077   b W95 FAT32
/dev/sda3         204,812,748   409,609,304   204,796,557   b W95 FAT32

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        86DB-626D                              vfat       WINXPSP3                      
/dev/sda3        4AD0-B38F                              vfat       DATA                          
/dev/sda5        869141f8-0579-49b2-ae9d-2f7275d656d8   ext3                                     
/dev/sda6        76ef528b-1a71-4272-a228-e85651552805   swap                                     
/dev/sda7        E072-1BD9                              vfat       DOWNLOAD0                     
/dev/sda8        95A1-67DE                              vfat       DOWNLOAD1                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\linux = "Ubunutu" 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN

## default grub root device
## e.g. groot=(hd0,0)
# groot=869141f8-0579-49b2-ae9d-2f7275d656d8

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

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.28-18-generic
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 ro locale=zh_CN  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        869141f8-0579-49b2-ae9d-2f7275d656d8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=869141f8-0579-49b2-ae9d-2f7275d656d8 /               ext3    relatime,errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=86DB-626D  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda9 during installation
UUID=76ef528b-1a71-4272-a228-e85651552805 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



=================== sda5: Location of files loaded by Grub: ===================


  85.5GB: boot/grub/menu.lst
  85.6GB: boot/grub/stage2
  80.6GB: boot/initrd.img-2.6.28-11-generic
  73.7GB: boot/initrd.img-2.6.28-18-generic
  80.6GB: boot/initrd.img-2.6.31-21-generic
  80.6GB: boot/vmlinuz-2.6.28-11-generic
  80.7GB: boot/vmlinuz-2.6.28-18-generic
  80.7GB: boot/vmlinuz-2.6.31-21-generic
  80.6GB: initrd.img
  73.7GB: initrd.img.old
  80.7GB: vmlinuz
  80.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by hansdown on 2010-05-21
> **wilee-nilee said:**
> That is a obvious problem but there are others lets see the bootscript before we suggest fixes blindly. ;)

My sight is quite good, thankyou.

---

### Post by wilee-nilee on 2010-05-21
> **hansdown said:**
> My sight is quite good, thankyou.

Excellent then read the bootscript.;) There are some anomalies in it.

---

### Post by jackflamer on 2010-05-21
By the way, when I tried to solved the problem myself (already found the issue), I tried to copy the first block of my ubuntu partition using WinHex, and saved to a file on the C: drive's root directory called linux, and modified the boot.ini using that file, but it didn't work. Apparantely, WinHEX showed me that there was nothing on the first block of my ubuntu partition, all "00 ", but I just tried.

---

### Post by hansdown on 2010-05-21
> **wilee-nilee said:**
> Excellent then read the bootscript.;) There are some anomalies in it.

Then I shall exit, stage left.

---

### Post by wilee-nilee on 2010-05-21
So OP what is happening now if you try to boot anything?

---

### Post by jackflamer on 2010-05-21
Now, if I boot the computer, I can boot into Windows XP using NT Loader with now problem, but I have no way to boot into Ubuntu. Obviously, the Grub has not yet been restored.

---

### Post by jackflamer on 2010-05-21
I appreciate all your kindness and help, thanks! This is a great community!

---

### Post by oldfred on 2010-05-21
This is a problem and two boot flags may be a problem but I think windows only sees boot flags on primary partitions. You still should delete the flag on sda5. You can use gparted, right click on partition and manage flags, or use Disk Utility. Or command line.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

Bigger problem with partitions. They cannot overlap. Your manual edit messed up somehow.
/dev/sda2 overlaps with /dev/sda3

Sometimes just rewriting it will fix it. Sometimes it make no changes:
You can reorder the partition with fdisk, just type single letters:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk

---

### Post by wilee-nilee on 2010-05-21
The sda2 and sda3 overlap was the first thing I noticed and was going to suggest a more knowledgeable user will be more helpful, and here you are; a much more experienced user. ;)

---

### Post by jackflamer on 2010-05-22
> **oldfred said:**
> This is a problem and two boot flags may be a problem but I think windows only sees boot flags on primary partitions. You still should delete the flag on sda5. You can use gparted, right click on partition and manage flags, or use Disk Utility. Or command line.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

Bigger problem with partitions. They cannot overlap. Your manual edit messed up somehow.
/dev/sda2 overlaps with /dev/sda3

Sometimes just rewriting it will fix it. Sometimes it make no changes:
You can reorder the partition with fdisk, just type single letters:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk


Thank you OldFred, the overlapping seems causing my problem, I did what you suggested, but seemed I had only fixed the "2 boot flags" issue, but I could not reorder the partition overlap problem:

```

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8
======================
Can't have overlapping partitions.
Can't have overlapping partitions.
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1bde1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    b  W95 FAT32
/dev/sda2            6080       60801   439554465    f  W95 Ext'd (LBA)
/dev/sda3           12750       25497   102398278+   b  W95 FAT32
/dev/sda5   *        6080       12401    50781402   83  Linux
/dev/sda6           12402       12749     2795278+  82  Linux swap / Solaris
/dev/sda7           25498       38245   102398278+   b  W95 FAT32
/dev/sda8           38246       60801   181181038+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo sfdisk -A1 /dev/sda
Done

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1bde1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    b  W95 FAT32
/dev/sda2            6080       60801   439554465    f  W95 Ext'd (LBA)
/dev/sda3           12750       25497   102398278+   b  W95 FAT32
/dev/sda5            6080       12401    50781402   83  Linux
/dev/sda6           12402       12749     2795278+  82  Linux swap / Solaris
/dev/sda7           25498       38245   102398278+   b  W95 FAT32
/dev/sda8           38246       60801   181181038+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): r

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1bde1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    b  W95 FAT32
/dev/sda2            6080       60801   439554465    f  W95 Ext'd (LBA)
/dev/sda3           12750       25497   102398278+   b  W95 FAT32
/dev/sda5            6080       12401    50781402   83  Linux
/dev/sda6           12402       12749     2795278+  82  Linux swap / Solaris
/dev/sda7           25498       38245   102398278+   b  W95 FAT32
/dev/sda8           38246       60801   181181038+   b  W95 FAT32

Command (m for help): v
5539 unallocated sectors

Command (m for help): q

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8
======================
Can't have overlapping partitions.
ubuntu@ubuntu:~$ 


```

The only thing I haven't done is to save the changes within fdisk as it told me "Nothing to do. Ordering is correct already." 

Do I still need to use the "W" command to write to disk?

Thanks again!

---

### Post by oldfred on 2010-05-22
I would try the write just to see if it corrects the end points or not. It may not make any changes. 

Normally this would be to reorder partitions, I am not sure why anyone would but thats what it is for. When partitions get renumbered grub often has to be reinstalled, but you are not changing anything, just trying to get to to do the recalculations automatically. 

IF that does not work I would look at testdisk. I have not used it so I do not know but it does many thing.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by jackflamer on 2010-05-22
Dear All, I have solved my problem, special thanks to OldFred! Also, I appreciate all of your inputs!

Yes, by downloading and running the TestDisk, the problem solved pretty smoothly.

1. run the TestDisk tool
2. Choosing [Analyze ] to check the partition table
3. It finds my partition table has some conflicts, actually, 2 partitions are duplicated ( overlapping)
4. Choose [Quick Search] to find the correct partition table
5. Choose [Write] to rewrite the partition table with correct information
6. Restart the computer

After these above process, I can restore the Grub Legacy to the MBR following this howto:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

After that, I can boot into Ubuntu again, but still need to modify the /boot/grub/menu.lst to add the windows boot option which is also indicated in this above mentioned howto.

And now, I can dual boot into both Ubuntu and Windows using Grub.

Thanks again, and Ubuntu is great! This community rocks!

---

### Post by oldfred on 2010-05-22
Glad you got it to work.:)

---

### Post by hansdown on 2010-05-23
Nice work oldfred.

Glad you got things sorted jackflamer.

---

