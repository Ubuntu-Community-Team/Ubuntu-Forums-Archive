---
title: "grub/partition table issues"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Atomiktoaster on 2010-02-15
I have Ubuntu 9.10, Win XP and Win 7 installed, and I used gparted to delete an ntfs partition (sda4) and extend the XP partition into the cleared space. Now grub just gives me "Error 17" and doesn't even bring up the boot menu when I try to boot off the HD. I tried grub> root (hd0,5) but I get "Error 21: Selected disk does not exist." It seems like grub can't even figure out where the partitions are anymore on the drive. When I try to mount the XP partition from the live cd, I get an error that says "$LogFile indicates unclean shutdown (0,0)...".

I think I'm in a little over my head, since I'm not really clear on the details of the MBR and partition tables.

I ran the boot info script, here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       194627400 sectors, but according to the info from 
                       fdisk, it has 327693806 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe45ae45a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   327,693,869   327,693,807   7 HPFS/NTFS
/dev/sda2         327,693,870   681,911,054   354,217,185   f W95 Ext d (LBA)
/dev/sda5         327,693,933   634,888,799   307,194,867   7 HPFS/NTFS
/dev/sda6         634,888,863   675,854,549    40,965,687  83 Linux
/dev/sda7         675,854,613   681,911,054     6,056,442  82 Linux swap / Solaris
/dev/sda3         681,911,055   781,417,664    99,506,610   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7C58AC1D58ABD464                       ntfs                                     
/dev/sda3        1ED4B008D4AFDFEF                       ntfs                                     
/dev/sda5        F83CEBCC3CEB844A                       ntfs                                     
/dev/sda6        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06   ext3                                     
/dev/sda7        45739167-a2b1-4500-8e66-2d60c8e648f9   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda6/boot/grub/menu.lst: ===========================

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
default        6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06

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
# howmany=2

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, memtest86+
uuid        0ecd75d0-6777-49f2-8f8e-9c63c71a0b06
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=0ecd75d0-6777-49f2-8f8e-9c63c71a0b06 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=45739167-a2b1-4500-8e66-2d60c8e648f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 341.7GB: boot/grub/menu.lst
 341.7GB: boot/grub/stage2
 341.7GB: boot/initrd.img-2.6.28-13-generic
 341.7GB: boot/initrd.img-2.6.31-19-generic
 341.8GB: boot/vmlinuz-2.6.28-13-generic
 341.8GB: boot/vmlinuz-2.6.31-19-generic
 341.7GB: initrd.img
 341.7GB: initrd.img.old
 341.8GB: vmlinuz
 341.8GB: vmlinuz.old
=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 1392: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 1516: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
/home/ubuntu/Desktop/boot_info_script055.sh: line 897: echo: write error: Input/output error
```

---

### Post by oldfred on 2010-02-15
In your partition editing something got renumbered. It is trying to boot from sda7 which is now swap. You need to reinstall grub. You have an upgraded 9.10 install so you have grub legacy not grub2. So instructions are for old grub (0.97). Do not follow instructions for grub2 with Karmic as that is only new installs of 9.10.

From a liveCD or working linux.
sudo mount /dev/sda6 /mnt
for i in dev proc sys; do mount --bind /$i /mnt/$i; done
sudo chroot  /mnt
grub
#at grub prompt:
root (hd0,5)
setup (hd0,5)
quit

See instructions for older Ubuntu's
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I see it is your first post - welcome to the forum.

---

### Post by Atomiktoaster on 2010-02-15
I ran into problems at the second and third line:
 ```
ubuntu@ubuntu:~$ for i in dev proc sys; do mount --bind /$i /mnt/$i; done
mount: only root can do that
mount: only root can do that
mount: only root can do that
ubuntu@ubuntu:~$ for i in dev proc sys; do sudo mount --bind /$i /mnt/$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

```

I'm assuming I added the sudo in the right place, but the chroot didn't seem to work (not sure what it's doing though).

---

### Post by oldfred on 2010-02-15
I still have trouble on whether sudo is required or not. If you get a message like that then it should have had sudo in front of the command to make it work. I think you had it correct, and I think the partition is sda6 or (hd0,5) in old grub per results.txt

full set of commands to chroot into your system:

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0)

---

### Post by Atomiktoaster on 2010-02-15
I downloaded a 9.10 64-bit live iso, because it seemed like chroot was failing with the old 8.10 32-bit live cd I was using.

I followed the command line directions and restarted, but grub still gave me Error 17. I ended up formatting sda6 and reinstalling 9.10 from the live cd, and I'm and running with grub 2.

---

