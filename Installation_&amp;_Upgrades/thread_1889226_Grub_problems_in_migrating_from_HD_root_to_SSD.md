---
title: "Grub problems in migrating from HD root to SSD"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by TheOneEyedMan on 2011-11-30
I just got a SSD and I'm using it to replace the hard disk that normally mount as root. The hard drive is 320G but I only use 25G. The SSD is 80G capacity. 

I made use of a usb ubuntu installation and the directions at [Move Installation to new disk]("askubuntu.com/questions/20460/move-installation-to-new-disk") to copy the files the new device and setup grub. While it appears the file transferred the grub setup isn't right. Despite my best attempts it still is booting into the old drive. If I disconnect that drive it doesn't boot into anything at all, just talking about missing UUIDs in the grub loader.

I'm wondering if anyone can help. I've pasted some file content and file system information that I hoped would help. Please let me know if anything else would help diagnose the problem. 

_________________________________________________
Results of df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             288G   25G  249G  10% /
udev                  3.9G  8.0K  3.9G   1% /dev
tmpfs                 1.6G  1.1M  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  4.0G  1.4M  4.0G   1% /run/shm
/dev/sda1             925G  444G  435G  51% /home
/dev/sdc2              74G   25G   46G  36% /home/ultrafast

_________________________________________________
results of blkid
/dev/sda1: LABEL="home" UUID="315e41d9-88bd-403a-9dec-172b8712a8af" TYPE="ext2" 
/dev/sdb1: LABEL="root" UUID="44236a36-9250-42c2-8305-7c2aa949a5c9" TYPE="ext3" 
/dev/sdb5: UUID="639a97ac-f9c3-48a1-a317-e3c8a079237d" TYPE="swap" 
/dev/sdc2: UUID="44695826-2504-4c38-bbe0-944f6878a02d" TYPE="ext4" 

_________________________________________________
from sudo gdisk /dev/sdc
Command (? for help): i
Partition number (1-2): 1
Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)
Partition unique GUID: 1F886228-69C6-4E34-B2A1-9FE97C248A6E
First sector: 2048 (at 1024.0 KiB)
Last sector: 6143 (at 3.0 MiB)
Partition size: 4096 sectors (2.0 MiB)
Attribute flags: 0000000000000000
Partition name: BIOS boot partition

Command (? for help): i
Partition number (1-2): 2
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: 66C1F8AC-A560-48ED-A410-2F28A0C22D8F
First sector: 6144 (at 3.0 MiB)
Last sector: 156301454 (at 74.5 GiB)
Partition size: 156295311 sectors (74.5 GiB)
Attribute flags: 0000000000000000
Partition name: Linux/Windows data

Command (? for help): p
Disk /dev/sdc: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): CAC819F7-9514-4FBF-B7E8-86ED8A2B922C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  BIOS boot partition
   2            6144       156301454   74.5 GiB    0700  Linux/Windows data

_________________________________________________
The only part of menu.lst I touched

title		Ubuntu 11.10, kernel 3.0.0-13-generic
root		(hd2,1)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d
initrd		/boot/initrd.img-3.0.0-13-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d ro single
initrd		/boot/initrd.img-3.0.0-13-generic


title		Ubuntu 11.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

---

### Post by efflandt on 2011-12-01
Which grub are you using and which Ubuntu version? The default grub since Ubuntu 9 something has been grub2, but menu.lst is used by legacy grub, which would have no effect if you currently have grub2.  Also where did you put grub, on your first hd or on the SSD?  You may need to use **sudo grub-install** with parameters to tell grub on which partition to find /boot/grub.

It would help us to help you by posting the output of boot info script wrapped in code tags (highlight and click **#** in message window) [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I currently have Win7 and Maverick (with its grub2 on its primary partition just in case I need it) on sda and 11.10 on sdb (all 64-bit).  sda has standard Windows mbr and 11.10's grub2 on sdb (SSD), currently as boot, in BIOS boots everything. If Maverick does anything (like kernel or video driver update) that updates its initramfs or grub, I just have to do **sudo update-grub** from 11.10 for it to automatically be in main grub menu booting sdb (no messing with menu.lst).  It is best to keep your grubs separate so they do not step on each other during updates.

---

### Post by TheOneEyedMan on 2011-12-01
I'm using Ubuntu 11.10.

GRUB2 isn't showing up as installed in Synaptic Package Manager so I'm assuming I am using grub 1.

---

### Post by TheOneEyedMan on 2011-12-01
Thanks for the help.
___________________________________
Shell output of sudo bash boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Computing Partition Table of /dev/sde...
Searching sda1 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdc1 for information... 
Searching sdc2 for information... 
Searching sde1 for information... 
Searching sdd for information... 

Finished. The results are in the file "RESULTS.txt"
____________________________________________
A zipped copy of RESULTS.txt is attached.

---

### Post by oldfred on 2011-12-01
When you copied the grub.cfg and fstab still have the old UUIDs. So When you boot sdc it will use the UUID from your old install. I think this is the main reason to do a clean install as well as housecleaning out all the old history.

> Device           UUID                                   TYPE       LABEL

/dev/sda1        315e41d9-88bd-403a-9dec-172b8712a8af   ext2       home
/dev/sdb1        [COLOR=Red]44236a36-9250-42c2-8305-7c2aa949a5c9[/COLOR]   ext3       root
/dev/sdb5        639a97ac-f9c3-48a1-a317-e3c8a079237d   swap       
/dev/sdc2        44695826-2504-4c38-bbe0-944f6878a02d   ext4       


Your fstab on sdc2:
```
# / was on /dev/sdb1 during installation
UUID=[COLOR=Red]44236a36-9250-42c2-8305-7c2aa949a5c9[/COLOR] /oldroot               ext3    errors=remount-ro 0       1

```

Your grub.cfg on sdc2:
>     set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]44236a36-9250-42c2-8305-7c2aa949a5c9[/COLOR]
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=[COLOR=Red]44236a36-9250-42c2-8305-7c2aa949a5c9[/COLOR] ro   quiet splash vt.handoff=7


You can manually edit fstab. And this may be one time where it is easier to edit the grub.cfg directly (which you never do), otherwise you have to chroot into your system to run the update grub. Once booted then run the sudo update-grub.

---

### Post by TheOneEyedMan on 2011-12-01
Oldfred, that worked!  I went into /home/ultrafast/boot/grub/grub.cfg and replaced the old UUID with the new one. Now it works. Thank you much.

Next time I update GRUB or Ubuntu am I going to have a problem with this reset to the old values?

---

### Post by oldfred on 2011-12-01
You need to make sure the grub install is based on your SSD install. Have you updated fstab and reinstall grub to the MBR of the SSD. There is also a file with the grub reinstall location that you need to update.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Before rebooting then check that the UUIDs are corrected.

---

### Post by TheOneEyedMan on 2011-12-01
I don't understand how to tell if "grub install is based on your SSD install" based on the output of fdisk -l. I have pasted the output below and I'm hoping you can straighten me out. 
Thanks. 


Output of sudo fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1953520064   976760001   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047861

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   613072529   306536233+  83  Linux
/dev/sdb2       613072591   625137344     6032377    5  Extended
/dev/sdb5       613072593   625137344     6032376   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   156301487    78150743+  ee  GPT

---

### Post by oldfred on 2011-12-01
Fdisk will not tell much about grub.

What did this show?
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

And for the most information, you can run the boot_info script. It just does not show exact partition used now with the newest grub 1.99. Something changed in the latest grub.

I run this before & after every change to system and I include it in my rsync backup.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by TheOneEyedMan on 2011-12-02
Code requested below. It looks like grub is indeed installed on the ssd /dev/sdc
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 44236a36-9250-42c2-8305-7c2aa949a5c9 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   613,072,529   613,072,467  83 Linux
/dev/sdb2         613,072,591   625,137,344    12,064,754   5 Extended
/dev/sdb5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1   156,301,487   156,301,487  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048         6,143         4,096 BIOS Boot partition
/dev/sdc2           6,144   156,301,454   156,295,311 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        315e41d9-88bd-403a-9dec-172b8712a8af   ext2       home
/dev/sdb1        44236a36-9250-42c2-8305-7c2aa949a5c9   ext3       root
/dev/sdb5        639a97ac-f9c3-48a1-a317-e3c8a079237d   swap       
/dev/sdc2        44695826-2504-4c38-bbe0-944f6878a02d   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /home                    ext2       (rw)
/dev/sdb1        /oldroot                 ext3       (rw,errors=remount-ro,commit=0)
/dev/sdc2        /                        ext4       (rw,noatime,discard,commit=0)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 11.10, kernel 3.0.0-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=0b93c54c-837a-42d8-8954-e0bb0e6cca21 ro
initrd		/boot/initrd.img-3.0.0-13-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-3.0.0-13-generic

title		Ubuntu 11.10, kernel 3.0.0-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 2.6.38-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.38-11-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-11-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.38-11-generic

title		Ubuntu 11.10, kernel 2.6.38-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.38-10-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-10-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.38-10-generic

title		Ubuntu 11.10, kernel 2.6.38-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.38-8-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.10, kernel 2.6.35-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 11.10, kernel 2.6.35-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 11.10, kernel 2.6.32-31-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-31-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-31-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-31-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-31-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-31-generic

title		Ubuntu 11.10, kernel 2.6.32-30-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-30-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-30-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 11.10, kernel 2.6.32-29-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-29-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-29-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-29-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-29-generic

title		Ubuntu 11.10, kernel 2.6.32-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-28-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 11.10, kernel 2.6.32-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-27-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-27-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-27-generic

title		Ubuntu 11.10, kernel 2.6.32-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-26-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-26-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 11.10, kernel 2.6.32-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 11.10, kernel 2.6.32-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 11.10, kernel 2.6.32-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 11.10, kernel 2.6.32-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 11.10, kernel 2.6.32-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 11.10, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 11.10, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 11.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 11.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 11.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/sdb,msdos1)'
  search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.24-24-generic ...'
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.22-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	echo	'Loading Linux 2.6.22-14-generic ...'
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.22-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44236a36-9250-42c2-8305-7c2aa949a5c9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 /               ext3    errors=remount-ro 0       1

# /home was on /dev/sda1 during installation
UUID=315e41d9-88bd-403a-9dec-172b8712a8af /home           ext2    defaults        0       2

# swap was on /dev/sdb5 during installation
UUID=639a97ac-f9c3-48a1-a317-e3c8a079237d none            swap    sw              0       0

#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#/dev/sdc1: UUID="0b93c54c-837a-42d8-8954-e0bb0e6cca21" TYPE="ext4" 

UUID=44695826-2504-4c38-bbe0-944f6878a02d /home/ultrafast ext4 defaults,noatime,discard 0 1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             2
               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.22-14-generic              4
               =                boot/initrd.img-2.6.22-14-generic.bak         15
               =                boot/initrd.img-2.6.24-24-generic             13
               =                boot/initrd.img-2.6.24-24-generic.bak         14
               =                boot/initrd.img-2.6.32-21-generic             26
               =                boot/initrd.img-2.6.32-22-generic             279
               =                boot/initrd.img-2.6.32-23-generic             127
               =                boot/initrd.img-2.6.32-24-generic             14
               =                boot/initrd.img-2.6.32-25-generic             205
               =                boot/initrd.img-2.6.32-26-generic              3
               =                boot/initrd.img-2.6.32-27-generic             59
               =                boot/initrd.img-2.6.32-28-generic             108
               =                boot/initrd.img-2.6.32-29-generic             69
               =                boot/initrd.img-2.6.32-30-generic             18
               =                boot/initrd.img-2.6.32-31-generic             10
               =                boot/initrd.img-2.6.35-28-generic             20
               =                boot/initrd.img-3.0.0-12-generic              19
               =                boot/initrd.img-3.0.0-13-generic              11
               =                boot/vmlinuz-2.6.22-14-generic                 2
               =                boot/vmlinuz-2.6.24-24-generic                 3
               =                boot/vmlinuz-2.6.32-21-generic                 3
               =                boot/vmlinuz-2.6.32-22-generic                 6
               =                boot/vmlinuz-2.6.32-23-generic                247
               =                boot/vmlinuz-2.6.32-24-generic                 2
               =                boot/vmlinuz-2.6.32-25-generic                 9
               =                boot/vmlinuz-2.6.32-26-generic                84
               =                boot/vmlinuz-2.6.32-27-generic                 2
               =                boot/vmlinuz-2.6.32-28-generic                70
               =                boot/vmlinuz-2.6.32-29-generic                341
               =                boot/vmlinuz-2.6.32-30-generic                16
               =                boot/vmlinuz-2.6.32-31-generic                46
               =                boot/vmlinuz-2.6.35-28-generic                 8
               =                boot/vmlinuz-3.0.0-12-generic                 38
               =                boot/vmlinuz-3.0.0-13-generic                  5
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        5
               =                vmlinuz.old                                   38

=========================== sdc2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 11.10, kernel 3.0.0-13-generic
root		(hd2,1)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d
initrd		/boot/initrd.img-3.0.0-13-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d ro single
initrd		/boot/initrd.img-3.0.0-13-generic


title		Ubuntu 11.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
### /dev/sdb1 44236a36-9250-42c2-8305-7c2aa949a5c9
### /dev/sdc2 44695826-2504-4c38-bbe0-944f6878a02d 
search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/sdb,msdos1)'
  search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.24-24-generic ...'
	linux	/boot/vmlinuz-2.6.24-24-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.22-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	echo	'Loading Linux 2.6.22-14-generic ...'
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=44695826-2504-4c38-bbe0-944f6878a02d  ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.22-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 44695826-2504-4c38-bbe0-944f6878a02d 
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=44236a36-9250-42c2-8305-7c2aa949a5c9 /oldroot               ext3    errors=remount-ro 0       1

# /home was on /dev/sda1 during installation
UUID=315e41d9-88bd-403a-9dec-172b8712a8af /home           ext2    defaults        0       2

# swap was on /dev/sdb5 during installation
UUID=639a97ac-f9c3-48a1-a317-e3c8a079237d none            swap    sw              0       0

#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#/dev/sdc1: UUID="0b93c54c-837a-42d8-8954-e0bb0e6cca21" TYPE="ext4" 

UUID=44695826-2504-4c38-bbe0-944f6878a02d / ext4 defaults,noatime,discard 0 1
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               1
               =                boot/initrd.img-2.6.22-14-generic              1
               =                boot/initrd.img-2.6.22-14-generic.bak          1
               =                boot/initrd.img-2.6.24-24-generic              1
               =                boot/initrd.img-2.6.24-24-generic.bak          1
               =                boot/initrd.img-2.6.32-21-generic              1
               =                boot/initrd.img-2.6.32-22-generic              1
               =                boot/initrd.img-2.6.32-23-generic              1
               =                boot/initrd.img-2.6.32-24-generic              1
               =                boot/initrd.img-2.6.32-25-generic              1
               =                boot/initrd.img-2.6.32-26-generic              1
               =                boot/initrd.img-2.6.32-27-generic              1
               =                boot/initrd.img-2.6.32-28-generic              1
               =                boot/initrd.img-2.6.32-29-generic              1
               =                boot/initrd.img-2.6.32-30-generic              1
               =                boot/initrd.img-2.6.32-31-generic              2
               =                boot/initrd.img-2.6.35-28-generic              2
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-13-generic               2
               =                boot/vmlinuz-2.6.22-14-generic                 1
               =                boot/vmlinuz-2.6.24-24-generic                 1
               =                boot/vmlinuz-2.6.32-21-generic                 1
               =                boot/vmlinuz-2.6.32-22-generic                 1
               =                boot/vmlinuz-2.6.32-23-generic                 1
               =                boot/vmlinuz-2.6.32-24-generic                 1
               =                boot/vmlinuz-2.6.32-25-generic                 1
               =                boot/vmlinuz-2.6.32-26-generic                 1
               =                boot/vmlinuz-2.6.32-27-generic                 1
               =                boot/vmlinuz-2.6.32-28-generic                 1
               =                boot/vmlinuz-2.6.32-29-generic                 1
               =                boot/vmlinuz-2.6.32-30-generic                 1
               =                boot/vmlinuz-2.6.32-31-generic                 1
               =                boot/vmlinuz-2.6.35-28-generic                 1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by oldfred on 2011-12-02
Boot script does not show this you only need to check that the install_devices line is the sdc drive:

What did this show?
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You also still have menu.lst which is from grub legacy. You should just be able to delete it since you are on grub2.

---

### Post by TheOneEyedMan on 2011-12-02
Output of sudo debconf-show grub-pc
```
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
  grub-pc/kopt_extracted: false
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3320620AS_6QF0XZQN
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/mixed_legacy_and_grub2: true
```

Output of ls /dev/disk/by-id/
```
total 0
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 ata-INTEL_SSDSA2CW080G3_CVPR1380019L080BGN -> ../../sdc
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 ata-INTEL_SSDSA2CW080G3_CVPR1380019L080BGN-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 ata-INTEL_SSDSA2CW080G3_CVPR1380019L080BGN-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 ata-ST3320620AS_6QF0XZQN -> ../../sdb
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 ata-ST3320620AS_6QF0XZQN-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 ata-ST3320620AS_6QF0XZQN-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 ata-ST3320620AS_6QF0XZQN-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 ata-WDC_WD1001FALS-00J7B1_WD-WMATV1706896 -> ../../sda
lrwxrwxrwx 1 root root 10 2011-12-01 11:52 ata-WDC_WD1001FALS-00J7B1_WD-WMATV1706896-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 scsi-SATA_INTEL_SSDSA2CW0CVPR1380019L080BGN -> ../../sdc
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 scsi-SATA_INTEL_SSDSA2CW0CVPR1380019L080BGN-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 scsi-SATA_INTEL_SSDSA2CW0CVPR1380019L080BGN-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 scsi-SATA_ST3320620AS_6QF0XZQN -> ../../sdb
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 scsi-SATA_ST3320620AS_6QF0XZQN-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 scsi-SATA_ST3320620AS_6QF0XZQN-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 scsi-SATA_ST3320620AS_6QF0XZQN-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 scsi-SATA_WDC_WD1001FALS-_WD-WMATV1706896 -> ../../sda
lrwxrwxrwx 1 root root 10 2011-12-01 11:52 scsi-SATA_WDC_WD1001FALS-_WD-WMATV1706896-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 wwn-0x50014ee05699a52c -> ../../sda
lrwxrwxrwx 1 root root 10 2011-12-01 11:52 wwn-0x50014ee05699a52c-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2011-12-01 11:34 wwn-0x50015179596b7bc9 -> ../../sdc
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 wwn-0x50015179596b7bc9-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-12-01 11:34 wwn-0x50015179596b7bc9-part2 -> ../../sdc2
```

So ata-ST3320620AS_6QF0XZQN looks like it is sdb and therefore grub is not keying off of the SSD. Would running sudo update-grub fix this?

---

### Post by oldfred on 2011-12-02
From post #7

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

