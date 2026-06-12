---
title: "Problem loading ubuntu after fresh install"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by tarutaruomen on 2008-11-23
Hello, I just installed Ubuntu 8.10 on my computer with a windows partition too.  however whenever it tries to load there seems to be an error and it automatically loads windows xp.  I tried using super grub disk and when I try to load ubuntu using the grub menu I get this error. 
"kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=2cfb8f05-6c10-48a5-8ad7-6649df1c5802 ro quiet splash
Error 13: Invalid or unsupported executable format.

I checked a bit and found some information about the bug here
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290798]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290798")

It says there that it's been fixed but I can't find the fix anywhere.  could any of you help me if you've encountered this problem before?

Thank You

---

### Post by tarutaruomen on 2008-11-23
Ok, here's something i found that seems suspicious
I loaded the live cd and checked the fstab file and i found this
/boot/vmlinuz-2.6.27-7-generic root=UUID=2cfb8f05-6c10-48a5-8ad7-6649df1c5802 **ro** quiet splash
that **ro** is where I think the problem is.

I think I need to change the permissions to read write but since I'm not the owner of the files i can't change the file from there.  Is there anyway I can do that from the boot menu or using super grub disk?

---

### Post by caljohnsmith on 2008-11-24
How about from your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the following:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/[COLOR="Blue"]sdXY[/COLOR] /mnt
sudo blkid
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
So replace the sdXY with your Ubuntu partition, and please post the output of the above commands.

---

### Post by tarutaruomen on 2008-11-24
here is the output of the command
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
# kopt=root=UUID=2cfb8f05-6c10-48a5-8ad7-6649df1c5802 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2cfb8f05-6c10-48a5-8ad7-6649df1c5802

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2cfb8f05-6c10-48a5-8ad7-6649df1c5802
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2cfb8f05-6c10-48a5-8ad7-6649df1c5802 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2cfb8f05-6c10-48a5-8ad7-6649df1c5802
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2cfb8f05-6c10-48a5-8ad7-6649df1c5802 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2cfb8f05-6c10-48a5-8ad7-6649df1c5802
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdh1
title		Microsoft Windows XP Home Edition
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1





here's the fdisk -lu output

Disk /dev/sda: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd41c07e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1465145135   732572536+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65695290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdh2       204796620   976768064   385985722+   5  Extended
/dev/sdh5       204796683   216797174     6000246   82  Linux swap / Solaris
/dev/sdh6       216797238   316801799    50002281   83  Linux
/dev/sdh7       316801863   976768064   329983101   83  Linux
ubuntu@ubuntu:~/Documents$ sudo mount /dev/sdh6 /mnt
ubuntu@ubuntu:~/Documents$ sudo blkid
/dev/sda1: UUID="5AAC10F7AC10CEFF" LABEL="BackupII" TYPE="ntfs" 
/dev/sdb1: UUID="6860227C6022515C" LABEL="My Book" TYPE="ntfs" 
/dev/sdg1: UUID="7C9CAD119CACC74C" LABEL="Seagate" TYPE="ntfs" 
/dev/sdh1: UUID="D4C4F74DC4F72FFA" TYPE="ntfs" 
/dev/sdh5: UUID="67666581-b14b-4035-9269-8ff9eabcc70c" TYPE="swap" 
/dev/sdh6: UUID="2cfb8f05-6c10-48a5-8ad7-6649df1c5802" TYPE="ext3" 
/dev/sdh7: UUID="b9861857-8ff3-4a77-8496-e2a0ee6a0cfb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~/Documents$ ls -l /mnt/boot
total 14336
-rw-r--r-- 1 root root   503560 2008-11-04 20:53 abi-2.6.27-7-generic
-rw-r--r-- 1 root root    85316 2008-11-04 20:53 config-2.6.27-7-generic
drwxr-xr-x 3 root root     4096 2008-11-23 19:21 grub
-rw-r--r-- 1 root root 10219040 2008-11-23 19:21 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root   124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root  1352144 2008-11-04 20:53 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root     1130 2008-11-04 20:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root  2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic

I have multiple disks, 2 SATA drives, 1 being 750gb, 1 500gb both internal.  and 2 other external 500gb HD's one connected through usb the other through firewire.  Currently my linux partition is on my 500gb drive which is the one that also has windows. when I load the live disk the root partition is identified as sdh6.

Hope this info helps

---

### Post by caljohnsmith on 2008-11-26
Can you change your BIOS to boot your Ubuntu sdh drive on start up? If so, that would be the most ideal solution, because you could install Grub to the MBR (Master Boot Record) of your Ubuntu sdh drive and make it bootable. You could also add an entry in your Ubuntu Grub's menu to boot Windows. If that sounds good to you, then from the Live CD do:
```
sudo grub
grub> device (hd0) /dev/sdh
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Reboot, set you BIOS to boot the Ubuntu drive, and then you should be able to boot into Ubuntu if all goes well. Let me know how it goes or if you run into problems.

---

### Post by tarutaruomen on 2008-11-27
> **caljohnsmith said:**
> Can you change your BIOS to boot your Ubuntu sdh drive on start up? If so, that would be the most ideal solution, because you could install Grub to the MBR (Master Boot Record) of your Ubuntu sdh drive and make it bootable. You could also add an entry in your Ubuntu Grub's menu to boot Windows. If that sounds good to you, then from the Live CD do:
```
sudo grub
grub> device (hd0) /dev/sdh
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Reboot, set you BIOS to boot the Ubuntu drive, and then you should be able to boot into Ubuntu if all goes well. Let me know how it goes or if you run into problems.

It worked!! for some reason when I loaded it changed my drive to sdg instead but it worked perfectly.  Is that a bug? because I had the same problem trying to install past versions of it and was about to give up lol.

Thanks a lot for your help I really appreciate it.

---

### Post by tarutaruomen on 2008-11-27
> **tarutaruomen said:**
> It worked!! for some reason when I loaded it changed my drive to sdg instead but it worked perfectly.  Is that a bug? because I had the same problem trying to install past versions of it and was about to give up lol.

Thanks a lot for your help I really appreciate it.

Guess my happiness was short lived, now i can't boot windows lol.
It says there's an error with the configuration.

---

### Post by caljohnsmith on 2008-11-27
OK, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Windows entries with:
```
title	   Windows XP (hd0)
root       (hd0,0)
chainloader +1

```
If Windows is on the same drive as Ubuntu as you say, the above entry should work to boot Windows. If not, let me know exactly what happens when you try it from the Grub menu.

---

### Post by tarutaruomen on 2008-11-27
YESS!!!
Sir, you are the man :P Can I suck your brain to see if i get all this? :P

Everything seems to be working perfectly now.

Can you please tell me what all that meant in english?  I'm a linux newbie so I kind of have an idea of it all but I'm not sure.  Thanks a lot for your help.

Oh, yes one last question.  I have to modprobe -r b44 ndiswrapper ssp etc. to then load b43 so i can get wireless connection everytime I boot the computer.  Is there a way to automate that?

Once again thank you.

---

### Post by caljohnsmith on 2008-11-27
> **tarutaruomen said:**
> YESS!!!
Sir, you are the man :P Can I suck your brain to see if i get all this? :P

Everything seems to be working perfectly now.

Can you please tell me what all that meant in english?  I'm a linux newbie so I kind of have an idea of it all but I'm not sure.  Thanks a lot for your help.

Oh, yes one last question.  I have to modprobe -r b44 ndiswrapper ssp etc. to then load b43 so i can get wireless connection everytime I boot the computer.  Is there a way to automate that?

Once again thank you.
If you want an explanation of why that worked, how about first reading post #17 in [this thread]("http://ubuntuforums.org/showthread.php?p=6197790"), and then let me know what questions you might have. :)

Also, about your networking problem, you can add b44, ndiswrapper, ssp or whichever modules you want removed to the module "blacklist" file so they shouldn't get loaded on start up:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And add each module per line in that blacklist file. Then to automatically load the b43 module on start up, you can add it to:
```
gksudo gedit /etc/modules
```
And hopefully that should be all it takes. Let me know how it goes. :)

---

