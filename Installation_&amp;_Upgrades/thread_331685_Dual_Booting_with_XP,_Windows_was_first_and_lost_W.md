---
title: "Dual Booting with XP, Windows was first and lost Windows"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by dragondef on 2007-01-04
I started out with two 120 g hard drives. I do believe that they are IDE. I just lost my last drive, and decided that I wanted to upgrade to XP, and go into Ubuntu. I installed Windows XP in the first drive. Works okay, had to install all of my drivers, get the three monitors going. Then, I started Ubuntu 6.10. I got it up and working, a and loved that I didn't have much problems. I couldn't get the three monitors and beryl working, but that was fine with me. I then rebooted my computer, and Grub didn't have Windows, or didn't even show up. Well, I found some forums that said to put this in the grub menu

     title           Windows
     root            (hda2,0)
     savedefault
     makeactive
     map             (hd1) (hd0)
     map             (hd0) (hd1)
     chainloader     +1

. I did, and still it didn't work. Grub said that the partition didn't exist, then I decided to look for the drive, and found 


     Disk /dev/hda: 203.9 GB, 203928109056 bytes
     255 heads, 63 sectors/track, 24792 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes

        Device Boot      Start         End      Blocks   Id  System

     Disk /dev/hdb: 122.9 GB, 122942324736 bytes
     255 heads, 63 sectors/track, 14946 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes

             Device Boot      Start         End      Blocks   Id  System
     /dev/hdb1   *           1       14570   117033493+  83  Linux
     /dev/hdb2           14571       14946     3020220    5  Extended
     /dev/hdb5           14571       14946     3020188+  82  Linux swap / Solaris

     Disk /dev/sda: 2047 MB, 2047868416 bytes
     255 heads, 63 sectors/track, 248 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes

        Device Boot      Start         End      Blocks   Id  System
     /dev/sda1               1          10       80293+   0  Empty
     /dev/sda2              11         248     1911735    b  W95 FAT32


I can't make any sense but that the sda is my Ipod, and hdb is my linux drive. I think that the hda is empty, and if so, help. If this is the case, then could you tell me how to reinstall windows, and add the grub to get back this linux. I don't want to lose this linux. I can handle reinstalling Windows, because I need it for programming with Microsoft Visual Studios.

If I didn't lost it, then I need to know how to fix this issue, what do I do?

---

### Post by confused57 on 2007-01-04
I assume you're booting first to hdb, which would be root (hd0,0) in grub...if this is the case you could try using a Windows entry similar to this in your /boot/grub/menu.lst:

title Windows
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

You might want to post the output of:
```
cat /boot/grub/menu.lst
```

you'd just need to post the entries for booting Ubuntu & Windows...I'm not sure why your hda isn't showing any partition table.

---

### Post by dragondef on 2007-01-05
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=0d443edf-de28-4f1c-8f77-ce5a3d6559bf ro
# kopt_2_6=root=/dev/hdb1 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot


title Windows
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST








This is what cat /boot/grub/menu.lst. I really would like to get the windows back someway.

---

### Post by bulldog on 2007-01-05
It seems you boot from the windows disk and GRUB is installed into the MBR of that disk.
You can see it at your ubuntu partition,which refers to hd1.
So you won't have to map your windows.

Make your windows entry exactly like this one with all the other info above it.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
#on /dev/hda0
title Windows
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

Can't guarantee your windows will boot,because I actually can't see a windows install,but give it a try.
Otherwise you have to reinstall windows,and after that we can reinstal GRUB to the second hdd,if you want to do so.

If you do,I advice you to make the Ubuntu hdd your master boot device so your GRUB will be visible at boot and you can choose the OS you want to start up.

---

### Post by dragondef on 2007-01-05
Okay, thanks for the help, and no luck. I think that I can reinstall the Windows on the secondary. But, how would I reinstall the GRUB. I think it might be in the cd, but I don't know where to look or know what commands to use. And should I install Windows with the Ubuntu in the Drive, or disattach the thing, install windows, and then put it back as the master drive?

---

### Post by bulldog on 2007-01-05
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

Keep in mind setup (hd0) command puts GRUB on the master boot device,if you want it on the second disk you have to make the setup command (hd1)

---

### Post by sdowney717 on 2007-01-05
Hi,
If you want to get rid of grub entirely. then boot from xp cd into recovery console prompt mode and at the prompt type in FIXMBR. This will write a genuine MBR just for windows and you could see if windows will boot again. 
I am running FC6, ubunuts, and XP off grub.
IN FC6 to fix grub, you boot recovery disk 5, 
type
chroot /mnt/sysimage
grub-install --recheck /dev/hda
exit

then it rewrites grub. But will this work in ubunuts? I dont know.

My Xwindows in Ubunuts is really flaky, sometimes it boots all the way, sometimes Xwindows wont come up and I dont know why. any ideas?

---

