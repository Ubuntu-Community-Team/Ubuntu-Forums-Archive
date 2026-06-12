---
title: "duel booting with xp"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by musdem on 2009-12-28
I'm tring to install Ubuntu to my second hard drive, with XP on my first hard drive and every time I try to it automatically boots to Ubuntus grub loader how do I change it so it boots from windows boot manager instead of grub (I'm a newbie with duel booting so be patient)

---

### Post by presence1960 on 2009-12-28
> **musdem said:**
> I'm tring to install Ubuntu to my second hard drive, with XP on my first hard drive and every time I try to it automatically boots to Ubuntus grub loader how do I change it so it boots from windows boot manager instead of grub (I'm a newbie with duel booting so be patient)

That is the usual way of booting windows & Linux: GRUB. GRUB is a lot more friendly in getting different OSs to boot. The windows boot manager on the other hand is not so friendly when trying to boot non-windows OSs, and can sometimes be tricky to get them to boot.

---

### Post by musdem on 2009-12-29
I know that is the usual way of booting but any time I boot it says grub error 17 so I want to by pass grub so I can boot properly.

---

### Post by presence1960 on 2009-12-29
> **musdem said:**
> I know that is the usual way of booting but any time I boot it says grub error 17 so I want to by pass grub so I can boot properly.

[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

see here for error 17. That is usually an easy fix. Why don't you do this so I can see what the problem is:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

You can look at this another way. Instead of ignoring the problem you can fix it and at the same time learn something new about Linux. If you stick with Linux you will be learning through mishaps as Linux is not like windows. Of course it is your decision which path you take, but running back to what is comfortable all the time is not going to increase your knowledge or expertise with Linux.

---

### Post by musdem on 2009-12-29
I typed exactly what you put as the code and it told me that "there is no such directory or file" was I not supposed to copy and paste the code or is this something else?

---

### Post by presence1960 on 2009-12-29
> **musdem said:**
> I typed exactly what you put as the code and it told me that "there is no such directory or file" was I not supposed to copy and paste the code or is this something else?

move the file you downloaded to the desktop. Then run the command from terminal.

If you did not download the file use the link in my signature "Boot Info Script". Click on the link, when downloaded move it to desktop and run the command.

---

### Post by oldfred on 2009-12-29
Run the script presence so we can see where everything is at.

Generally dual booting with two drives I like to keep windows as is and since Ubuntu/grub can easily boot windows also, make ubuntu be the first hard drive and windows the second drive. Then if someday there is a issue with with first drive you can still switch back and windows will still boot.

To switch Sata drives you just have to go into BIOS and tell it to boot from the second drive. If IDE/Pata drives you may be able to change in BIOS or may have to change master/slave connections in the computer.

---

### Post by musdem on 2009-12-30
Ok after reinstalling it again it's working but then I installed a driver for my new graphics card and rebooted and now it's giving me error 25 and it still won't boot properly.

---

### Post by presence1960 on 2009-12-30
> **musdem said:**
> Ok after reinstalling it again it's working but then I installed a driver for my new graphics card and rebooted and now it's giving me error 25 and it still won't boot properly.

When are you going to download the script and post the results as asked? I for one refuse to try to help with boot issues unless I have the info requested. The reason why is very simple: I can not see EXACTLY your setup & boot process.

Until then I guess you are going to troubleshoot this on your own.

---

### Post by musdem on 2009-12-31
OK sorry for not giving you the results I thought that if it was a different error you wouldn't want the same info so here it is:
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,941,614,591 1,941,612,544   7 HPFS/NTFS
/dev/sda2       1,941,615,900 1,953,520,064    11,904,165   5 Extended
/dev/sda5       1,941,615,963 1,953,520,064    11,904,102  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00018c77

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,941,615,899 1,941,615,837  83 Linux
/dev/sdb2       1,941,615,900 1,953,520,064    11,904,165   5 Extended
/dev/sdb5       1,941,615,963 1,953,520,064    11,904,102  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1999.6 GB, 1999696297984 bytes
255 heads, 63 sectors/track, 243115 cylinders, total 3905656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005a4e2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 3,905,656,831 3,905,654,784   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D20CCDC90CCDA935" TYPE="ntfs" 
/dev/sda5: UUID="3cd6a602-f08d-4d38-82b9-b0fb7b3a31b4" TYPE="swap" 
/dev/sdb1: UUID="6e3d82d6-5dcb-494b-b2f0-fe9f157e9430" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e32484ca-1983-4fc2-8f26-a15a69bf8ccb" TYPE="swap" 
/dev/sdc1: UUID="40284A46284A3AE4" LABEL="My Book" TYPE="ntfs" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/My Book type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr2 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=hal,uid=999)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT /TUTAG=N1PS1Y 

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430

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
uuid        6e3d82d6-5dcb-494b-b2f0-fe9f157e9430
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6e3d82d6-5dcb-494b-b2f0-fe9f157e9430
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6e3d82d6-5dcb-494b-b2f0-fe9f157e9430
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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e32484ca-1983-4fc2-8f26-a15a69bf8ccb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 858.3GB: boot/grub/menu.lst
 858.4GB: boot/grub/stage2
 858.3GB: boot/initrd.img-2.6.28-11-generic
 858.4GB: boot/vmlinuz-2.6.28-11-generic
 858.3GB: initrd.img
 858.4GB: vmlinuz

---

### Post by musdem on 2009-12-31
sorry the smile faces are all 8 then )

---

### Post by presence1960 on 2009-12-31
Here is error 25 from the GRUB version 0.97 Manual:

25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

Your script results look ok. But I would try a couple changes. I would put GRUB on the MBR of sdb rather than the windows (sda) disk. This will necessitate you changing your hard disk boot order in BIOS to sdb, sda, sdc. And lastly you will need to change the windows stanza in menu.lst so you can boot windows after those changes. Sounds harder than it actually is. You will need the 9.04 Live CD/USB.

Boot from the Live CD/USB, select "try ubuntu without any changes..." When the desktop loads open a terminal and do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". 
5. Type "root (hd1,0)"
6. Type "setup (hd1)" to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

When rebooting go into BIOS and set the hard disk boot order to sdb (Ubuntu disk), sda (windows) then lastly sdc. Save changes to CMOS and continue booting. Boot into Ubuntu. Open a termianl and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

scroll down to your windows entry and change this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

TO:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title          Windows Vista (loader)
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Click Save on toolbar. Close file & reboot. Now try booting windows. (I am assuming you were able to boot windows prior to this error)

---

### Post by musdem on 2009-12-31
holy crap you are a genius thank you so much and also I was not able to boot windows before it just froze up at the error.

---

### Post by musdem on 2010-01-01
OK now I'm trying to get the graphics card to work its an ATI Radeon HD 4670 and i installed the driver that ii found at this URL: 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English) 
and it wont work any ideas?

---

### Post by presence1960 on 2010-01-01
> **musdem said:**
> OK now I'm trying to get the graphics card to work its an ATI Radeon HD 4670 and i installed the driver that ii found at this URL: 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English) 
and it wont work any ideas?

I am not able to help with that as I am a Nvidia man. But here is some info for you:

[http://www2.ati.com/drivers/linux/catalyst_912_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_912_linux.pdf)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I do not know if that is helpful to you. You can try using Envyng to download and install the ATI driver for you. If you do not have Envyng installed open a terminal and run one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk
```

Then run in terminal ```
envyng -t
```
Follow the prompts to uninstall the ATI driver, then choose to install.

If nothing else works since you are now able to boot I would start a new thread containing the words ATI Radeon 4670 in the title to attract those people successfully using that card.

---

