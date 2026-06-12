---
title: "Grub Stage 1.5 Error 2??"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Yougm on 2010-01-23
Hello,

I am new to Linux and Ubuntu. I have a Dell Optiplex GX260 with 2Gigahertz processor, 512 mb of ram, a Hitachi 250GB harddrive. I am trying to install Ubuntu 8.4.1 LTS I think in a multiboot confguration with Windows XP. I have partitioned my disks properly (120GB for windows NTFS, 105GB for Ubuntu Ext3 and 6GB of swap space, these are all primary partitions). I went throught the installation properly and selected that GRUB should be loaded at (hd0)> I then finished the install.

When I rebooted my PC It said 
```

Grub Stage 1.5

GURB is loading, please wait...
Error 2

```

I have tried installing Grub into several different places but to no avail...

Could any one help me??


Thanks

Yougm

---

### Post by tachuela on 2010-01-23
Allocate space for Ubuntu first from within Windows. Then use the Live CD and install using the option 'maximum free space'.

---

### Post by ssican on 2010-01-23
On GRUB Legacy Page--Grub version 0.97-- there is information about COMMON BOOTING ERRORS AND SOME POSSIBLE CURES:
Grub Errors:
[http://members.iinet.net.au/%7Eherman546/p15.html#Grub_Errors](http://members.iinet.net.au/%7Eherman546/p15.html#Grub_Errors)

Grub Error 2:
[http://members.iinet.net.au/%7Eherman546/p15.html#2_](http://members.iinet.net.au/%7Eherman546/p15.html#2_)

Common Booting Errors:
[http://members.iinet.net.au/%7Eherman546/p15.html#Common_Booting_Errors_and_Some_Possible](http://members.iinet.net.au/%7Eherman546/p15.html#Common_Booting_Errors_and_Some_Possible)

See also:
1)Installing Ubuntu 8.04 LTS
Hardy Heron step-by-step installation guide with screenshots:
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

EDIT
2)How to dual boot Windows XP and Linux (XP installed first) -- the step-by-step guide with screenshots.
You want the simplest way to dual-boot XP and Linux. You've already installed Windows XP and now want to dual-boot it with Ubuntu 8.04
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

EDIT
3)Install Ubuntu after Windows
[https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows)

---

### Post by kansasnoob on 2010-01-23
That is a rare error but it still might be helpful to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Also, assuming you have only one hard drive, the output of:

```
sudo parted /dev/sda print
```

---

### Post by Yougm on 2010-01-25
Ok, I tried the tutorials sscian gave me, it didn't work. " Kansasnoob here is the output of the sudo script '> Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  137GB  137GB   primary   ntfs         boot 
 2      137GB   243GB  106GB   extended                    
 5      137GB   242GB  104GB   logical   ext3              
 6      242GB   243GB  1546MB  logical   linux-swap        
 3      243GB   250GB  6720MB  primary   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.       ' I think its says the boot system is msdos becuase I have to reinstall the microsoft mbr to get my machine going again. This is the other little script '


> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
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
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ca69ca6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,269,434   268,269,372   7 HPFS/NTFS
/dev/sda2         268,269,435   475,266,959   206,997,525   5 Extended
/dev/sda5         268,269,498   472,246,739   203,977,242  83 Linux
/dev/sda6         472,246,803   475,266,959     3,020,157  82 Linux swap / Solaris
/dev/sda3         475,266,960   488,392,064    13,125,105  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9088E96188E945F6" LABEL="Optiplex" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="ffffffff-ffff-ffff-ffff-ffffffffffff" 
/dev/sda3: UUID="ffffffff-ffff-ffff-ffff-ffffffffffff" TYPE="swap" 
/dev/sda5: UUID="d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="1a092fa5-7f8f-457f-970d-89e6ae706592" 
/dev/sda6: UUID="1a092fa5-7f8f-457f-970d-89e6ae706592" TYPE="swap" 

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
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 

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
# kopt=root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1a092fa5-7f8f-457f-970d-89e6ae706592 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 233.7GB: boot/grub/menu.lst
 233.8GB: boot/grub/stage2
 233.7GB: boot/initrd.img-2.6.24-19-generic
 233.8GB: boot/vmlinuz-2.6.24-19-generic
 233.7GB: initrd.img
 233.8GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory

---

### Post by presence1960 on 2010-01-25
A few things I noticed:

```
=> Windows is installed in the MBR of /dev/sda
```

GRUB is not installed to MBR

```
Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ca69ca6

Partition Boot Start End Size Id System

/dev/sda1 * 63 268,269,434 268,269,372 7 HPFS/NTFS
/dev/sda2 268,269,435 475,266,959 206,997,525 5 Extended
/dev/sda5 268,269,498 472,246,739 203,977,242 83 Linux
/dev/sda6 472,246,803 475,266,959 3,020,157 82 Linux swap / Solaris
/dev/sda3 475,266,960 488,392,064 13,125,105 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="9088E96188E945F6" LABEL="Optiplex" TYPE="ntfs"
[COLOR="Red"]/dev/sda3: TYPE="swap" UUID="ffffffff-ffff-ffff-ffff-ffffffffffff"
/dev/sda3: UUID="ffffffff-ffff-ffff-ffff-ffffffffffff" TYPE="swap"[/COLOR]
/dev/sda5: UUID="d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a" SEC_TYPE="ext2" TYPE="ext3"
[COLOR="Red"]/dev/sda6: TYPE="swap" UUID="1a092fa5-7f8f-457f-970d-89e6ae706592"
/dev/sda6: UUID="1a092fa5-7f8f-457f-970d-89e6ae706592" TYPE="swap"[/COLOR] 
```

your swap partitions entries are duplicated-that is odd indeed
```

=================== sda5: Location of files loaded by Grub: ===================


233.7GB: boot/grub/menu.lst
233.8GB: boot/grub/stage2
233.7GB: boot/initrd.img-2.6.24-19-generic
233.8GB: boot/vmlinuz-2.6.24-19-generic
233.7GB: initrd.img
233.8GB: vmlinuz
```

Your files loaded by GRUB are at 233 GB on your disk. If your machine is older it may be subject to the 137 GB limit that BIOS can read on a disk. If that is so you need to look for a BIOS update that addresses that issue or create a separate boot partition at the beginning of your disk.

But first let's put GRUB in the MBR and see if that gets you booting. Boot the Ubuntu Live CD and at the menu choose "try ubuntu without any changes". When the deskttop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

THis will put GRUB on MBR. If you get a GRUB error 18 when booting again the problem is your boot files are located past the point on your disk that is the limit that BIOS can read up to as I mentioned earlier.

---

### Post by meierfra. on 2010-01-25
>  entries are duplicated-that is odd indeed
That's a bug in the boot info script.  I already fixed it, but haven't filed the new release yet. But will do so later today.

---

### Post by Yougm on 2010-01-26
OK presence1960, I reinstalled grub like you said, however I still have a GRUB Error 2...
What should I do??


Thanks in advance

Yougm

---

### Post by presence1960 on 2010-01-26
> **Yougm said:**
> OK presence1960, I reinstalled grub like you said, however I still have a GRUB Error 2...
What should I do??


Thanks in advance

Yougm

Run the boot info script again and let's see what changed. Post the results back here.

---

### Post by Yougm on 2010-01-30
Ok I ran the boot script. Here is what I got

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 456659498 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ca69ca6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,269,434   268,269,372   7 HPFS/NTFS
/dev/sda2         268,269,435   475,266,959   206,997,525   5 Extended
/dev/sda5         268,269,498   472,246,739   203,977,242  83 Linux
/dev/sda6         472,246,803   475,266,959     3,020,157  82 Linux swap / Solaris
/dev/sda3         475,266,960   488,392,064    13,125,105  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9088E96188E945F6                       ntfs       Optiplex                      
/dev/sda3        ffffffff-ffff-ffff-ffff-ffffffffffff   swap                                     
/dev/sda5        d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a   ext3                                     
/dev/sda6        1a092fa5-7f8f-457f-970d-89e6ae706592   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 

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
# kopt=root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1a092fa5-7f8f-457f-970d-89e6ae706592 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 233.7GB: boot/grub/menu.lst
 233.8GB: boot/grub/stage2
 233.7GB: boot/initrd.img-2.6.24-19-generic
 233.8GB: boot/vmlinuz-2.6.24-19-generic
 233.7GB: initrd.img
 233.8GB: vmlinuz
```


Thanks

Yougm

---

### Post by kansasnoob on 2010-01-30
I have an idea but I want to boot into my own 8.04 and check some things.

I'm curious, even before reinstalling grub, were you able to boot into Windows? 

If yes ignore the rest of this.

If no I'd like you to try something. Boot the Live CD and from the live desktop:

```
sudo apt-get install lilo
```

Ignore the warning and just hit enter.

```
sudo lilo -M /dev/sda mbr
```

Then reboot and see if you can boot Windows.

I'll be back :)

---

### Post by kansasnoob on 2010-01-30
I'm very curious whether or not you can boot Windows?????????

Could you before reinstalling grub?

Or did error #2 stop you from booting anything?

Did you try what I suggested in my last post?

If so could you boot Windows then?

I have a couple of ideas but need to know where we're at with this first.

I notice that there have been a few updates to the package "grub" in Hardy since point release 8.04.1 so we could mount and chroot Hardy, update the package list, and reinstall grub (package and all).

In the meanwhile I'm trying some grub2 stuff with Hardy :D

---

### Post by Yougm on 2010-01-30
Ok kansanoob,

I could only boot into Windows once I reinstalled the Microsoft MBR via the Windows Recovery Console (From CD). Always when I had Grub on my PC it gave me an Error 2. I couldn't get into Windows or Linux( Except the Live CD) while GRUB was inatlled.

I'll try LILO

---

### Post by kansasnoob on 2010-01-30
> **Yougm said:**
> Ok kansanoob,

I could only boot into Windows once I reinstalled the Microsoft MBR via the Windows Recovery Console (From CD). Always when I had Grub on my PC it gave me an Error 2. I couldn't get into Windows or Linux( Except the Live CD) while GRUB was inatlled.

I'll try LILO

When you say, "I'll try Lilo", I hope you mean just as I proposed!

**I was NOT suggesting that you use Lilo as the primary bootloader!**

---

### Post by Yougm on 2010-01-30
I did as you asked with the code for lilo, I restarted my my machine and booted into windows... Is that ok??? I ran the boot script again after using your code: ```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 456659498 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9ca69ca6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,269,434   268,269,372   7 HPFS/NTFS
/dev/sda2         268,269,435   475,266,959   206,997,525   5 Extended
/dev/sda5         268,269,498   472,246,739   203,977,242  83 Linux
/dev/sda6         472,246,803   475,266,959     3,020,157  82 Linux swap / Solaris
/dev/sda3         475,266,960   488,392,064    13,125,105  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9088E96188E945F6                       ntfs       Optiplex                      
/dev/sda3        ffffffff-ffff-ffff-ffff-ffffffffffff   swap                                     
/dev/sda5        d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a   ext3                                     
/dev/sda6        1a092fa5-7f8f-457f-970d-89e6ae706592   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 

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
# kopt=root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d52ffa69-d6e3-4b75-b51d-5cf9b1e8717a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1a092fa5-7f8f-457f-970d-89e6ae706592 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 233.7GB: boot/grub/menu.lst
 233.8GB: boot/grub/stage2
 233.7GB: boot/initrd.img-2.6.24-19-generic
 233.8GB: boot/vmlinuz-2.6.24-19-generic
 233.7GB: initrd.img
 233.8GB: vmlinuz
```


Thanks

Yougm

---

### Post by meierfra. on 2010-01-30
I noticed that you have two swap partitions:

```
/dev/sda6         472,246,803   475,266,959     3,020,157  82 Linux swap / Solaris
/dev/sda3         475,266,960   488,392,064    13,125,105  82 Linux swap / Solaris
```


Also your second swap partition does not have a UUID:

```
/dev/sda3        ffffffff-ffff-ffff-ffff-ffffffffffff   swap   
```
Can you tell us  how you installed Ubuntu?  Did you use manual partitioning? What was on your hard drive  before you installed Ubuntu?
Did you  reinstall Ubuntu and created a second swap partition? 


Grub error 2 can occur for many different reason. So here are a few things to try

1)  Run a file system check:

```
sudo umount /dev/sda5 2>/dev/null
sudo e2fsck -fycv /dev/sda5
```


2) Look in your   bios. Also  make sure  your hard drives and cdrom drives are plugged into correctly. See this thread for some concrete suggestions

[http://ubuntuforums.org/showthread.php?t=151682](http://ubuntuforums.org/showthread.php?t=151682)
 

If you change any setting in the bios, make sure to write down the original setting, so can undo your changes if necessary.

3)  Sometimes Grub error 2 is caused by "256 inodes", but that only effected Ubuntu 8.10. Just to make sure, could  you post the output of 

```
sudo tune2fs -l  /dev/sda5 | grep "Inode size"
```

---

### Post by Yougm on 2010-01-31
Ok, Well My partitions are a bit of a mess after I let the installer partition them for me (I normally did it manually), I'll clean them up soon... Before I installed Linux There was My XP primary disk, an NTFS Logical disk (1gb which I didn't use) and some free space. 

I ran your steps 1 & 3 and I'll soon tamper with the BIOS
Step 1 said that there were 0 bad blocks and 1 large file. Step 3 said "The inode size is 128" is that ok?? I'll let you know about the tweaking of the BIOS. Oh and was the thing I did with LILO correct?? 

Thanks

Yougm

---

### Post by Yougm on 2010-01-31
Ok I've checked the BIOS.... Nothing helpful there (Its VERY old) just my Primary Drive 0 is my HardDisk and my Secondary Drive 0 is my CD Drive.

---

### Post by kansasnoob on 2010-01-31
Glad to see Meierfra giving this a look, he's the best of the best :)

I'll just review things a bit. I did see that one large extra primary SWAP but I doubted that had anything to do with your boot problem.

Then again Meierfra knows 100 times more than I do.

---

### Post by kansasnoob on 2010-01-31
BTW you asked:

> I did as you asked with the code for lilo, I restarted my my machine and booted into windows... Is that ok???

Yes. As we try and find a solution to this problem it may be nice for you to be able to at least boot your Windows.

I'm still studying.

---

### Post by meierfra. on 2010-01-31
> I did see that one large extra primary SWAP but I doubted that had anything to do with your boot problem.
The  OP should no have have those two swap partitions and maybe whatever caused those two swap partitions  also caused the Grub 2 error.

> Oh and was the thing I did with LILO correct?? 
Yes.  The  lilo command does  basic the same thing  as the "fixmbr" you did earlier.

> My partitions are a bit of a mess after I let the installer partition them for me (I normally did it manually), I'll clean them up soon... Before I installed Linux There was My XP primary disk, an NTFS Logical disk (1gb which I didn't use)
The installer should  not created two swap partitions.  Did you try fixing your problem by reinstalling? You might also check your Ubuntu CD for errors: Choose "check disk for defects" at the boot menu of the Live CD.

> Step 1 said that there were 0 bad blocks and 1 large file.
Thats fine.

 > Step 3 said "The inode size is 128" is that ok??

Yes. That's what it should be.

> BIOS.... Nothing helpful there (Its VERY old)

How old? You might check whether there is a bios upgrade available.  Also check for loose or faulty cables.

---

### Post by Yougm on 2010-01-31
Hi

> **meierfra. said:**
> The installer should not created two swap partitions. Did you try fixing your problem by reinstalling? You might also check your Ubuntu CD for errors: Choose "check disk for defects" at the boot menu of the Live CD.
 One Swap partition was before I let the installer partition the drive for me...

> How old? You might check whether there is a bios upgrade available. Also check for loose or faulty cables.
My BIOS is Pretty old its Dell Revision A03, the latest for my pc is A09, I haven't installed it yet because of the risk that it'll distroy my entire machine and my dad doesn't want to try and save it. I really doubt there's faulty cables, it should effect more than just GRUB...

I'll check my Linux CD for errors and post the results here.

I read somewhere that you could use LILO instead of GRUB to dual boot Windows and Linux... Shouldn't I do that?

Thanks

From Yougm

---

### Post by meierfra. on 2010-01-31
> My BIOS is Pretty old its Dell Revision A03, the latest for my pc is A09, 
A bios upgrade is probably your best option to cure the problem.


> I read somewhere that you could use LILO instead of GRUB to dual boot Windows and Linux...

I  have no idea whether lilo can get around your bios problem. But you can give it a try. Herman has a nice page on lilo:
[http://members.iinet.net.au/~herman546/p4.html](http://members.iinet.net.au/~herman546/p4.html)

> I really doubt there's faulty cables, it should effect more than just GRUB...

You are probably right, but these things can be funny.


A couple of  more things to try:

1) You might consider creating small  boot partition at the beginning of the hard drive, but  that involves moving the start point your XP partition and it can  be tricky to get XP to boot again

2)  Boot from the Ubuntu LiveCD and choose "boot from first  hard disk". In some strange case this lets you boot into Ubuntu.

3) Get  [supergub]("http://www.supergrubdisk.org/"). Download the    [ iso file](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/super_grub_disk_0.9799.iso) and burn it to a CD.  Boot from the CD and choose the 

5 !LINUX! (1) AUTO"

 option on the first screen. This will   try to boot Ubuntu,

You can also try

3 GRUB => MBR & !LINUX! (1) AUTO  ;- )))

This will  reinstall Grub to the MBR and then boot Ubuntu.


 Start with SuperGrub. It shouldn't take very long and even it it fails, the error messages might give us  better clue on what is going on.

---

### Post by kansasnoob on 2010-02-01
Speaking of cables I just ran across one today where they were still using an old 40 wire IDE cable and a new $2.00 80 wire IDE cable solved things nicely :D

It wasn't a boot issue but rather a random "freeze" issue. Regardless cables can be troublesome.

---

