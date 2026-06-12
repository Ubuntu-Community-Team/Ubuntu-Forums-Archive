---
title: "GRUB Error 17"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by CroEragon on 2006-12-09
I got a problem with GRUB. I would appreciate your help because i really do not want to use Bill's crap again, 5 years is enough.
First i just wanna say that Ubuntu is best thing that happened to IT world since inventing of rewritable cd-s.
So story goes like this.
I dual-boot instaled Ubuntu on my only comp (P4, Intel Motherboard, XPress integrated graphic card, SATA 160gb hdd, 512RAM) with OEM Windows XP. Thing worked really well. In matter of 40 minutes i installed Ubuntu (resizing C: also) and everithing worked without slightest glitch. 
After that i was messing around with Ubuntu instalation to learn as much as possible so i messed up lot of stuff like resolution, GNOME, KDE and etc.
I succeeded even in messing up Graphic card drivers that worked perfectly fine beafore! So yesterday i decided to reinstall Ubuntu so i can use it more seriously and properly.
Thats where i made mistake. I have basic knowladge of BIOS, partitioning,and computers overall, not just using Windows so i cant explain why i just erased Ubuntu partition, even so i knew i will screw up something. But i did it.
Of course i got GRUB Error 22 and wasnt even able to boot Windows. In my desperate try to enable Windows as fast as possible (rest of family would kill me if i didnt) i reinstaled Ubuntu on my SATA unallocated hd space (i was not able to use Windows rescue cd due to not knowning main administration password).It enabled Windows by rewriting MBR (as i assumed) but brought another GRUB error.
This time it is noumber 17. Cannot mount.
Since then i spent 6 hours straight trying to enable Ubuntu, reinstall GRUB 
and only thing i succeeded was to boot Ubuntu with elp of Super GRUB thing.
It boots my ubuntu with GNU/Linux Boot directly option. I tried to let Super GRUB (it is live cd grub loader with all grub options but little simplified) reinstall and rewrite MBR but nothing. It just wont work without  Super GRUB witch is inconvinient due to using different boot sequence and live cd. So any ideas what i should do next. I cannot just format whole drive or something like that because i musnt lose my windows installation. 
I really want to continue using Ubuntu, but i will be forced to change to Windows if you do not help me. And i really do not want to do that after speech recognition demo. It looks scary.
Any suggestions?

Sorry on my lousy English, it is not my firs language.

---

### Post by bulldog on 2006-12-09
Go back to windows than :D :D 

Give us the outcome of ```
fdisk -l (l as in like)
```
And let us have a look at your menu.lst as well.
```
cat /boot/grub/menu.lst
```

---

### Post by CroEragon on 2006-12-09
No way, windows sux big time, im ashamed that i discovered linux so late!
this is outcome of fsdisc -l:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11749    94373811    7  HPFS/NTFS
/dev/sda2           11750       19293    60597180   83  Linux
/dev/sda3           19294       19457     1317330    5  Extended
/dev/sda5           19294       19457     1317298+  82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         637     5116671    7  HPFS/NTFS
/dev/hdd2             638        2433    14426370    f  W95 Ext'd (LBA)
/dev/hdd5             638        2433    14426338+   7  HPFS/NTFS



and this is menu.lst



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
# kopt=root=UUID=13b33c38-787f-420f-b2de-f49945fce441 ro
# kopt_2_6=root=/dev/sda2 ro

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
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


BTW just to not confuse you i do not have two XP instalations, the professional one is instalation of xp on ide hd from my old comp that i just added to my primary SATA hd in my new computer because of some data on my old hd. also GRUB swaped names of two XP installations. When i choose XP Professional it acctualy loads Home edition that worked even before Ubuntu or old HD and when i try to select Home one it reaturns some error, but i do not care actually, it can stay like that, windows works fine.

---

### Post by bulldog on 2006-12-09
From which disk are you booting [with grub installed to the MBR]
```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=13b33c38-787f-420f-b2de-f49945fce441 ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```
To be sure on what partition is your XP?
I see a boot able NTFS partition on the sda disk and one on the IDE disk.

---

### Post by CroEragon on 2006-12-09
You mean from where i boot ubuntu linux that GRUB cant boot and return error 17?
Im using Super GRUB Live Disc and its option GNU/Linux Direct boot
If you ask about Ubuntu i installed it on same SATA drive where windows(sda2 i think).
If this is useless can you reformat your question?

---

### Post by bulldog on 2006-12-09
When you boot from your computer [no super Grub disk]using the hard disk,which one is set to boot by default?

Reading your story I think your Sata disk is the one,and you added the IDE drive later on.
So if I'm correct,your Sata disk was the original disk which came with your new computer.
You installed XP and Ubuntu on this Sata disk and added later the IDE disk.

Is this correct?

So when you just boot from the hard disk what is happening?
What do you see? and what errors are listed when you choose an option from GRUB?

---

### Post by CroEragon on 2006-12-09
When i turn comp on default selection is Ubuntu. And it reaturns error 17 (recovery mode and memtest also).
You are right about IDE drive. SATA is only one that came with my comp with OEM installation of Windows XP Home. After first installation of ubuntu i added IDE HD from my old comp that was partitioned on C and D partitions in windows. It had installed Windows XP Pro on it that was used on my old comp. Now on reintalation of ubuntu (and GRUB also) it showed my Professional instalation that was used on my old computer. And it mislabeled it. When i select Home it tries to load old professional installation and return error (not 17 one that im talking about, some different error) and when i try to load one labeled Professional it loads Home one on SATA that works fine.

---

### Post by bulldog on 2006-12-09
yes I know al this,but what I **need** to know which disk you're booting from to set the right partitions in your GRUB.

What we are going to do is making a copy of your menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

If you did this replace your menu.lst with the one I change from above.
Save the file as menu.lst.
Then try to reboot and see if it works.

---

### Post by CroEragon on 2006-12-09
From SATA disc where Ubuntu and WinXP Home are. Forget IDE disc. Ignore it, it is not relevant for this. There is no working OS on it.

---

### Post by bulldog on 2006-12-09
See my previous post and try this.
Now the windows XP-home entry should work.

---

### Post by CroEragon on 2006-12-09
It works!!!! Ubuntu and Home entries work perfectly.
Thanks a lot, you saved me relly! I still have some issues with Ubuntu, not related to this problem (my ubuntu keeps freezing when disk starts to spin faster, it shows error with PCI; "Cannot allocate resurce region 3" or somthing like that).
But at last i can boot it properly. Thank again. You see that's what i like about Linux/Ubuntu. You were able to help me on fast, patient way for free and Microsoft wouldnt help me with Windows even thought i have legal copy of windows (OEM, so there is no support).
And you did it on most professional way even so nobody payed you and there is no profit for you in this.
Thanks a lot again!

---

### Post by bulldog on 2006-12-09
Wait till you get the bill :D :D :D 

My pleasure to help you,have fun.

---

