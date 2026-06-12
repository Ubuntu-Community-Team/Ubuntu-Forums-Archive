---
title: "Adding Xp to Ubuntu"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by savyboy24 on 2010-03-24
I have a Dell laptop that I clean installed Ubuntu 8.04LTS on. I need to use Itunes for my girl and want to add XP with a small partition on this laptop. Can I add XP with a partition to Ubuntu. I know I can install Ubuntu in a partition of XP but can it be done the other way?

---

### Post by Fafler on 2010-03-24
Not quite. Windows XP is not as good at tolerating other OS'es on the machine. You would have to repartition your filesystem to free up space for a new partition, install Windows, and then fix the bootloader. Another solution is running XP in VirtualBox. Have you considered that? It would spare you a lot of work and you wouldn't have to reboot each time.

---

### Post by savyboy24 on 2010-03-24
Didn't know I could do that. I thought I would just try and run my XP disk and see what happened. So I did. I saw about 4 partitions, 3 small and one big one, that only had 1 MB of it in use. So I deleted this one and split it in to two smaller ones one of which I am now installing XP onto. Hope I did the right thing...I guess I will find out in a bit when it is done.

1)Where do I go from here?

2) Will I have to fix Ubuntu?

---

### Post by mizar001 on 2010-03-24
If you had listen to Fafler, you should know that M$ windows XP is not OS tolerant, so your ubuntu will be invisible once xp is installed.

To restore your actual ubuntu installation you should use a procedure for GRUB Restore (a search on this forum will show you good guides to do that).

It is also possible that the restore of GRUB (the software that detect os partitions when machine starts) will not see Windows partitions, but this can be added once you are inside Ubuntu.

My suggest is : never install/restore windows after linux installation. Sadly but true, ubuntu lives better if it's installed after, or lives much better if it's installed standalone.

The second suggest is : install windows as Virtual machine with vmware server or virtual box, inside ubuntu. If you have enough ram Windows can be only a bit slower than phisical install.

---

### Post by savyboy24 on 2010-03-24
> **mizar001 said:**
> If you had listen to Fafler, you should know that M$ windows XP is not OS tolerant, so your ubuntu will be invisible once xp is installed.

To restore your actual ubuntu installation you should use a procedure for GRUB Restore (a search on this forum will show you good guides to do that).

It is also possible that the restore of GRUB (the software that detect os partitions when machine starts) will not see Windows partitions, but this can be added once you are inside Ubuntu.

My suggest is : never install/restore windows after linux installation. Sadly but true, ubuntu lives better if it's installed after, or lives much better if it's installed standalone.

The second suggest is : install windows as Virtual machine with vmware server or virtual box, inside ubuntu. If you have enough ram Windows can be only a bit slower than phisical install.


Problem is that I started tinkering before he posted LOL. The joy for me is in the tinkering anyhow. 

So now nothing runs...I will try to restore the GRUB. Which one do I have?

---

### Post by Fafler on 2010-03-24
1) You'll lay down on the floor, crying. Well, i hope you didn't have any important data on your laptop.

2) Re-install ;)

Windows doesn't (by default - 3rd party solutions exist) have a driver for the ext3/4 filesystem Ubuntu uses, so it couldn't have told you anything relevant as to how much space Ubuntu was using. Two of the smaller partitions would have been /boot and your swap partition. The large one was probably / and was holding all your data. Don't know what the 3rd small partition was for. Maybe it was / and the large one was /home. Either way, you're screwed. Not sure, as i never use the default layout anyway.

---

### Post by mk-naomi on 2010-03-24
Just as a sidenote. If you are going to use Virtual Box. Use the latest version from the website rather than the repositories version as it doesn't support USBs which will no doubt be a show stopper when you try to connect the Ipod.

---

### Post by mizar001 on 2010-03-24
What means with 'Nothing runs' ? At least windows xp should start !

Anyway ... to restore Grub you need ubuntu live cd. 
Start the live system (insert cd and starts your pc from cdrom).
Once inside Graphical environment open a terminal.

$> sudo grub
find /boot/grub/stage1
root (hdX,Y)    (X and Y are the index found with the previous command)
setup (hdX)
quit

Close the terminal and restart system without cd inserted , and see what happens.

---

### Post by savyboy24 on 2010-03-24
> **mizar001 said:**
> What means with 'Nothing runs' ? At least windows xp should start !

Anyway ... to restore Grub you need ubuntu live cd. 
Start the live system (insert cd and starts your pc from cdrom).
Once inside Graphical environment open a terminal.

$> sudo grub
find /boot/grub/stage1
root (hdX,Y)    (X and Y are the index found with the previous command)
setup (hdX)
quit

Close the terminal and restart system without cd inserted , and see what happens.


when I get to step to find /boot/grub/stage1 I get "error15 file not found"

---

### Post by mizar001 on 2010-03-24
Do Live System mounted the disc ubuntu partition as secondary disc ? Can you find it ? You should find it somewhere in /media folder (try with ouptput of the 'mount' command).

After finding the mount location of the ubuntu file system in your hard disc, open the terminal and try to execute the grub from that location :

$> cd /media/mountedLocation
$> cd sbin
$> ./grub     

and retype the same commands as before.

---

### Post by savyboy24 on 2010-03-24
Erased it all and now I put on xp next I will try to install ubuntu into a partition. When I installed XP I deleted all of the partitions doineed to male new ones before I try to install ubuntu again or will it walk me through the process with the live CD?

---

### Post by mizar001 on 2010-03-26
The live cd can partition your hard disk in order to mantain Windows. The live cd will propose you an optimal solution for windows users, but not for linux users, because it allocates little space for Ubuntu. But if you are unsure or you don't have knowledge on partitioning DO NOT enter in editing Ubuntu proposal, simply accept what ubuntu decide for partitioning.

---

### Post by savyboy24 on 2010-03-27
I thought I had given up on this idea but I have not...yet. So, I got the grub working again and both os's installed. Bit now in the grub menu I cannot see my XP os. How can I run XP...there is a way I know there is I do not believe that it cannot be done. Please help thanks!

---

### Post by savyboy24 on 2010-03-27
If I could only figure out how to get XP to run now?

---

### Post by 98cwitr on 2010-03-27
Wow...you guys sometimes really know how to complicate things...this is easy to do.

1. Use [SRD](http://www.sysresccd.org/Main_Page) (you could just use a stand-alone partitioner, but this disk is a 'must have' for anyone using a Linux OS) to boot and make an NTFS partition the size you want

2. Restart, boot to Windows XP disk

3. Install on NTFS partition

Done.

---

### Post by savyboy24 on 2010-03-27
The thing is that I have XP loaded into it's own ntfs file but can't seem to load it now. I am trying to figure put how to use the grub commands to run it but I am a newbie

---

### Post by paddy.melon on 2010-03-28
if you have the 9.10 disc and, select 'repair mode' you get the option to 'repair' or, 'reinstall' GRUB and, just select this

---

### Post by savyboy24 on 2010-03-28
I am not running 9.10

---

### Post by oldfred on 2010-03-28
If you have everything installed but not quite right run this script so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by mizar001 on 2010-04-02
Take a look at the bottom of my grub list file :
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


```

Now you can do some tries when you are inside ubuntu.
1. Try to understand what is the device that have Windows (probably windows is mounted inside ubuntu under /media/something...). You can do that digiting the command mount.

2. When you discover the location of windows disc you can use this simple mapping (it's not working everytime) :
  if it is sda1 the code for grub is hd0,0
  if it is sda2 the code is hd0,1
  if it is sdb2 the code is hd1,1 
  ... and so on...

3. Once you have found the couple hdX,Y you can append lines to your /boot/grub/menu.lst like those i showed at the beginning.

Beware : do a copy of menu.lst before modifing the file. 
If the windows boot does not work yet you can enter in edit mode of the windows line pressing 'e' (I mean when you are booting with grub) and try some different combinations of hdX,Y until you will see windows start. When you find this couple you must overwrite them in the menu.lst to get them stored permanently in every restart.

---

### Post by savyboy24 on 2010-04-05
Old Fred this is what I got...thanks for looking

---

### Post by savyboy24 on 2010-04-05
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 337365.
    Boot file info:     Grub 0.97 in the file /bootsect.dos looks at sector 
                       349817 of the same hard drive for the stage2 file. A 
                       stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #2 for /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 8135669 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       337,364       337,302  de Dell Utility
/dev/sda2    *        337,365     6,634,844     6,297,480   b W95 FAT32
/dev/sda3           6,634,845    35,680,364    29,045,520  83 Linux
/dev/sda4          35,680,365    78,140,159    42,459,795   f W95 Ext d (LBA)
/dev/sda5          35,680,428    78,140,159    42,459,732   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0801                              vfat       DellUtility                   
/dev/sda2        0556-7980                              vfat       install                       
/dev/sda3        6530795d-2ae9-4320-abde-ffd60ade6806   ext3                                     
/dev/sda5        D49025799025636A                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sda2        /media/install           vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)
/dev/sda5        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


============================= sda2/grub/menu.lst: =============================

; vim:tw=0:noai 
 
; Note: REINSTALL parameter is used by script to add CONFIRMATION PROMPT for reinstall. Do not add this parameter for factory... 
title Recovery Mode -- Automatically reinstall/erase (Intel Graphics) 
  root (hd0,1) 
  kernel /casper/vmlinuz preseed/file=/cdrom/preseed/dell.seed boot=casper noninteractive noprompt REINSTALL edd=on splash quiet 
  initrd /casper/initrd.gz 
 
title Recovery Mode -- Automatically reinstall/erase (AMD Graphics) 
  root (hd0,1) 
  kernel /casper/vmlinuz preseed/file=/cdrom/preseed/dell.seed boot=casper noninteractive noprompt AMD REINSTALL edd=on splash quiet 
  initrd /casper/initrd.gz 
 
title Recovery Mode -- Automatically reinstall/erase (NVIDIA Graphics) 
  root (hd0,1) 
  kernel /casper/vmlinuz preseed/file=/cdrom/preseed/dell.seed boot=casper noninteractive noprompt NVIDIA REINSTALL edd=on splash quiet 
  initrd /casper/initrd.gz 
 
title Recovery Mode -- Boot recovery Live Image (Manual Reinstall) 
  root (hd0,1) 
  kernel /casper/vmlinuz boot=casper preseed/file=/cdrom/preseed/ubuntu.seed edd=on 
  initrd /casper/initrd.gz 
 
title Go back to normal Hard Drive boot 
  rootnoverify (hd0,2) 
  chainloader +1 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\ = "Unidentified operating system on drive C." 

=================== sda2: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .1GB: grub/stage2

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6530795d-2ae9-4320-abde-ffd60ade6806 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=6530795d-2ae9-4320-abde-ffd60ade6806 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=6530795d-2ae9-4320-abde-ffd60ade6806 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=6530795d-2ae9-4320-abde-ffd60ade6806 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=6530795d-2ae9-4320-abde-ffd60ade6806 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6530795d-2ae9-4320-abde-ffd60ade6806 /               ext3    errors=remount-ro 0       1
# /dev/sda5
UUID=6e24c6c0-fded-4b05-b300-7305cc607cea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


   3.6GB: boot/grub/menu.lst
   4.1GB: boot/grub/stage2
   3.6GB: boot/initrd.img-2.6.24-19-generic
   4.1GB: boot/initrd.img-2.6.24-19-generic.bak
   3.5GB: boot/initrd.img-2.6.24-27-generic
   4.0GB: boot/initrd.img-2.6.24-27-generic.bak
   4.1GB: boot/vmlinuz-2.6.24-19-generic
   3.7GB: boot/vmlinuz-2.6.24-27-generic
   3.5GB: initrd.img
   3.6GB: initrd.img.old
   3.7GB: vmlinuz
   4.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  6d 63 d8 54 f0 ca 0e fb  23 e8 df 06 2f c7 dd 53  |mc.T....#.../..S|
00000010  44 f0 67 87 7e 22 7e cf  3e 10 b1 f0 98 b8 16 b6  |D.g.~"~.>.......|
00000020  de 24 f8 e7 af ea 7a c5  b5 ac ac 8a 82 18 e0 cf  |.$....z.........|
00000030  fa 33 49 b4 60 aa 11 9c  fc ca 30 07 b5 e8 5f 0d  |.3I.`.....0..._.|
00000040  7e 34 f8 4a ef c7 5a 3f  c2 4b 5f 83 7a 37 81 fc  |~4.J..Z?.K_.z7..|
00000050  6f 1a 26 b7 1c 76 d0 fd  92 cd 84 02 17 96 14 9b  |o.&..v..........|
00000060  6c b0 a6 d2 c7 7a 92 5b  68 3d 40 03 cc a5 e2 9c  |l....z.[h=@.....|
00000070  6b e2 63 42 82 bc 29 bd  66 74 73 c6 3e ea db b9  |k.cB..).fts.>...|
00000080  8f f0 6b e0 7f 83 be 16  69 7a bf 87 3c 4f e1 2f  |..k.....iz..<O./|
00000090  86 5f 1d 75 3d 5a e2 e6  66 f1 1f 87 ef ee 0d cf  |._.u=Z..f.......|
000000a0  84 26 70 01 8c 31 40 13  cb da cc ab 1b ae 39 24  |.&p..1@.......9$|
000000b0  83 83 5f 39 7e d2 df b2  35 e7 87 ed 64 f1 27 c3  |.._9~...5...d.'.|
000000c0  29 fc 71 e2 cb fd 6c 88  e2 f0 ae b8 f9 6d 10 b6  |).q...l......m..|
000000d0  c0 f6 e1 57 85 18 fb b2  39 e7 af 5c d7 d8 66 be  |...W....9..\..f.|
000000e0  2a fd 7a 0b 09 4e dc 9d  59 c1 52 9d a5 cb 1d 4f  |*.z..N..Y.R....O|
000000f0  a1 7e 00 7c 0a f1 c7 c2  3f 86 a7 c5 fe 09 f8 63  |.~.|....?......c|
00000100  e2 0d 13 c4 c2 d1 ae bc  47 67 ae 78 aa c1 2d e2  |........Gg.x..-.|
00000110  ca 86 df 03 93 95 ce 30  d1 92 7a 67 03 a5 78 37  |.......0..zg..x7|
00000120  c4 6f 1e fc 74 f8 d3 a3  48 3c 53 67 e1 dd 13 c2  |.o..t...H<Sg....|
00000130  fa 50 26 d9 74 7f 22 0b  89 e3 12 2c 8c 0a b2 83  |.P&.t."....,....|
00000140  28 2c 80 e7 3d 46 4f b7  83 94 cb 13 93 55 e6 ae  |(,..=FO......U..|
00000150  fd c9 bf 74 f5 d2 e7 49  2d cf cf 28 b5 8b 9d 7b  |...t...I-..(...{|
00000160  e2 5e a3 ae 6b 9a 17 8d  7c 4d e1 8d 2e 0f b2 5b  |.^..k...|M.....[|
00000170  0d 2e 08 54 68 ae bb 02  bb 34 87 0e 41 39 3d b1  |...Th....4..A9=.|
00000180  91 e9 5f a0 9f 04 7e 35  f8 cf c0 f3 59 68 96 f6  |.._...~5....Yh..|
00000190  fe 0a f1 ae 8f e2 cb b8  34 a6 d3 7c 5f a3 35 dc  |........4..|_.5.|
000001a0  9a 09 91 88 59 e2 8e 19  63 88 b0 0f 83 9e 83 07  |....Y...c.......|
000001b0  91 92 35 ce b3 b5 4b 1b  19 47 48 c7 f1 33 00 fe  |..5...K..GH..3..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 54 e2 87 02 00 00  |......?...T.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

NOw I got the code tags...I am still new!!!

---

### Post by oldfred on 2010-04-06
Wow, you have a lot of grub's installed into partitions (PBR). Grub should only be installed in the MBR unless you are chainbooting which in fact is what we have to do for windows. Windows has to have its PBR with the windows boot loader.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

the windows partition sda2 will have to have the boot flag on it. Linux does not use the boot flag. You probably will not be able to repair until you move the flag. You can use gparted and right click on the windows partition to manage flags.

To restore the windows boot loader to the PBR of the windows partition.
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.
FIXBOOT  C:

Other instructions may say to also run fixmbr but you only want that if you only want to boot windows. If you do run that command then you will have to reinstall grub.

You also have a menu.lst in the windows partition. Just delete that, it may confuse windows.

I do not know if that is everything or not. after these changes lets see what works and if not ok rerun the script so we can tell what else needs to be done. We may have to manually add a windows stanza to the menu.lst.

---

### Post by savyboy24 on 2010-04-06
Ok this is way above my head. But I will do some reading (your link) and decoding with wikipedia and see what I can do. I don't know what PBR, MBR MS or a boot flag is but intend on finding out. Thanks for the help so far. I will let you know when I get some further action completed.

---

### Post by oldfred on 2010-04-06
MBR is master boot record. Computers use the BIOS to start and the BIOS finds the MBR or first sector of the drive designated as the primary master. In windows fixmbr rewrites the MBR. Grub can just be reinstalled to the MBR.
PBR is also known by other names it is like the MBR as a boot sector but at the beginning of every partition. Also boot slice, boot sector. In window fixboot rewrites the PBR.
Windows requires a boot flag or in windows the active partition. When you run fdisk it shows * as the flag setting for boot. There may be other flags also.

---

