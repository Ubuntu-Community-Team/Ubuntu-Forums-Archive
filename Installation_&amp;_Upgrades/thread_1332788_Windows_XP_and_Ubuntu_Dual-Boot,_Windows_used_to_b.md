---
title: "Windows XP and Ubuntu Dual-Boot, Windows used to but no longer boots"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by jrc27 on 2009-11-20
My desktop computer originally had Windows XP installed, and then I added Ubuntu, and OpenSuSE as well.  The tri-boot system worked fine for months, until, in a past occurrence similar to my current problem, Windows stopped booting, but the other 2 OSs worked and I could mount my Windows C drive on Ubuntu.  Specifically, when I chose Windows XP at the GRUB screen, it would load and then give me the screen that says Windows has encountered an error and give different boot options like start normally, safe mode, last good configuration (none of which worked, it would just restart the computer and go back to the GRUB screen).  Now with this occurrence, I just randomly tried booting Windows Safe Mode again one day and it worked that time and I did a System Restore and all was well.

Now, the same thing has happened and I can't figure out how to solve it, mostly because I have no idea what fixed it last time other than "magic".  What's different this time is that I can't load Windows Recovery or the HP System Recovery like I was last (although I didn't do anything in them last time).  I've read tons of threads and none seem to match my situation of my tri-boot system once working for a while and how Windows behaves.  If you need me to post the results of any commands or files or anything, let me know, just PLEASE help me fix this quickly! Thanks!

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
If you have an install disk for XP you can use it to restore the system. I had to do this QUITE often when I was running Vista on an HP box. The best fix, of course, is just reformat and reinstall or reformat to ext3 and use as a backup but for gaming and some other uses that isn't an option. I forget how I went about using the install disk to restore but I actually found it when I wanted to switch a hard drive from an HP Pavillion 750n to an HP m8000n without reinstall so I know the info is out there in the interwebs. May I advise an upgrade to Windows 7 as well... it works well for me.

---

### Post by jrc27 on 2009-11-20
I don't have a Windows install cd unfortunately.  The main thing is that I'd like a fix that doesn't require that I lose my files on the Windows drive, because then I'd have to backup everything and then rebuild Windows to the way I had it.  What exactly do you mean by reformat to ext3, would that fit with what I want?  And do you know if a Windows upgrade to Windows 7 would be able to just replace the XP partition and leave the Linux ones alone, and if it would delete my Windows files (i'm guessing it would)?

---

### Post by Eric.brackenbury on 2009-11-20
Go here:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and download the super grub MBR restore it works and I keep a CD with it on just in case I need it again.

Good luck
Eric B

---

### Post by Eric.brackenbury on 2009-11-20
Oh yes I forgot you need to use a friends computer if you cannot get your Linux distro to work either

Eric B

---

### Post by jrc27 on 2009-11-21
So I burned a SuperGrub CD and tried it out but it only recognized the linux partitions at first, and then I selected Auto Magic or something like that and it only found my Windows Recovery partition, which I still cannot boot.

Any other ideas? Remember, I can select Windows XP on the regular GRUB boot screen and it'll try to boot up, but then it'll give me the choices to boot normally, or in safe mode, etc., none of which work, they just restart the computer and bring me back to GRUB.

---

### Post by presence1960 on 2009-11-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jrc27 on 2009-11-22
```
============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 192393130 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #13 for 
                       /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 192393130 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #13 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    15,755,039    15,754,977   c W95 FAT32 (LBA)
/dev/sda2          15,755,040   142,700,352   126,945,313   7 HPFS/NTFS
/dev/sda3    *    185,245,515   312,576,704   127,331,190   5 Extended
/dev/sda5         185,245,578   190,386,314     5,140,737  83 Linux
/dev/sda6         307,291,383   312,576,704     5,285,322  82 Linux swap / Solaris
/dev/sda7         302,680,728   306,953,954     4,273,227  83 Linux
/dev/sda8         306,954,018   307,291,319       337,302  82 Linux swap / Solaris
/dev/sda9         298,070,073   302,343,299     4,273,227  83 Linux
/dev/sda10        302,343,363   302,680,664       337,302  82 Linux swap / Solaris
/dev/sda11        205,808,778   294,198,344    88,389,567  83 Linux
/dev/sda12        294,198,408   298,070,009     3,871,602  82 Linux swap / Solaris
/dev/sda13        190,386,378   205,808,714    15,422,337  83 Linux
/dev/sda4         142,705,395   185,245,514    42,540,120  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="HP_RECOVERY" UUID="77AF-AA80" TYPE="vfat" 
/dev/sda2: UUID="1A282FFC282FD593" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda4: UUID="99af7e04-f958-4439-a093-9d37df40c115" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="34592790-fc9d-4c33-accd-5d957c6e68e8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="597e4d88-266b-4982-9e27-f8013d23248e" TYPE="swap" 
/dev/sda7: UUID="cb2d3e96-8170-4126-982a-c2a4c58ea1d1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="061ca8dd-23d6-4afc-9836-30254ccbea91" TYPE="swap" 
/dev/sda9: UUID="a408974c-5a54-4752-87d6-392578fd022e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="e94941d3-02fd-4f22-b7c0-f4f0f6ecf82d" TYPE="swap" 
/dev/sda11: UUID="d910ecfc-8a1b-4bbc-97d9-49c47f0de811" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: UUID="12f4b80e-e97b-44a7-9ab8-2ad1a1a3a9e8" TYPE="swap" 
/dev/sda13: UUID="d632a9c5-a4a2-4dff-b914-31efd2181dbf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


================================ sda2/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=34592790-fc9d-4c33-accd-5d957c6e68e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=597e4d88-266b-4982-9e27-f8013d23248e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  95.0GB: boot/vmlinuz-2.6.24-19-generic
  95.0GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=cb2d3e96-8170-4126-982a-c2a4c58ea1d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=061ca8dd-23d6-4afc-9836-30254ccbea91 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 155.1GB: boot/vmlinuz-2.6.24-19-generic
 155.1GB: vmlinuz

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=a408974c-5a54-4752-87d6-392578fd022e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=e94941d3-02fd-4f22-b7c0-f4f0f6ecf82d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 154.6GB: boot/vmlinuz-2.6.24-19-generic
 154.6GB: vmlinuz

========================== sda11/boot/grub/menu.lst: ==========================

default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-23-generic
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Microsoft Windows XP Home Edition
root (hd0,1)
chainloader +1
savedefault
makeactive

title Other operating systems:
root 

title Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro quiet splash
initrd /boot/initrd.img-2.6.24-22-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,10)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,10)
kernel /boot/memtest86+.bin
quiet

title Windows NT/2000/XP
root (hd0,0)
chainloader +1
savedefault
makeactive

title Ubuntu 8.04.1 (8.04) (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda5
savedefault

title Ubuntu 8.04.1 (8.04) (on /dev/sda7)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda7
savedefault

title Ubuntu 8.04.1 (8.04) (on /dev/sda9)
root (hd0,8)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda9
savedefault
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
# kopt=root=UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,10)

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


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=d910ecfc-8a1b-4bbc-97d9-49c47f0de811 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda12
UUID=12f4b80e-e97b-44a7-9ab8-2ad1a1a3a9e8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


 107.7GB: boot/grub/menu.lst
 107.7GB: boot/grub/stage2
 107.7GB: boot/initrd.img-2.6.24-19-generic
 107.6GB: boot/initrd.img-2.6.24-19-generic.bak
 107.7GB: boot/initrd.img-2.6.24-22-generic
 107.7GB: boot/initrd.img-2.6.24-22-generic.bak
 107.6GB: boot/initrd.img-2.6.24-23-generic
 107.7GB: boot/initrd.img-2.6.24-23-generic.bak
 107.7GB: boot/initrd.img-2.6.24-24-generic
 107.7GB: boot/initrd.img-2.6.24-24-generic.bak
 107.7GB: boot/vmlinuz-2.6.24-19-generic
 107.7GB: boot/vmlinuz-2.6.24-22-generic
 107.7GB: boot/vmlinuz-2.6.24-23-generic
 107.7GB: boot/vmlinuz-2.6.24-24-generic
 107.7GB: initrd.img
 107.6GB: initrd.img.old
 107.7GB: vmlinuz
 107.7GB: vmlinuz.old

========================== sda13/boot/grub/menu.lst: ==========================

# Modified by YaST2. Last modification on Sat Nov 21 20:14:36 EST 2009
default 4
timeout 15
##YaST - generic_mbr
gfxmenu (hd0,12)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.29-0.1
    root (hd0,12)
    kernel /boot/vmlinuz-2.6.27.29-0.1-default root=/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part13 resume=/dev/sda6 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.29-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.29-0.1
    root (hd0,12)
    kernel /boot/vmlinuz-2.6.27.29-0.1-default root=/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part13 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.29-0.1-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.04.1, kernel 2.6.24-23-generic (/dev/sda11)###
title Ubuntu 8.04.1, kernel 2.6.24-23-generic (/dev/sda11)
    root (hd0,10)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title Windows Recovery
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title Windows XP Home Edition
    rootnoverify (hd0,1)
    chainloader +1

=============================== sda13/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part6 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part10 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part12 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part13 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part4 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part1 /windows/C           vfat       users,gid=users,umask=0002,utf8=true 0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614CR_S0DCJ10Y822352-part2 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda13: Location of files loaded by Grub: ===================


  98.6GB: boot/grub/menu.lst
  98.5GB: boot/grub/stage2
  98.5GB: boot/initrd
  98.5GB: boot/initrd-2.6.27.29-0.1-default
  98.6GB: boot/vmlinuz
  98.6GB: boot/vmlinuz-2.6.27.29-0.1-default
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
```

---

### Post by oldfred on 2009-11-22
Presence usually sees things I do not but to get you started thiinking out several things.

I was not familiar with the acer boot but found this:
Acer ships it’s laptops with a custom [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") and an hidden recovery partition. The code in the MBR can intercept the <Alt><F10> key combination if pressed during the early stage of the boot, more or less when there is the first Acer splashscreen displayed from the BIOS. This key combination let boot the hidden partition and this brings up the restore utility. This stuff is what constitutes the *Restore system to factory default* of the [Acer eRecovery Management]("http://www.google.it/url?sa=t&source=web&ct=res&cd=1&url=ftp%3A%2F%2Fftp.support.acer-euro.com%2Fdesktop%2Fempowering_technology%2FUser%2520Guides%25202.0%2520-%25202.4%2FAcer%2520eRecovery%2520Management%2520english.pdf&ei=cEkgSuq7GaCRjAeN-9HEBg&usg=AFQjCNGLURWH_1L43ldVEc1_PsOuVM6RbQ&sig2=5Nl77G4JZkWNbCEmr3zgtA").

Normally I would suggest reinstalling windows to the PBR partition boot records with fixboot and reinstalling grub to the MBR, but that will overwrite the acer MBR. I am not sure how the acer mbr connects to either ubuntu or OpenSuse. 

The reason you cannot boot the your recovery partition is that the openSuse installed a PBR of its own overwriting the windows boot and linking to partition 13. This may be the way you boot. Do you boot to the openSuse menu.lst?

I do not know the command to save a MBR to a file but I would do that and consider installing grub and using that since Ubuntu will see the recovery partition. Why do you even need the recovery partition? I thought that was just to create a CD or DVD to totally rewrite the hard drive to factory original.

Your Ubuntu menu.lst is totally customized. I would save it and force a new menu.lst to be written from scratch and copy back a few of the custom entries you need. I would also add a chainboot entry to openSuse and have Ubuntu's in charge but that is because I know Ubuntu more and know about nothing about openSuse.

---

### Post by presence1960 on 2009-11-22
> **oldfred said:**
> Presence usually sees things I do not but to get you started thiinking out several things.

I was not familiar with the acer boot but found this:
Acer ships it’s laptops with a custom [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") and an hidden recovery partition. The code in the MBR can intercept the <Alt><F10> key combination if pressed during the early stage of the boot, more or less when there is the first Acer splashscreen displayed from the BIOS. This key combination let boot the hidden partition and this brings up the restore utility. This stuff is what constitutes the *Restore system to factory default* of the [Acer eRecovery Management]("http://www.google.it/url?sa=t&source=web&ct=res&cd=1&url=ftp%3A%2F%2Fftp.support.acer-euro.com%2Fdesktop%2Fempowering_technology%2FUser%2520Guides%25202.0%2520-%25202.4%2FAcer%2520eRecovery%2520Management%2520english.pdf&ei=cEkgSuq7GaCRjAeN-9HEBg&usg=AFQjCNGLURWH_1L43ldVEc1_PsOuVM6RbQ&sig2=5Nl77G4JZkWNbCEmr3zgtA").

Normally I would suggest reinstalling windows to the PBR partition boot records with fixboot and reinstalling grub to the MBR, but that will overwrite the acer MBR. I am not sure how the acer mbr connects to either ubuntu or OpenSuse. 

The reason you cannot boot the your recovery partition is that the openSuse installed a PBR of its own overwriting the windows boot and linking to partition 13. This may be the way you boot. Do you boot to the openSuse menu.lst?

I do not know the command to save a MBR to a file but I would do that and consider installing grub and using that since Ubuntu will see the recovery partition. Why do you even need the recovery partition? I thought that was just to create a CD or DVD to totally rewrite the hard drive to factory original.

Your Ubuntu menu.lst is totally customized. I would save it and force a new menu.lst to be written from scratch and copy back a few of the custom entries you need. I would also add a chainboot entry to openSuse and have Ubuntu's in charge but that is because I know Ubuntu more and know about nothing about openSuse.

Unfortunately I must bow out of this one. I am not at all familiar with how that ACER MBR works, especially in relation to booting other OSs from it. If it were any other situation I could solve this, but I don't want to be responsible for overwriting your Acer MBR.

---

### Post by jrc27 on 2009-11-28
Ok, so I've pretty much given up on fixing the problem while keeping my system intact.  I've backed up everything and I'm planning on wiping my entire system and then just installing Windows XP or Windows 7, so I'll only have 1 OS installed.  I just wanted to make sure that either of the install cd's will install windows over all the partitions so that the whole hard drive is dedicated to windows (I know that the Ubuntu install cd can do this), or if there's anything I'd have to do before hand.

---

### Post by darkod on 2009-11-28
This is not really a place to discuss windows installation but since you asked. :)
Yes, windows installer should allow you to delete all partitions regardless whether they were for windows or ubuntu. After you delete all of them, it's your choice entirely whether you want only one partition for the whole drive, or more.
Have in mind that if anything happens to windows and you have to reformat the system partition, that would be the whole drive if you only have one partition. I always have at least one more, and the data on it can remain intact during clean install on the system partition.

---

