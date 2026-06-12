---
title: "Grub wont boot vista?"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by wolfhunter9154 on 2009-12-28
Hello guys, I'm having a problem with my 9.04 install. I just re-installed it today and it wont let me boot up vista which is on the same disc but a different partition. It says that there is no OS on it or something similar. I checked the hd and all files are still there. These are my hard drives: I have a 80 gb 60 vista the other 20 ubuntu. A 120 for all my crap on the computer because I ran out of space on the 80. And 1 10 GB partition off the 120 drive and then a 1 tb drive with win 7. The bootloader is on the vista partition so it wont let me load win 7. I could just reinstall win7 because I don't have much on it yet but I would prefer not to.  Thanks in advance.

---

### Post by presence1960 on 2009-12-28
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by wolfhunter9154 on 2009-12-28
These are my results.


```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 213994431.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #192843 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1156df79

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   213,993,471   213,991,424   7 HPFS/NTFS
/dev/sda2         213,994,431   234,441,647    20,447,217   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac47ee18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,892,081,663 1,892,079,616   7 HPFS/NTFS
/dev/sdb2    *  1,892,081,664 1,953,519,615    61,437,952  af HFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x394c394b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63       192,779       192,717  82 Linux swap / Solaris
/dev/sdc2             192,780    21,430,709    21,237,930   5 Extended
/dev/sdc5             192,843    21,430,709    21,237,867  83 Linux
/dev/sdc3    *     21,430,710   156,296,384   134,865,675   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40B64DC9B64DC060" LABEL="120 disc" TYPE="ntfs" 
/dev/sda2: LABEL="UNTITLED 3" UUID="6FE3-07F0" TYPE="vfat" 
/dev/sdb1: UUID="0E1CF8A81CF88C49" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb2: UUID="88BC0740A311E4AD" LABEL="OSX" TYPE="hfsplus" 
/dev/sdc1: UUID="f91e209e-b572-4067-9daf-c357fd4766cb" TYPE="swap" 
/dev/sdc3: UUID="C834940C3493FF9C" TYPE="ntfs" 
/dev/sdc5: UUID="f53925ef-0759-4470-ac8e-148a616ceb9d" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
/dev/sda1 on /media/120 disc type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Windows 7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=f53925ef-0759-4470-ac8e-148a616ceb9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f53925ef-0759-4470-ac8e-148a616ceb9d

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
uuid        f53925ef-0759-4470-ac8e-148a616ceb9d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f53925ef-0759-4470-ac8e-148a616ceb9d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f53925ef-0759-4470-ac8e-148a616ceb9d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f53925ef-0759-4470-ac8e-148a616ceb9d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f53925ef-0759-4470-ac8e-148a616ceb9d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc3
title        Windows Vista (loader)
rootnoverify    (hd2,2)
savedefault
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
UUID=f53925ef-0759-4470-ac8e-148a616ceb9d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc1 during installation
UUID=f91e209e-b572-4067-9daf-c357fd4766cb none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


   4.7GB: boot/grub/menu.lst
   4.7GB: boot/grub/stage2
   4.1GB: boot/initrd.img-2.6.28-11-generic
   4.0GB: boot/vmlinuz-2.6.28-11-generic
   4.1GB: initrd.img
   4.0GB: vmlinuz
```

---

### Post by presence1960 on 2009-12-28
```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR="Red"]Operating System:  [/COLOR]
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [COLOR="DarkOrchid"]/grldr
[/COLOR]

```

This is windows from 1 TB disk above. First problem the Operating System is not defined, so there may be a problem with that install.
You also have grub4dos installed as evidenced by the /grldr in boot files/dir. You want to boot into Ubuntu and mount that sdb1 partition and delete /grldr.



```
sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
   [COLOR="Red"] Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #192843 on boot drive #1[/COLOR]
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [COLOR="Purple"]/grldr[/COLOR]
```

Again you want to delete the /grldr on sdc3. You also have a problem there in the bootfile info, unsure what that is at the moment.

You want to also boot into ubuntu and edit your menu.lst
Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
Scroll down to windows Vista entry and change this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc3
title        Windows Vista (loader)
rootnoverify    (hd2,2)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```
TO:

```
title          Windows Vista
rootnoverify   (hd0,2)
chainloader    +1
```

In Legacy GRUB (version 0.97) the (hdx,y) designation where x = device & y = partition, the x character is not determined by the disk order in fdisk, but rather by the hard disk boot order in BIOS. Since sdc boots first in the hard disk order(if it didn't you would not get GRUB) then sdc becomes (hd0). That makes Vista (hd0,2).

You also do not need the map lines when windows is on the disk that boots first in BIOS. You only need those when windows is on a disk other than the disk booting first in BIOS.

---

### Post by wolfhunter9154 on 2009-12-28
I'll try this tomorrow. I'm too tired and dont want to mess up.

---

### Post by presence1960 on 2009-12-28
> **wolfhunter9154 said:**
> I'll try this tomorrow. I'm too tired and dont want to mess up.

I hear you, nothing like fatigue causes errors we usually would not make. Sleep on it.

---

### Post by meierfra. on 2009-12-29
>  BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector [COLOR="Red"]#192843 [/COLOR]on boot drive #1


NST/nst_grub.mbr is  a file  used by EasyBCD  to chain load the boot sector of the Ubuntu partition:

> dev/sdc5             [COLOR="Red"]192,843  [/COLOR]  21,430,709    21,237,867  83 Linux

The file does not cause any harm. But since the boot sector  of sdc5: 
> 
scd5: 
    Boot sector info:  


contains no boot code, the file is pretty useless.


> 
sdb1:
Operating System:   
Boot files/dirs:  /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr


The boot info script  looks inside the file winload.exe for the words "Vista" and "Windows 7" to identify the operating system. For some reason your winload.exe does not seem  to have "Windows 7" insert. I don't think that  is anything to worry about, but just a flaw in the boot info script.


> title          Windows Vista
rootnoverify   (hd0,2)
chainloader    +1
+1

But since you have "bootmgr" also  on /dev/sdb1, you might also try


title          Windows 7
rootnoverify   (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

and 

title          Windows 7
rootnoverify   (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader    +1

---

### Post by wolfhunter9154 on 2009-12-29
> **meierfra. said:**
> 

title          Windows 7
rootnoverify   (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader    +1

Thanks! this worked. And thank you to presence too.

---

### Post by presence1960 on 2009-12-29
> **wolfhunter9154 said:**
> Thanks! this worked. And thank you to presence too.

Glad you got it working. Enjoy.

---

### Post by meierfra. on 2009-12-29
> glad you got it working. Enjoy.
+1

---

### Post by meierfra. on 2009-12-29
Could you do my a favor? I'm trying to figure out why the boot info script did not detect the Window 7 operating system:

```
sudo mount /dev/sdb1 /mnt
cd /mnt/Windows/System32
tar -cvf ~/Desktop/winload.exe.tar.gz winload.exe
```

This creates the file winload.exe.tar.gz on your desktop.   Could you attach that file to your next post?

Thanks

---

