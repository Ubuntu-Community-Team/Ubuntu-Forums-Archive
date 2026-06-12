---
title: "Grub did not upgrade"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by raunhar on 2010-03-28
I upgraded Ubuntu 8.10 to 9.04 and then to 9.10

After upgrade I noticed that while booting Grub showed 8.10 with the old kernel.

How do I upgrade it, so that while booting it shows the new version.

---

### Post by Tom.Lane on 2010-03-28
Hello.

You will need to update the grub.conf file. You can use the following command to open the file in nano.

In a Terminal window type:

```
nano /boot/grub/grub.conf
```

Keep scrolling down until you find the line that says your operating system name and modify it accordingly.

EDIT: it should look something like this when complete.

```
title Ubuntu 9.10
root (hd0,5)
```
Tom

---

### Post by oldfred on 2010-03-28
If you upgraded and did not separately uninstall grub legacy and install grub2 you still have old grub and its menu.lst.

You can edit menu.lst manually but if you upgraded to grub2, you do not directly edit grub.conf.

Did you try, it should work for old grub as well as grub2, but grub2 is much better at finding new operating systems.

sudo update-grub

---

### Post by raunhar on 2010-03-29
I have the old grub with menu.lst

When I opened that file through terminal, There was no mention of the new kernels.

---

### Post by presence1960 on 2010-03-29
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by raunhar on 2010-03-30
Here is the content of RESULT.txt
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9e3f9e3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   156,296,384    94,863,825   f W95 Ext d (LBA)
/dev/sda5          61,432,623   112,631,714    51,199,092   b W95 FAT32
/dev/sda6         112,631,778   156,296,384    43,664,607  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7A0454D2045492CD                       ntfs                                     
/dev/sda5        24AA-D63F                              vfat                                     
/dev/sda6        18539188-4390-4960-9b29-d9ca86606674   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18539188-4390-4960-9b29-d9ca86606674

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
# defoptions=quiet splash vga=773

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

title		Ubuntu 8.10, kernel 2.6.27-15-generic
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

#title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

#title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=18539188-4390-4960-9b29-d9ca86606674 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
uuid		18539188-4390-4960-9b29-d9ca86606674
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=18539188-4390-4960-9b29-d9ca86606674 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd.img-2.6.27-15-generic
    ??GB: boot/initrd.img-2.6.31-20-generic
    ??GB: boot/vmlinuz-2.6.27-15-generic
    ??GB: boot/vmlinuz-2.6.31-20-generic
    ??GB: initrd.img
    ??GB: vmlinuz

---

### Post by oldfred on 2010-03-30
Did you run the sudo update-grub? The top entry is your Karmic -15 but it did not add the -20 newest version to the menu. All the other entries are the old versions and you should edit out.

The other choice is to copy the -15 entry and manually create -20 entry. And change descriptions to Karmic 9.10.

You could rename menu.lst to menu.lst.old and run the update. It should create a brand new menu.lst. If the old kernels are still in synaptic I would also delete them.

---

### Post by raunhar on 2010-03-31
I have reinstalled Ubuntu 09.04 and then upgraded it to 9.10.
So problem solved the other way.

---

