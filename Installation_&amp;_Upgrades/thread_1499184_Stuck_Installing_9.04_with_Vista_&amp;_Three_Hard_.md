---
title: "Stuck Installing 9.04 with Vista &amp; Three Hard Drives"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by cpcpcp on 2010-06-01
My smallest disc has the Vista loader and nothing else but  I cannot select it for Dual Booting in the Ubuntu installation set up only for use as an entire disc  which would delete the Vista Loader. Help Please

This is what I have:-
1st disc - no operating system much data
2nd Disc - empty except for Windows loader
3rd Disc - no operating system much stuff.


My original plan was to give Ubuntu all of the smaller second disc and I deleted everything ready to give it the entire hard disc. 
It was only when I went to install Ubuntu it I found the Vista loader lurking on disc 2 and the only option the install Ubuntu set up gave  me for disc 2 was to use the entire disc (wiping out Vista loader) 
otherwise I could have installed  Ubunbtu  on another disc  - which it reported as having no operating system.

[B]Question A
If I put Ubuntu on disc 1 would I have a dual boot arrangement given that the installer saw no  operating system on that disc ?

Question B
Is there any (simple) way I can install Ubuntu on disc 2 and not loose the Vista loader?
[/B] 

I am installing this version of Ubuntu as it was on the DVD that came with book "Beginning Ubntu Linux" It took me long time to Psych myself up to install it and when I did . . . :(

Chris

---

### Post by pricetech on 2010-06-01
> **cpcpcp said:**
> This is what I have:-
1st disc - no operating system much data
2nd Disc - empty except for Windows loader
3rd Disc - no operating system much stuff.


So where is windows installed ??  You don't show it being on any of your 3 disks.

---

### Post by darkod on 2010-06-01
If you boot ubuntu in live mode, in terminal execute:

sudo fdisk -l (small L)

That will show your disks and partitions. Copy the results here and give us short explanation what is what and where you want ubuntu installed.

Yes, it will give dual boot options regardless on which disk you install it, as long as you have another OS on any of your disks.

---

### Post by cpcpcp on 2010-06-01
the windows "stuff" is on disc 1
It is the Vista loader that is on disc 2

---

### Post by cpcpcp on 2010-06-02
> **darkod said:**
> If you boot ubuntu in live mode, in terminal execute:

sudo fdisk -l (small L)

That will show your disks and partitions. Copy the results here and give us short explanation what is what and where you want ubuntu installed.

Yes, it will give dual boot options regardless on which disk you install it, as long as you have another OS on any of your disks.

[SIZE=3]I am willing but in Ubuntu how do I copy the output of the command to a file I post here?
I am new to Ubuntu remember:confused:
[/SIZE]

---

### Post by darkod on 2010-06-02
Run that command in terminal and the output it gives just copy/paste as simple text. Select the text in terminal, Edit-Copy, open the forum and Paste here.
It's better if it's in CODE tags but no problem if it isn't, lets not complicate things. :)

---

### Post by cpcpcp on 2010-06-04
> **darkod said:**
> Run that command in terminal and the output it gives just copy/paste as simple text. Select the text in terminal, Edit-Copy, open the forum and Paste here.
It's better if it's in CODE tags but no problem if it isn't, lets not complicate things. :)

Here you are 


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2270ae87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2270ae82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7af1f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1973 MB, 1973420032 bytes
60 heads, 59 sectors/track, 1088 cylinders
Units = cylinders of 3540 * 512 = 1812480 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1089     1927100+   6  FAT16

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa84926ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       38914   312568832    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

**w[SIZE=3]hat I wanted to do was install ubuntu[/SIZE]**[SIZE=3] on the 80gb disc but when I tried to do that ( having deleted all) the installer reports that disc as having the hidden files comprising the Vista loader and gives me the otion of deleting everything to install ubuntu rather than just a partition with ubuntu  in it. Only on teh fisrt disc can I put a Ubuntu partition.
It is the first disc that has all teh Vista system files etc, it is just that the Vista loader that has gone on the 80gb disc. I guess they did that when teh machine was put together as it was the old (IDE) disc from my former machine and the new ones are SATA disc - just guessing here you understand.

So if have been told that that if I put Ubuntu in a partion on the first disc it will realise that there is also a Vista system on board and offer me dual boot. I guess I could do this (but I am nervous) and I really wanted to put it on the old small disc[/SIZE].

Have I explained myself OK?
(The disc at the end is a USB hard drive) 

Chris

---

### Post by darkod on 2010-06-04
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, [COLOR=Red]9729[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7af1f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        [COLOR=Red]9729[/COLOR]    78148161    c  W95 FAT32 (LBA)

It only offered to delete the whole disk because even though you have only vista boot files on that disk, the fat32 partition is taking the whole disk. Ubuntu needs unallocated (unpartitioned) space on the disk to set up its own filesystem, it doesn't work on fat32/ntfs.

Boot your vista and check how much space is used on the 80GB disk. It should be very little, even less than 100MB. If that is correct, open Disk Management and shrink the partition on that 80GB disk to 200MB. Leave all the rest of the disk as unallocated.

Boot vista few times, it might want to do some disk checks.

After that start the ubuntu installer again, and this time after selecting the 80GB disk, in step 4 you should have the option Use Largest Available Free space. That will install ubuntu inside the unallocated space you left on the disk. In this step also note down the name of the disk, it might be /dev/sdc as in the fdisk results, or maybe different.
In the last screen of the installer, before clicking Install, click on Advanced and check where the bootloader (grub2) will go. It should be the same disk name, and no number in it. For example, /dev/sdc in our example. Grub2 should go to the MBR of the same disk, just make sure you double check. When you have multiple disks it can go to another one which is not big problem, but sometimes can create complications.

---

### Post by cpcpcp on 2010-06-04
[SIZE=3]Wow Dorkod - a quick reply and I shall follow your plan in day or so and let you know how things go.

A worry in my mind is that both times I ran Ubunyu from the cd/dvd the machine siezed and had to be fixed by turning it off- even ctrl-alt-del did not work.

hey ho onward and upwards.:)

Chris
[/SIZE]

---

### Post by cpcpcp on 2010-06-05
> 
**=darkod;9411214**
Boot your vista and check how much space is used on the 80GB disk. It should be very little, even less than 100MB. If that is correct, open Disk Management and shrink the partition on that 80GB disk to 200MB. Leave all the rest of the disk as unallocated.



[SIZE=2]As Vista's disc manager does not work where there is system stuff and cannot shrink FAT32 partitions I have downloaded and used the Free EASEUS Partion Master firstly to shrink the existing partition (After three automatic restarts it worked - Phew) secondly to make the remaining stuff in to a large logical NTFS partition. 
That also worked and now I have drive U ready for Ubuntu.[/SIZE]

Later I will install Ubuntu so fingers crossed please

---

### Post by darkod on 2010-06-05
> **cpcpcp said:**
> [SIZE=2] secondly to make the remaining stuff in to a large logical NTFS partition. 
[/SIZE]

I hope you didn't create ntfs partition on that disk planned for ubuntu on it. Ubuntu doesn't install on ntfs, linux works on its own filesystem. I already said that, it needs unallocated space not belonging to any partition. You won't be able to install it on ntfs.

---

### Post by cpcpcp on 2010-06-06
getting there - just won't boot Ubuntu

Which is a problem


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2270ae87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2270ae82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7af1f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         714     5735173+   b  W95 FAT32
/dev/sdc2             715        9729    72412987+   5  Extended
/dev/sdc5             715        9356    69416833+  83  Linux
/dev/sdc6            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 1973 MB, 1973420032 bytes
60 heads, 59 sectors/track, 1088 cylinders
Units = cylinders of 3540 * 512 = 1812480 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1089     1927100+   6  FAT16

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa84926ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       38914   312568832    7  HPFS/NTFS

---

### Post by oldfred on 2010-06-06
With multiple drives you have to use the advance button on the last partition install screen to choose where to install grub. It probalby installed to sda. and you are booting thru another drive. You can try booting each of the drives to see if one gives you grub or not or post this which will show your entire system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (click on # in edit panel) to make it easier to read when you post the results.txt.

---

### Post by darkod on 2010-06-06
Run the script as oldfred says, just fdisk is not enough info. And for additional info, because the OP sent me a PM (the bad side of PM-ing is that other people don't have the info now), the ubuntu install froze just before the end so I am suspecting grub2 didn't install at all, and just reinstalling to the MBR of /dev/sdc might not be enough.

---

### Post by cpcpcp on 2010-06-06
Thank you both - here are th results.

Would it be easier if I simply deleted using partition manager and started again?


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /bootmgr /boot/bcd /IO.SYS /MSDOS.SYS /COMMAND.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2270ae87

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2270ae82

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7af1f42

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    11,470,409    11,470,347   b W95 FAT32
/dev/sdc2          11,470,410   156,296,384   144,825,975   5 Extended
/dev/sdc5          11,470,473   150,304,139   138,833,667  83 Linux
/dev/sdc6         150,304,203   156,296,384     5,992,182  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1973 MB, 1973420032 bytes
60 heads, 59 sectors/track, 1088 cylinders, total 3854336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                 135     3,854,335     3,854,201   6 FAT16


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa84926ff

Partition  Boot         Start           End          Size  Id System

/dev/sdh1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        26D0908AD09061BB                       ntfs                                     
/dev/sdb1        CEFCFDFBFCFDDDA1                       ntfs                                     
/dev/sdc1        1DF8-203B                              vfat       SEGATE                        
/dev/sdc5        d7c55409-10ad-49e0-9ef0-be668adfe990   ext3                                     
/dev/sdc6        cb50f985-6a6a-4db2-a00a-bd59efcaaa35   swap                                     
/dev/sdd1        0000-0000                              vfat       RICOHDCX                      
/dev/sdh1        38A04BC3A04B867A                       ntfs       320 GB WD Compusolve          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdh1        /media/320 GB WD Compusolve fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/RICOHDCX          vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7c55409-10ad-49e0-9ef0-be668adfe990

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=cb50f985-6a6a-4db2-a00a-bd59efcaaa35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  53.1GB: boot/grub/menu.lst
  53.0GB: boot/grub/stage2
  53.1GB: boot/initrd.img-2.6.28-11-generic
  53.0GB: boot/vmlinuz-2.6.28-11-generic
  53.1GB: initrd.img
  53.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg 
```

---

### Post by darkod on 2010-06-06
OK, the quick fix should be going into BIOS and making /dev/sda, the 250GB disk, first boot option. Your grub1 ended up there.

If that works out fine, you can consider whether you want to move it to /dev/sdc, the 80GB disk.

---

### Post by cpcpcp on 2010-06-06
> **darkod said:**
> OK, the quick fix should be going into BIOS and making /dev/sda, the 250GB disk, first boot option. Your grub1 ended up there.

If that works out fine, you can consider whether you want to move it to /dev/sdc, the 80GB disk.

[CENTER][SIZE=3]Sadly I had [/SIZE]
[SIZE=3]grub loading [/SIZE]
[SIZE=3] followed [/SIZE]
[SIZE=3] by [/SIZE]

[SIZE=3] Error 22[/SIZE][/CENTER]

---

### Post by darkod on 2010-06-06
> **cpcpcp said:**
> [CENTER][SIZE=3]Sadly I had [/SIZE]
[SIZE=3]grub loading [/SIZE]
[SIZE=3] followed [/SIZE]
[SIZE=3] by [/SIZE]

[SIZE=3] Error 22[/SIZE][/CENTER]


Use your 9.04 cd in live mode and follow the instructions here for 9.04:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you follow the instructions for 9.04.

That should reinstall grub1 to the MBR of /dev/sdc. When you reboot also go into BIOS and make /dev/sdc, the 80GB disk, first in boot order because with that procedure grub1 should install on it.

---

### Post by cpcpcp on 2010-06-06
> **darkod said:**
> Use your 9.04 cd in live mode and follow the instructions here for 9.04:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you follow the instructions for 9.04.

That should reinstall grub1 to the MBR of /dev/sdc. When you reboot also go into BIOS and make /dev/sdc, the 80GB disk, first in boot order because with that procedure grub1 should install on it.

[SIZE=2]How do you know all this stuff?

Just a quicky before I blindly follow the instructions - with my three disks is the command
setup (hd0) 
going to be correct or should it be setup (hd1) or even setup (hd2)[/SIZE]

Chris

---

### Post by darkod on 2010-06-06
> **cpcpcp said:**
> [SIZE=2]How do you know all this stuff?

Just a quicky before I blindly follow the instructions - with my three disks is the command
setup (hd0) 
going to be correct or should it be setup (hd1) or even setup (hd2)[/SIZE]

Chris

It should work either way, but you need to set the correct disk as first to boot from after.

Personally, I would install grub to the same disk where ubuntu is. That means when running the 'find...' command returns root(hdX,Y) I would use:

setup (hdX).

In your case it will probably be setup (hd2). And the 80GB needs to be first to boot from after that.

---

### Post by cpcpcp on 2010-06-07
> **darkod said:**
> It should work either way, but you need to set the correct disk as first to boot from after.

Personally, I would install grub to the same disk where ubuntu is. That means when running the 'find...' command returns root(hdX,Y) I would use:

setup (hdX).

In your case it will probably be setup (hd2). And the 80GB needs to be first to boot from after that.

I did all that and the ubuntu came up and loaded and then failed in what looked like terminal mode. I rebooted and then I think I destroyed everthing as rather than sob on your shoulders again I thought I would be clever and run recovery mode. It found problems and and I answered fix it to everything (isn't hindsight wonderful) and now Ubuntu only boots in a terminal mode and windows will not boot at all - something about no MBR if I remember correctly. 
(I not am not at home but earning a crust)
suggestions - buy a new machine and just put the old discs in it? Oh I looked last night for my Vista disc but could not find it so avoid a suggestion that would require that.:mad:

I do still like the idea of Linux but  . . . :)

---

### Post by darkod on 2010-06-07
> **cpcpcp said:**
> I did all that and the ubuntu came up and loaded and then failed in what looked like terminal mode. I rebooted and then I think I destroyed everthing as rather than sob on your shoulders again I thought I would be clever and run recovery mode. It found problems and and I answered fix it to everything (isn't hindsight wonderful) and now Ubuntu only boots in a terminal mode and windows will not boot at all - something about no MBR if I remember correctly. 
(I not am not at home but earning a crust)
suggestions - buy a new machine and just put the old discs in it? Oh I looked last night for my Vista disc but could not find it so avoid a suggestion that would require that.:mad:

I do still like the idea of Linux but  . . . :)

This is starting to make no sense. Yes, you do have small confusion in your system, but nothing too bad. What I mean by this is that you have files looking like the vista bot files on your win98 partition, /dev/sdc1, instead of the vista partition, /dev/sda1. But it should still work OK.
While we are at the subject, are you still using that win98 from /dev/sdc1?

Also, since the fixes that should have worked, seem to have no effect, maybe it's time to consider moving to 10.04. 9.04 has only 6 months support left.

Download the image for 10.04, burn a cd at low speed (low is 4x or 8x), and try it in live mode. If it works fine, most probably it should work fine when installed.

You can also try putting back generic MBR on /dev/sdc, just to see if windows will boot fine. It should give any error, at least not related to ubuntu. If you want to try this, just boot the ubuntu cd in live mode and do:

sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr

Ignore the warnings. That will write generic mbr on /dev/sdc and you should see your windows bootloader when /dev/sdc is first in the boot order.

If that works out fine we can think about booting ubuntu back.

Also, if any of the other disks is external, I think it's time to disconnect it during this troubleshooting. :) Just in case.

---

### Post by cpcpcp on 2010-06-07
I will do this latest version stuff  but it may take a while as I have no working machine at home except my little netbook with no optical drives and I would qite like to get what I have working.

As for the old windows OS that is long gone I had the new machine built (including the old 80GB disc) to run Vista.

I will try the other stuff you mention when I get home

---

### Post by cpcpcp on 2010-06-07
back home.
the error message when trying to go to windows from ubuntu loader message is 
BOOTMGR is missing
Press Ctrl+Alt+Del
   
[B]So what ought I do
A    to restoreVista/ windows
B    to get a graphical Ubuntu[/B]

---

### Post by darkod on 2010-06-07
You said you don't use win98 any more, but it is still detected as OS. Maybe just some remains of the boot files that grub2 picked up, I don't know. But the vista installer seemed to be confused by this too, because it put the vista boot files on the win98 partition.

It seems you just wanted to keep using that hdd (partition) and you just continued using it. You should really format the partition first in that case, to get rid of the old OS and any traces from it (in this case win98 ).

Now, time for drastic measures:

1. Download vista repair cd image from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Burn a cd with that. It should allow you to repair the vista boot process.

2. Power down and unplug ALL hdds except the vista disk. Boot with the vista repair cd and after the language screen, use Repair This Computer process. You might need to run it few times to fix everything.
Alternatively, if the automatic repair doesn't work, there are manual steps from command prompt here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

3. Once you have vista booting happily, power down and add just the ubuntu disk. Boot with the ubuntu cd in live mode, run the script again and post the results file to see the current status.

We'll continue after that. :)

---

### Post by cpcpcp on 2010-06-07
> **darkod said:**
> You said you don't use win98 any more, but it is still detected as OS. Maybe just some remains of the boot files that grub2 picked up, I don't know. But the vista installer seemed to be confused by this too, because it put the vista boot files on the win98 partition.

It seems you just wanted to keep using that hdd (partition) and you just continued using it. You should really format the partition first in that case, to get rid of the old OS and any traces from it (in this case win98 ).

We'll continue after that. :)
[SIZE=3][B]
wow
[/B]This will take a while to get around to.

About the partition on the old 80GB disc, I had no desire to keep using it beyond it being where Vista booted from (and I guess from the error message it has now gone anyway which is why I no longer have Windows). All I wanted to do, and did, was make room on the small disc for Ubuntu to be installed.
It all  went wrong from there. 

I thought, perhaps wrongly, that the reference to Win98 simply dated from the time the FAT disc was formatted.

let me see if I can rescue Windows first.

At least by keeping Ububtu off the two bigger discs my data and progs should be safe even if unaccessible for now
[/SIZE]

---

### Post by cpcpcp on 2010-06-08
UPDATE

I used the recovery disc 

it found no fault with the windows Vista on drive E but on restarting Windows did not appear.

I followed the manual instructions to fix the boot loader. On restarting nothing happened when the 80GB disc was used except it kept rebooting but with the use of "drive E" as windows called it Grub 1.5 appeared with the same error message - Error 22 - as before but no windows. 
 Deja Vue me thinks.

 Later this evening I might try the instructions you gave me last time when I was in this position to sort out grub but the problem seems that the windows loader may have vanished unless it is now on Drive E - and playing hard to get.
**For now I will go back to my desktop, boot using the cd and post the output from bootinfo as recommended by Old Fred** as that be helpful to you experts.
Chris

---

### Post by cpcpcp on 2010-06-08
here is the output from Bootinfo

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  Windows 98
    Boot files/dirs:   /bootmgr /boot/bcd /IO.SYS /MSDOS.SYS /COMMAND.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2270ae87

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2270ae82

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7af1f42

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    11,470,409    11,470,347   b W95 FAT32
/dev/sdc2          11,470,410   156,296,384   144,825,975   5 Extended
/dev/sdc5          11,470,473   150,304,139   138,833,667  83 Linux
/dev/sdc6         150,304,203   156,296,384     5,992,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        26D0908AD09061BB                       ntfs                                     
/dev/sdb1        CEFCFDFBFCFDDDA1                       ntfs                                     
/dev/sdc1        1DF8-203B                              vfat       SEGATE                        
/dev/sdc5        d7c55409-10ad-49e0-9ef0-be668adfe990   ext3                                     
/dev/sdc6        cb50f985-6a6a-4db2-a00a-bd59efcaaa35   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7c55409-10ad-49e0-9ef0-be668adfe990

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d7c55409-10ad-49e0-9ef0-be668adfe990
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=d7c55409-10ad-49e0-9ef0-be668adfe990 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=cb50f985-6a6a-4db2-a00a-bd59efcaaa35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  53.1GB: boot/grub/menu.lst
  53.0GB: boot/grub/stage2
  53.1GB: boot/initrd.img-2.6.28-11-generic
  53.0GB: boot/vmlinuz-2.6.28-11-generic
  53.1GB: initrd.img
  53.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg  
```

Any thoughts so far?

---

### Post by darkod on 2010-06-08
Was /dev/sdc connected or not when you were trying the vista repair? As I suggested in post #25, disconnect all of them, leave just the vista disk connected.

Then run the manual process, but run it at least three times.

Try to boot just like that and see if vista will boot fine. Can it?

PS. The point with disconnecting /dev/sdc is that during the boot repair process windows depends on:
1. Which disk is set as first to boot from in BIOS.
2. Which partition has the boot flag on that disk.

I guess that is how vista boot files ended up on /dev/sdc1. And unless /dev/sdc disk is diconnected, or the boot order changed in BIOS, it will keep doing the same. The easy way to block this interference is to disconnect all disks except the vista disk.

From your new results nothing seems repaired. Vista still doesn't have the boot files on /dev/sda1, and grub1 is still the bootloader on /dev/sda. The windows repair process would have overwritten it.

---

### Post by cpcpcp on 2010-06-08
> **darkod said:**
> Was /dev/sdc connected or not when you were trying the vista repair? As I suggested in post #25, disconnect all of them, leave just the vista disk connected.

Then run the manual process, but run it at least three times.

Try to boot just like that and see if vista will boot fine. Can it?

PS. The point with disconnecting /dev/sdc is that during the boot repair process windows depends on:
1. Which disk is set as first to boot from in BIOS.
2. Which partition has the boot flag on that disk.

I guess that is how vista boot files ended up on /dev/sdc1. And unless /dev/sdc disk is diconnected, or the boot order changed in BIOS, it will keep doing the same. The easy way to block this interference is to disconnect all disks except the vista disk.

From your new results nothing seems repaired. Vista still doesn't have the boot files on /dev/sda1, and grub1 is still the bootloader on /dev/sda. The windows repair process would have overwritten it.

I cant do much more tonight as I am tired but perhaps you would clarify for me the Vista Disc you refer to?
I guess you do not mean the 80GB disc that has Ubuntu on it. 
That leaves the other two identical Maxtor discs. 
In BIOS they are referenced SATA 4 (Maxtor STM3250310AS) and SATA 2 (Maxstor STM 3250820AS) 
Ubuntu refers to them differently and spotting  which one you would like me to dive into the case and disconnect will be fun.
I am guessing but I suspect the Windows system files are on SATA 2 but grub is on SATA 4 since in that BIOS boot order I get the grub loader whilst with SATA 2 first in BIOS the message is about their being no system

With apologies I will first make the BIOS order SATA 2 first and give the recovery disk another  play or three (assuming that is where I need to get it booting from)before I get under the hood nand start ripping leads out.

Chris.

---

### Post by darkod on 2010-06-08
Yes, it's difficult to tell apart same capacity disks. :)

Just changing the order in BIOS should be enough, I wanted to avoid any confusion so suggested unplugging (I rarely do that).

It could also help if at least the 80GB is disconnected, that is where vista repair is putting the files if I understood it right. That's my guess.

---

### Post by cpcpcp on 2010-06-22
[CENTER]**"Look on my works ye mighty and dispair"**


[LEFT][SIZE=3]I think I give up.
 Ubuntu & I have broken my machine beyond help.

I returned to it today and variously made each Maxtor disc in turn the primary hard disc to boot from and in each case I used the rescue disc to try to restore the windows boot loader. As you suggested I tried three times and the results were no different to those previously reported including No Vista.

I think I will either have to buy a new machine and pop my  old hard discs in it or I go back to where I bought  it and see if they will help me out and reinstall windows for me leaving the disc with data intact.

Nightmare loosing use of my operating system whilst trying to install Ubuntu. Thank goodness for this little netbook (even though it was this that tempted me to insall Linux).

Frustration factor is high.

And no I do not wish to climb in the box and disconnect drives especially as two are, to all intents and purposes the same to look at.
[/SIZE][/LEFT]

scream
[/CENTER]

---

