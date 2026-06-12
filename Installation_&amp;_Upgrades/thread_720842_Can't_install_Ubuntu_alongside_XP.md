---
title: "Can't install Ubuntu alongside XP"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by aidave on 2008-03-10
I've been having headaches trying to install Ubuntu.  I managed to install Ubuntu on one machine (this one) but this is my old computer and I had to format the harddrive to do it.  My main computer cannot even boot up now that I tried to install Ubuntu.  It is very frustrating!  

After installing "Ubuntu 7.10 Desktop", it would say something like "Error trying to find operating system", then do nothing.  I tried "Linux System Recovery CD" and set the boot to the original Windows XP partition, and that boots properly, thankfully.  

Then I tried "Ubuntu Server 7.10" to use the GRUB reinstall feature.  That worked at first, giving me a GRUB menu.  But none of the OSes would boot, giving error code 15 or 18.  I tried to install again, and now GRUB wont work at all, it says:

"Reboot and Select proper Boot device"
"or Insert Boot Media in selected Boot device and press a key"

I am going crazy trying to get Ubuntu just to install.  I tried the online tutorials but nothing works.

Please help!

---

### Post by zvacet on 2008-03-10
Read [this](http://users.bigpond.net.au/hermanzone/p15.htm#15) and scrolldown to the error 18 and see if that can help you.

---

### Post by aidave on 2008-03-10
Thanks for the reply.

That doesnt seem to help, since I cant even get past "Reboot and Select proper Boot device" message, which seems to be before GRUB.  My computer is also fairly new, so it shouldnt be limited like error message 18 says.  The linux partitition is less than 14 GB.

Here is more info for my system, using "GParted":

Partitions:
/dev/sdb1 ntfs 15GB (Windows XP)
/dev/sdb3 extended 60GB lbs
- /dev/sdb6 ext3 12GB boot (New Partition for Ubuntu)
- /dev/sdb7 linux-swap 2GB
- /dev/sdb5 ntfs 45GB (Data partition for XP)

If I use GParted to set the /dev/sdb1 partition to have the "boot" flag, Windows will run.  Otherwise, nothin works!

---

### Post by zvacet on 2008-03-11
Did you try [this?](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by aidave on 2008-03-11
Actually I did try that, and got back to the initial stage.  GRUB starts, but then everything gives me "Error 22: No Such Partition" for Ubuntu, and Error 18 for Windows.  If I try Ubuntu twice, it will give Error 18 instead of 22.  

This is tiring me out... I cant believe Ubuntu doesnt even come with an option for dual-boot installation.  I thought this would be important.

I might have to give up on Ubuntu because the installer has made a mess of my computer :confused:  I dont want to go back to Windows tho!

---

### Post by sammywham on 2008-03-11
try super grub disk at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by rillip on 2008-03-11
Firstly, does Windows give you a dual boot installation? I thought that would be important.

Second, you have grub, which is letting you do a dual boot instalation.  Granted, it's not working 100% perfectly for you at the moment, but Windows doesn't offer at all.

Problems can be frustrating, but please try not to point fingers at the distro/makers/support - at the end of the day, thousands of people got it working, some with hard work like you, some with no issue at all.

The whole base of the issue is the options aren't going to the approrpiate items, thus giving partition errors.  Try booting with the liveCD, mounting your Linux drive and posting the /boot/grub/menu.lst.  With that and the info you've already provided we can probably fix it.

---

### Post by applehead on 2008-03-11
I wonder why you had to format your drive to install ubuntu on your old machine.  The only problems I've had installing ubuntu on a windows machine was when using a dodgy CD that I burned too quickly.

---

### Post by froy02 on 2008-03-11
Like rilip says post your /boot/grub/menu.lst and your /etc/fstab file.  It looks like you have more than 1 hard drive in your computer because your partitions are sdb's so we are assuming that that is the 2nd drive in your computer.
You might want to post the results of 'sudo fdisk -l' also.

---

### Post by aidave on 2008-03-12
I tried installing Ubuntu onto the first 4 GB of hard drive, with Windows on the next part.  That didnt work at all.  It says "Error Loading Operating System" now, and GRUB doesnt come up.  I ran SuperGRUB and it brought up the GRUB menu, which then gave me error 17 for every choice of boot:

GRUB:

Error loading operating system

SUPERGRUB:

(choose Ubuntu)
root (hd1,1)
Filesystem type unknown, partition type 0xf
Error 17: Cannot mount selected partition

(choose Windows XP)
root (hd1,0)
Filesystem type unknown, partition type 0x7
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot
NTLDR is missing


This is from "fdisk -l"
I have to type it out by hand because its on another computer
The "first" disk sda is just a storage drive.  The "second" disk sdb is where the OSes are.  
----------------
Disk /dev/sda 200.0 GB
255 heads, 63 sectors, 24321 cylinders
Device Boot      Start    End   Blocks   Id System
/dev/sda1 *  1   12748  ... 7 NTFS
/dev/sda2   
/dev/sda5   ... NTFS

Disk /dev/sdb: 80.0 GB
255 heads, 63 sectors, 8078 cylinders
Device Boot      Start    End   Blocks   Id System
/dev/sdb1    523   2426 ... 7 NTFS
/dev/sdb2 *  1   522  ...  83 Linux
/dev/sdb3  2427 9728 ... f W95
/dev/sdb5 3825 9728 ... 7 NTFS
/dev/sdb6 2427 2687 ... 82 Linux Swap
/dev/sdb7 2688 3824 ... 83 Linux
 ------------------------------------------------


How do you print out the "menu.lst" and "fstab" files?  It says they arent real files, but I am on the Live CDs. You say to "mount the linux drive" but I have no idea what that means.

---

### Post by aidave on 2008-03-12
I tried to boot back into Windows, and now GRUB is install on Windows, and Windows wont load anymore!!!

---

### Post by aidave on 2008-03-12
I am in Ubuntu DEsktop Live CD mode:

menu.lst
> 
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
# kopt=root=UUID=ca58e1b8-2cd4-4afa-9d01-121d50641561 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ca58e1b8-2cd4-4afa-9d01-121d50641561 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ca58e1b8-2cd4-4afa-9d01-121d50641561 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	/ntldr
----

i know this is the right file, because i changed the last line to "/ntldr" and it appeared in the boot menu.  however it wont boot any thing

/etc/fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ca58e1b8-2cd4-4afa-9d01-121d50641561 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7A5C99385C98F05D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=46F0B704F0B6F96F /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=46B4CC9DB4CC90BB /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=88A4D337A4D3268A /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=5ae740d9-580e-454e-995c-316257f6a98f /media/sdb7     ext3    defaults        0       2
# /dev/sdb6
UUID=05b27525-1ca8-480c-baaf-080a330aa3c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by zvacet on 2008-03-12
From your **fdisk -l **

/dev/sda1 * 1 12748 ... 7 NTFS

which means that you have windows installed on first disc and first partition.Replace in menu.lst (scroll down)** /dev/sdb1** with** /dev/sda1** and **root (hd1,0)** with **root (hd0,0).**

```
sudo update grub
```

---

### Post by aidave on 2008-03-12
> **zvacet said:**
> From your **fdisk -l **

/dev/sda1 * 1 12748 ... 7 NTFS

which means that you have windows installed on first disc and first partition.Replace in menu.lst (scroll down)** /dev/sdb1** with** /dev/sda1** and **root (hd1,0)** with **root (hd0,0).**

```
sudo update grub
```

omg, its working...! :)

---

### Post by aidave on 2008-03-12
thanks!  wow you are smart!!! 
ill post back to let you know more of the status
i have yet to try the Windows boot (but i dont really NEED that anymore ;)

---

### Post by aidave on 2008-03-12
Ubuntu is running well now!

However the GRUB loader seems to be connected to Windows partition.  Or something.  Because it does not use the changes made in the Ubuntu file.  Windows does also not boot.  This wouldnt be a big problem but I need to convert my old Outlook Emails into Thunderbird.  Apparently there is no way to do that without Windows (?)

---

