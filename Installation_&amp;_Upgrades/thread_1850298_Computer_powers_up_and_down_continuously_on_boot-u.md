---
title: "Computer powers up and down continuously on boot-up"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by afhx on 2011-09-26
I have a Dell Inspiron 530 with Ubuntu 10.4. My problem is that the computer goes into this cycle on boot-up.The initial screen (with F2) comes up, then the system powers down then starts up. Any help  would be greatly appreciated.

---

### Post by sanderd17 on 2011-09-26
So you can't even boot a live CD?

Try putting the computer without power (so disconnect it, get the batteries out if it's a laptop, and press the power button a few times), afterwards, try to start it again.

---

### Post by afhx on 2011-09-26
It is a  desktop. It is not the battery since the time is showing ok. Can't boot from live cd.Now I don't reach the  starting up message . sometimes the computer does start up.
A message appears(too quick for me to read) about the problem maybe.

---

### Post by vinterkind on 2011-09-26
Could you tell your system to put out more messages ?
Normally you can turn on some debug modes via BIOS.

If you enter the BIOS and turn off your HD it should boot until "Hard Disk failure". 
But It shouldn't reboot.

Does it reboot before or after the GRUB2 Loader ?

---

### Post by afhx on 2011-09-26
Reboots sometimes before I reach GRUB2 loader. sometimes after.

---

### Post by afhx on 2011-09-26
Here is the output from boot_info_script

```

============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda2 and looks at sector 2837616 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #2 
                       for /grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /grub/menu.lst

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 404554181 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             128,520    10,618,964    10,490,445   b W95 FAT32
/dev/sda3    *     10,618,965   482,223,104   471,604,140  83 Linux
/dev/sda4         482,223,105   488,279,609     6,056,505   5 Extended
/dev/sda5         482,223,168   488,279,609     6,056,442  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D8-0408                              vfat       DellUtility
/dev/sda2        2B4C-7080                              vfat       OS
/dev/sda3        15322dfd-a7df-4713-b29d-23b843d5de06   ext3       
/dev/sda5        32058402-63f0-4aea-9179-d370b610dc1f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr1         /media/T-Mobile          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


============================= sda2/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
; vim:tw=0:noai

; Note: REINSTALL parameter is used by script to add CONFIRMATION PROMPT for reinstall. Do not add this parameter for factory...
title Recovery Mode -- Automatically reinstall and erase hard drive
  root (hd0,1)
  kernel /casper/vmlinuz preseed/file=/cdrom/preseed/dell.seed boot=casper automatic-ubiquity noprompt REINSTALL xforcevesa
  initrd /casper/initrd.gz

title Recovery Mode -- Boot recovery Live Image (Manual Reinstall)
  root (hd0,1)
  kernel /casper/vmlinuz boot=casper preseed/file=/cdrom/preseed/ubuntu.seed xforcevesa
  initrd /casper/initrd.gz

title Go back to normal Hard Drive boot
  rootnoverify (hd0,2)
  chainloader +1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/menu.lst                                  1
            ?? = ??             grub/stage2                                    1
            ?? = ??             initrd.gz                                      1
            ?? = ??             vmlinuz                                        1

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro

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

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-33-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-33-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-32-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-32-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-32-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-32-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-31-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-31-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-31-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-28-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-28-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-27-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-27-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-25-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-25-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-24-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.31-21-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.31-21-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.28-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=15322dfd-a7df-4713-b29d-23b843d5de06 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 10.04.3 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        chainloader +1
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=15322dfd-a7df-4713-b29d-23b843d5de06 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=32058402-63f0-4aea-9179-d370b610dc1f none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 192.978468418 = 207.209052672  boot/grub/menu.lst                             1
 192.906572819 = 207.131855360  boot/grub/stage2                               2
 192.929956913 = 207.156963840  boot/initrd.img-2.6.28-14-generic              4
 192.930773258 = 207.157840384  boot/initrd.img-2.6.31-21-generic              9
 192.828150272 = 207.047649792  boot/initrd.img-2.6.32-22-generic              7
 192.916559696 = 207.142578688  boot/initrd.img-2.6.32-24-generic              9
 192.876432896 = 207.099492864  boot/initrd.img-2.6.32-25-generic             11
 192.938417912 = 207.166048768  boot/initrd.img-2.6.32-27-generic             10
 192.971510410 = 207.201581568  boot/initrd.img-2.6.32-28-generic              5
 192.958979130 = 207.188126208  boot/initrd.img-2.6.32-30-generic              5
 192.976225376 = 207.206644224  boot/initrd.img-2.6.32-31-generic              9
  89.093866825 = 95.663811072   boot/initrd.img-2.6.32-32-generic              6
  89.138617039 = 95.711861248   boot/initrd.img-2.6.32-33-generic              5
 192.848024845 = 207.068989952  boot/vmlinuz-2.6.28-14-generic                 2
 192.864035130 = 207.086180864  boot/vmlinuz-2.6.31-21-generic                 2
 192.858412266 = 207.080143360  boot/vmlinuz-2.6.32-22-generic                 3
 192.934515476 = 207.161858560  boot/vmlinuz-2.6.32-24-generic                 3
 192.831949711 = 207.051729408  boot/vmlinuz-2.6.32-25-generic                 3
 192.851194859 = 207.072393728  boot/vmlinuz-2.6.32-27-generic                 3
 192.944136143 = 207.172188672  boot/vmlinuz-2.6.32-28-generic                 4
 192.868639469 = 207.091124736  boot/vmlinuz-2.6.32-30-generic                 6
 192.879850864 = 207.103162880  boot/vmlinuz-2.6.32-31-generic                 4
 192.978434086 = 207.209015808  boot/vmlinuz-2.6.32-32-generic                 5
 193.000837803 = 207.233071616  boot/vmlinuz-2.6.32-33-generic                 6
  89.138617039 = 95.711861248   initrd.img                                     5
  89.093866825 = 95.663811072   initrd.img.old                                 6
 193.000837803 = 207.233071616  vmlinuz                                        6
 192.978434086 = 207.209015808  vmlinuz.old                                    5

========= Devices which don't seem to have a corresponding hard drive: =========

sdb

```

---

### Post by sanderd17 on 2011-09-27
So now you are able to boot from a Live CD?

And what partition is what?

Windows is installed to the mbr of sda. So that would mean you never reach Grub.

sda1 and sda2 are vfat partitions, so Windows partitions. Sda1 contains some dell specific boot files (most likely to boot the original Windows OS), but sda2 contains Grub boot files. Grub should never be installed to a vfat formatted partition.

And finally, sda3 also contains grub, and this time it's on an ext4 drive.

Now I ask you what you wanted to achieve. A dual boot? Only linux? A specific partitioning schema?

In any way, do backup all your files. If you have such a mess, you'll likely be lost in partitions once, and if you make a mistake, you can erase all your files without wanting that.

---

### Post by afhx on 2011-09-30
I only have ubuntu installed, there is no dual partition.I submitted the output of the script because it made no sense to me.If I take to be repaired is this likely to be expensive. ?

---

### Post by dino99 on 2011-09-30
seems like a hardware security: do you hear the fans running (open your box) or the ups is going to trouble

---

### Post by sanderd17 on 2011-09-30
single boot Linux?

This should be solvable.

I guess you don't need sda1 and sda2 anymore (they are only leftovers from a previous windows installation).

So in a live CD, open gparted and delete those two partitions (first check that there is indeed nothing important on it). Afterwards, you can enlarge sd3 if you want a bit more space for Linux.

Once that happened, you can reinstall grub by following this thread: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by afhx on 2011-09-30
Please consider this thread closed. The problem seems to have disappeared. However,I am reading the references suggested by dino99 and the links therein.

---

