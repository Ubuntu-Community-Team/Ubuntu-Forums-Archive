---
title: "Ubuntu 9.10 GRUB Error 11: Unrecognized device string"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by jtfourieuk on 2010-01-14
(I'm a bit of a noob).

I performed an update last night on Ubuntu 9.10 64 bit (I started in Ubuntu 9.04, updated in about November to 9.10).  Everything seemed to go well with the update last night.

Tonight I wanted to boot into Windows Vista.  I got the following message when I chose the option for other OSes:  "Error 11: Unrecognized device string".

I noticed that it doesn't give the option for Vista.  From some other forums I looked at my menu.lst file, which I reproduce here.  The last two options (Windows vista and XP) doesn't appear in my GRUB menu at start up.  I also include /boot/grub/device.map and fdisk -l below.



```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# .........................
# A bunch more comments (starting with #) that I removed.  Let me know if I should repost with them.
# .........................



## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1
```


/boot/grub/device.map

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

fdisk -l

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       27760   212374520    7  HPFS/NTFS
/dev/sda4           27761       38914    89587625+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           27761       28732     7807558+  82  Linux swap / Solaris
/dev/sda7           28733       33595    39062016   83  Linux
/dev/sda8           33596       38586    40090176    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x393bfcf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12749   102400000    7  HPFS/NTFS
```

Any help out there?

TIA

---

### Post by running_rabbit07 on 2010-01-14
This link shows you how to manually add Windows. [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Leppie on 2010-01-14
why don't you upgrade to grub2?
```
sudo apt-get install grub-pc grub-common
```

---

### Post by jtfourieuk on 2010-01-14
How do I see which disk / sector grub is installed to?  Will it be (hd0,0)?

---

### Post by Leppie on 2010-01-14
> **jtfourieuk said:**
> How do I see which disk / sector grub is installed to?  Will it be (hd0,0)?
which version of grub are you talking about? in grub legacy (hd0,0) would be sda1, but in grub2 (hd0,0) doesn't exist (partition numbering starts at 1, hd0 is the mbr of sda).

---

### Post by jtfourieuk on 2010-01-14
> **Leppie said:**
> why don't you upgrade to grub2?
```
sudo apt-get install grub-pc grub-common
```

Let me just see if running_rabbit07's post solves my problem then I'll try the grub2 approach.

---

### Post by Leppie on 2010-01-14
> **jtfourieuk said:**
> Let me just see if running_rabbit07's post solves my problem then I'll try the grub2 approach.
grub2 is more advanced. it has an os-prober which can add newly installed or missing operating systems.

---

### Post by jtfourieuk on 2010-01-14
> **Leppie said:**
> which version of grub are you talking about? in grub legacy (hd0,0) would be sda1, but in grub2 (hd0,0) doesn't exist (partition numbering starts at 1m hd0 is the mbr of sda).

I'm still using grub legacy.  I'm wondering how will I see where grub is currently installed to.  Is there a possibility that it is installed to (hd1,0)?  (If it helps in answering, grub is the first boot menu I see.)

---

### Post by Leppie on 2010-01-14
you could [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/"), the first thing listed should be which version(s) of grub is (are) installed in which mbr.

---

### Post by jtfourieuk on 2010-01-14
> **running_rabbit07 said:**
> This link shows you how to manually add Windows. [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I tried the steps in the link you posted but I get the following:

```
Probing devices to guess BIOS drives. This may t

       [ Minimal BASH-like line editing is suppo
         the   first   word,  TAB  lists  possib
         completions.  Anywhere else TAB lists t
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
```

I can access that disk so I don't understand why it can't mount it.

---

### Post by jtfourieuk on 2010-01-14
> **Leppie said:**
> you could [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/"), the first thing listed should be which version(s) of grub is (are) installed in which mbr.


Below are the results from running the script.  Can you guys maybe see why I get this:
```
Probing devices to guess BIOS drives. This may take a 

       [ Minimal BASH-like line editing is supported. 
         the   first   word,  TAB  lists  possible  co
         completions.  Anywhere else TAB lists the pos
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition

```


```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       240,974       240,912  de Dell Utility
/dev/sda2             241,664    21,213,183    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,213,184   445,962,223   424,749,040   7 HPFS/NTFS
/dev/sda4         445,964,461   625,139,711   179,175,251   f W95 Ext d (LBA)
/dev/sda5         619,898,880   625,139,711     5,240,832  dd Dell Media Direct
/dev/sda6         445,964,463   461,579,579    15,615,117  82 Linux swap / Solaris
/dev/sda7         461,579,643   539,703,674    78,124,032  83 Linux
/dev/sda8         539,703,738   619,884,089    80,180,352   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x393bfcf7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   204,802,047   204,800,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-030D" TYPE="vfat" 
/dev/sda2: UUID="AE942C83942C505F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="6E3A2FDE3A2FA257" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="4C33-DD2F" TYPE="vfat" 
/dev/sda6: UUID="9e4f9d23-750a-426c-803e-806496de9992" TYPE="swap" 
/dev/sda7: UUID="f7fc3d3d-eb82-4572-a75b-4449d0755913" TYPE="ext3" 
/dev/sda8: UUID="E931-7D0A" TYPE="vfat" 
/dev/sdb1: UUID="D2AA94E3AA94C57F" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda8 on /sharedubwin type vfat (rw,utf8,umask=007,gid=46)
gvfs-fuse-daemon on /home/jtfourie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jtfourie)
/dev/sdb1 on /media/D2AA94E3AA94C57F type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== sda7/boot/grub/menu.lst: ===========================

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
default saved

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
# kopt=root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f7fc3d3d-eb82-4572-a75b-4449d0755913

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		f7fc3d3d-eb82-4572-a75b-4449d0755913
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f7fc3d3d-eb82-4572-a75b-4449d0755913 /               ext3    relatime,errors=remount-ro 0       1
# /sharedubwin was on /dev/sda8 during installation
UUID=E931-7D0A  /sharedubwin    vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=9e4f9d23-750a-426c-803e-806496de9992 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 236.3GB: boot/grub/menu.lst
 236.3GB: boot/grub/stage2
 236.3GB: boot/initrd.img-2.6.28-16-generic
 236.3GB: boot/initrd.img-2.6.31-14-generic
 236.3GB: boot/initrd.img-2.6.31-15-generic
 236.3GB: boot/initrd.img-2.6.31-16-generic
 236.3GB: boot/initrd.img-2.6.31-17-generic
 236.3GB: boot/vmlinuz-2.6.28-16-generic
 236.3GB: boot/vmlinuz-2.6.31-14-generic
 236.3GB: boot/vmlinuz-2.6.31-15-generic
 236.3GB: boot/vmlinuz-2.6.31-16-generic
 236.3GB: boot/vmlinuz-2.6.31-17-generic
 236.3GB: initrd.img
 236.3GB: initrd.img.old
 236.3GB: vmlinuz
 236.3GB: vmlinuz.old
```

---

### Post by oldfred on 2010-01-14
Back to your original error. did you actually click on this line?
when I chose the option for other OSes
The other os line is meant to be a comment but because it cannot show comments it has a blank root line that will not boot anything. You have to select the windows entry below. I set my default to that line once and and walked away when it was booting and it kept not working.:)

You do not have ubuntu at hd0,0 but at hd0,6 or sda7. The find command should only find (hd0,6) and that is what you should enter for the root command.

---

### Post by jtfourieuk on 2010-01-14
> **oldfred said:**
> Back to your original error. did you actually click on this line?
when I chose the option for other OSes
The other os line is meant to be a comment but because it cannot show comments it has a blank root line that will not boot anything. You have to select the windows entry below. I set my default to that line once and and walked away when it was booting and it kept not working.:)

You do not have ubuntu at hd0,0 but at hd0,6 or sda7. The find command should only find (hd0,6) and that is what you should enter for the root command.

Yes, I did click on that line.  I realised that was the reason I had the error 11.

However, I managed to "solve" the problem.  I feel (rightfully) like an idiot.

> **jtfourieuk said:**
> I noticed that it doesn't give the option for Vista.  From some other forums I looked at my menu.lst file, which I reproduce here.  The last two options (Windows vista and XP) doesn't appear in my GRUB menu at start up

The "reason" the last two arguments didn't show is because I hadn't scrolled down far enough.  The latest kernel update (from last night) caused them to move below the last visible options for the boot loader.

But thanks nonetheless for everyone that helped.

Two quick questions:  Can I just delete the grub entries of the earlier kernel versions?  Can I move the vista option up?

Thanks again all.  You can mark this thread as solved.

---

### Post by Leppie on 2010-01-14
> **jtfourieuk said:**
> Two quick questions:  Can I just delete the grub entries of the earlier kernel versions?  Can I move the vista option up?
yes, AFAIK you can just edit the menu.lst to your likings and save.

> **jtfourieuk said:**
> You can mark this thread as solved.
you have to do that using "Thread Tools" (above the post at the top), or edit the status (under the post at the bottom).

---

