---
title: "Dual boot-XP on internal and ubuntu on usb external drive"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by manishmk on 2010-01-13
I have a Toshiba laptop m35-s359 with BIOS 1.30. I installed Ubuntu 9.0.4 on the external USB HDD as I have windows XP on internal HDD and want to dual-boot. It does not recognize USB external HDD as a bootable device and does not boot from it. 
 
It will only see the external HDD if you remove the internal HDD and then shows you the GRUB menu. 
 
1. Is there a BIOS update that will help remedy it? 
2. Is there another way I can dual boot with windows on hd0 and ubuntu on USB external hd1.
 
Any help will be appreciated.
 
Thanks

---

### Post by tommcd on 2010-01-13
> **manishmk said:**
> 
It will only see the external HDD if you remove the internal HDD and then shows you the GRUB menu.
Did you set the laptop's BIOS to boot from the usb as the first boot device? This is what you will need to do so that the grub on the MBR of the external drive boots the system. 
 > **manishmk said:**
> 
1. Is there a BIOS update that will help remedy it? 
If your current BIOS does not have the option to set the usb port as the first boot device, then check the Toshiba support site for any BIOS updates for your model laptop.
> **manishmk said:**
> 
2. Is there another way I can dual boot with windows on hd0 and ubuntu on USB external hd1.
 
You could install Ubuntu to the external drive, and install grub to the MBR of the internal drive. Note that this will overwrite the Windows MBR on the internal drive and replace it with grub.
If the laptop's BIOS allows setting the usb port as the first boot device, then that would be the simplest remedy at this point, so try that first.

---

### Post by manishmk on 2010-01-13
> **tommcd said:**
> Did you set the laptop's BIOS to boot from the usb as the first boot device? This is what you will need to do so that the grub on the MBR of the external drive boots the system. 
=> I did experiment with BIOS, it just has "removable device" as an option, but does not direct the boot to the usb HDD.
 
> **tommcd said:**
> 
If your current BIOS does not have the option to set the usb port as the first boot device, then check the Toshiba support site for any BIOS updates for your model laptop.
=> I have a post open in Toshiba forum. Toshiba itself just gives 1.70 as an upgrade. If there's another site you know for BIOS downloads, pls let me know.
> **tommcd said:**
> 
You could install Ubuntu to the external drive, and install grub to the MBR of the internal drive. Note that this will overwrite the Windows MBR on the internal drive and replace it with grub.
=> Ubuntu is installed on external drive. Once windows MBR is overwritten, I get GRUB error 21 i.e. not found, and nothing boots. How can we modify the windows MBR to give us a boot menu?

---

### Post by presence1960 on 2010-01-13
> **manishmk said:**
> 
***_2. Is there another way I can dual boot with windows on hd0 and ubuntu on USB external hd1._***
 
Any help will be appreciated.
 
Thanks

If your BIOS will not allow you to boot from USB placing GRUB on the internal disk will not work. GRUB does not actually boot the OSs chosen from it's menu but rather points to the directories/files necessary to boot that OS on it's partition. So GRUB will point to /boot on the external disk- but since your BIOS will not allow booting from the USB it still will not boot ubuntu.

---

### Post by manishmk on 2010-01-13
Note that if I remove the internal HDD, the BIOS does recognize the external HDD. So that means BIOS does see it if forced to. So is there a way I can tell GRUB to go to external HDD?
Manish

---

### Post by presence1960 on 2010-01-13
> **manishmk said:**
> Note that if I remove the internal HDD, the BIOS does recognize the external HDD. So that means BIOS does see it if forced to. So is there a way I can tell GRUB to go to external HDD?
Manish

Just because BIOS recognizes the disk does not mean that you can boot from it. BIOS that can not boot from USB still recognizes disks because if you are to use them for data (read/write) they must be recognised or they will not work. Remember BIOS controls how all your hardware works so if a disk is not recognized by BIOS no OS will ever see it.

Your best bet is to refer to your mobo documentation to see if that mobo & BIOS are capable of booting from USB.

---

### Post by manishmk on 2010-01-13
When I said recognize, I meant boot. So when I remove my internal HDD, ubuntu does boot from external HDD. That tells me that if I redirect grub or boot loader to external drive, it should work. Any ideas on it?
Thx

---

### Post by darkod on 2010-01-13
> **manishmk said:**
> When I said recognize, I meant boot. So when I remove my internal HDD, ubuntu does boot from external HDD. That tells me that if I redirect grub or boot loader to external drive, it should work. Any ideas on it?
Thx

You already have it solved by the time I read this. :)
When you said it has an option for "removable device" that means you have to enable that option in order booting from USB to be possible at all. If it's disabled, the booting from USB is ignored.
But you still have to set the correct sequence in which USB has to be before internal HDD. That's usually in Advanced BIOS options too. Look around.
Enable booting from removable device but also look around to set USB before HDD.

---

### Post by presence1960 on 2010-01-13
> **manishmk said:**
> When I said recognize, I meant boot. So when I remove my internal HDD, ubuntu does boot from external HDD. That tells me that if I redirect grub or boot loader to external drive, it should work. Any ideas on it?
Thx

GRUB has to already be on the external drive because you said you disconnected the internal. If the internal is disconnected and GRUB is not on the external it would not boot. By boot you mean ubuntu's desktop loaded right?

Let's see exactly what you have on this rig and what is going on with the boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with both disks plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2010-01-13
I downloaded the User Documentation from Toshiba's site. pretty sparse info, does not even have a section on BIOS or even mention BIOS in the whole manual. BIOS is not even the in the glossary or index.

---

### Post by manishmk on 2010-01-14
Darkod, ubuntu does not boot even when you select "Removable devices" in BIOS. 

Presence1960, when I disconnect the internal HDD, ubuntu boots from external HDD and functions perfectly, desktop, networking, et al. Here's the output of the bootinfo script. Thanks.

> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 942693684 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00800080

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   917,970,164   917,970,102   c W95 FAT32 (LBA)
/dev/sdb2         917,970,165   949,232,654    31,262,490   5 Extended
/dev/sdb5         917,970,228   947,272,724    29,302,497  83 Linux
/dev/sdb6         947,272,788   949,232,654     1,959,867  82 Linux swap / Solar
is


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="C2D8390AD838FE6B" TYPE="ntfs" 
/dev/sdb1: LABEL="My Passport" UUID="305D-3480" TYPE="vfat" 
/dev/sdb5: UUID="7b3fb7f6-eb45-472d-af9a-78debe3a1af6" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="c3192694-8234-4e83-bc18-cbab9e7aff3c" 
/dev/sdb6: UUID="c3192694-8234-4e83-bc18-cbab9e7aff3c" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev
)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nod
ev,user=ubuntu)
/dev/sdb1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname
=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" 
/fastdetect /NoExecute=OptIn
C:\ubnldr.mbr="Auto Super Grub Disk"

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7b3fb7f6-eb45-472d-af9a-78debe3a1af6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b3fb7f6-eb45-472d-af9a-78debe3a1af6

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
uuid        7b3fb7f6-eb45-472d-af9a-78debe3a1af6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7b3fb7f6-eb45-472d-af9
a-78debe3a1af6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7b3fb7f6-eb45-472d-af9a-78debe3a1af6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7b3fb7f6-eb45-472d-af9
a-78debe3a1af6 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7b3fb7f6-eb45-472d-af9a-78debe3a1af6
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=7b3fb7f6-eb45-472d-af9a-78debe3a1af6 /               ext3    relatime,error
s=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c3192694-8234-4e83-bc18-cbab9e7aff3c none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 482.6GB: boot/grub/menu.lst
 482.6GB: boot/grub/stage2
 482.6GB: boot/initrd.img-2.6.28-11-generic
 482.7GB: boot/vmlinuz-2.6.28-11-generic
 482.6GB: initrd.img
 482.7GB: vmlinuz

---

### Post by darkod on 2010-01-14
I think you didn't understand me. The fact you can boot from the ext hdd with the int hdd disconnected says it all. It's working.
Now you need to set up the boot option in BIOS correctly. There are two steps:
1. To enable booting from removable device so you can be allowed to boot from the ext hdd. But this will NOT boot from it automatically.
2. Check the BIOS boot options and how the boot devices are ordered. You need to set the USB before the HDD. Or if you have a Quick Boot menu at startup by pressing F10, F12 or whetever, you can use that to boot from USB.

That's it.

---

### Post by manishmk on 2010-01-14
Darko, I did play around with those boot options, F12, etc. Even if you select the external device, it does not boot from the external HDD. There is no option for USB specifically, the BIOS could be old.
Thanks

---

### Post by darkod on 2010-01-14
OK. Yes, it's difficult like this when I can't see the BIOS and the options. Maybe the options I'm talking about really don't exist.
But I'm still confused. If the BIOS is that old and doesn't support booting from USB, it won't be able to boot from it at all, even with the int hdd disconnected. And it does.
On the other hand, if it supports booting from USB, you must be able to set the option USB before HDD.
Don't know what to say.

---

### Post by tommcd on 2010-01-14
> **manishmk said:**
> Darko,  Even if you select the external device, it does not boot from the external HDD. 

Are you sure you set the BIOS to boot from the external device as the **first boot device**? The external device has to set first in the boot order, before cdrom and before the internal hard drive in order to boot from it. Since the hard drive has Windows MBR on it, it will boot from that if the hard drive is set before the external device in the boot order.

---

### Post by manishmk on 2010-01-14
Darko, I was positive that BIOS is old and won't boot after my initial tries. But when it recognized the external HDD when I removed the internal HDD, it got me confused too. That makes me think that its possible to force it somehow. That's what I am looking for.
TommCD, I did set the external device as the first boot device.
 
Manish

---

### Post by manishmk on 2010-01-14
Presence1960, any insights after looking at boot info?

---

### Post by presence1960 on 2010-01-14
> **manishmk said:**
> Presence1960, any insights after looking at boot info?

windows is on MBR of sda (internal) don't know why it won't boot. GRUB is on MBR of sdb (external) and points to the correct partition for boot files: sdb5.

You messed up and put GRUB on the first sector of sdb1, which is a windows filesystem partition.

AS to why the external can not boot with the internal plugged in- I am at a loss. That is a hardware and/or BIOS issue. Maybe you can get someone to look at it.

---

