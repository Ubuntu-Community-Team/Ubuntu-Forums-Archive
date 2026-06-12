---
title: "Installed Xubuntu 7.10 (UserOS ULTRA), Windows crashes"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by gilbs on 2008-02-24
I recently obtained a copy of a customised version of Xubuntu 7.10 called UserOS ULTRA, which came with the March 2008 issue of PC User magazine. I installed it, intending to dualboot with XP. It works perfectly fine, except now when I start XP and I log on, and after several seconds - sometimes even a minute, the screen goes black for a moment and then reappears usually as a white screen with black dashes throughout.

My specs are as follows:

Intel Pentium 4 Prescott 3.0GHz (Socket 478)
EPoX 4PDA3-I3 Motherboard ICH5 Southbridge, i865PE chipset
NVIDIA 7600GT 256MB AGP 8x
19" BenQ FP91W-B Widescreen LCD Monitor
Channel 0 Master: (sda) 80GB WD IDE HDD (contains XP and files)
Channel 0 Slave:  (sdb) 40GB WD IDE HDD (contains xubuntu)
Channel 1 Master: LG DVD-RW
Channel 2: (sdc) 80GB WD SATA HDD (contains files)

I can access all of my files through Linux. I have never had this problem before, and it can be stalled by ending half of the processes through task manager in Windows (including explorer.exe).

Any help would be much appreciated.
-Gilbs

---

### Post by Pumalite on 2008-02-24
Let me see the entry for XP in your menu.lst

---

### Post by gilbs on 2008-02-24
This is probably the wrong section of it since I am new to linux but this is what I found:

# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Pumalite on 2008-02-24
Make it like this:

# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
map  (hd0,0) (hd1,0)
map  (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

Save exit and reboot.
Make sure you make a copy of menu.lst before editing.

---

### Post by gilbs on 2008-02-24
I did as you said but the loader got stuck on "Starting up..." after I chose Windows XP.

---

### Post by Pumalite on 2008-02-24
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by gilbs on 2008-02-24
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x82e082e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   156296384    37190475    f  W95 Ext'd (LBA)
/dev/sda5        81915498   156296384    37190443+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x069cca99

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74862899    37431418+  83  Linux
/dev/sdb2        74862900    78156224     1646662+   5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0de9a395

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   156296384    78148161    7  HPFS/NTFS
gilbert@Lynx:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b27aeb24-46bf-4bf9-a507-4ac2c4ef14a7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b27aeb24-46bf-4bf9-a507-4ac2c4ef14a7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b27aeb24-46bf-4bf9-a507-4ac2c4ef14a7 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Pumalite on 2008-02-24
You installed Grub to it's partition or with the XP drive disconnected.

---

### Post by PmDematagoda on 2008-02-24
About the Windows partition, can you properly mount and read/write to it with no problems?

---

### Post by Pumalite on 2008-02-24
You can use Super Grub to boot XP: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by gilbs on 2008-02-24
@PmDematagoda:
Yes, I can read and write to the windows partition perfectly fine

@Pumalite:
Is there anyway to fix this? If not, thanks for trying.

---

### Post by Pumalite on 2008-02-24
See my post.

---

### Post by Pumalite on 2008-02-24
You can also reinstall Grub to the MBR with XP connected:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by gilbs on 2008-02-26
I'm confused about the MBR with XP connected thing. How do I connect XP and why was it not connected already? I'm unsure which section of the thread you referred me to I am supposed to perform.

---

### Post by Pumalite on 2008-02-26
For what I see, all Windows stuff is in sda, Linux in sdb. The question is: when you installed: did you have sda connected?
-Did you use Super Grub? Were you able to boot Windows? Did you reinstall Grub to MBR (sda)?

---

### Post by gilbs on 2008-02-26
I used super grub to start windows (I chose the option that said WIN & MBR). It seems to work alright, although I'm not sure if that is because I ended some processes or because it's been fixed. When I turn on my computer now, it goes straight to windows i.e. it skips grub.

How do I tell whether the drive is connected? Does that just mean I have to mount it in linux, and then install grub to it?

---

### Post by Pumalite on 2008-02-26
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

