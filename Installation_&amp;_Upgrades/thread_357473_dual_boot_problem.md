---
title: "dual boot problem"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by nomowindows on 2007-02-09
Hello, i am lost.  i installed ubuntu on another compter with dual boot w/o any problems.  I need windows on one other computer for now. I did a fresh install of window and ubuntu desktop 6.06.  I had ubuntu resize the windows partition and install itself.  when grub loads there is no windows option at all.  There seems to be a correct entry in the /boot/grub/menu.lst file. ( i even checked my other computers menu.lst to compare.)  I hav found/ read most if not all the previous posts that have to do with grub/dual boot.  I have also tried supergrub..it just made things worse,hence the fresh install of both systems.The problem seems to be that grub/ubuntu set the boot drive/partition to its own partition(hd0,1) instead of the windows/first partition(hdo,0). Here are my grub menu and fdisk results. Thank you in advance for your help.

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+   7  HPFS/NTFS
/dev/hda2   *        1217        2441     9839812+  83  Linux
/dev/hda3            2442        2498      457852+   5  Extended
/dev/hda5            2442        2498      457821   82  Linux swap / Solaris
steve@amd-desktop:~$


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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by FractalBrain on 2007-02-09
Hey there!  

So this does not directly answer your question and it wiped out my grub, but it got my windows back.  I had to reinstall linux after that.  I am sure there is a much easier way and probably a way to get grub back, but I HAD to have windows back, and I am new at this.  Ive got two harddrives, the one with Windows is the master IDE...which I guess windows wants to be.  The other one is Kubuntu.  I think the master boot record is on the windows drive.  This is what I did to get the windows boot loader back:

1.  Boot from Windows XP cd and at the begining start up sequence enter the recovery mode.
2.  Type "fixmbr" in at the prompt followed by the drive letter of the boot drive with windows.

aaand I dont remember what happened after that, but windows worked.  I suggest visiting the following URL for Microsofts description of fixmbr:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

Im not sure if this is what you were looking for as a solution, but you might find it helpful if you really need windows....or in fixing the problem.  If someone writes a better solution Ill be bookmarking this thread for sure.  

-Fractal

---

### Post by Herman on 2007-02-09
> I had ubuntu resize the windows partition and install itself. when grub loads there is no windows option at all. There seems to be a correct entry in the /boot/grub/menu.lst file. I agree, that looks okay to me. > The problem seems to be that grub/ubuntu set the boot drive/partition to its own partition(hd0,1) instead of the windows/first partition(hdo,0). I don't think that would be the problem, since grub ususe the 'makeactive' command to move the boot flag around whenever that is required. I see that you have a 'makeactive command there inyoour Windows entry. 
If you want you can move the boot flag with any partitioner though. GParted can do it, or 'Parted > Here are my grub menu and fdisk results. Thank you in advance for your help. I have analysed your fdisk results, here,
nomowindows

```
Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device______Boot______Start______End______Blocks______Id______System
/dev/hda1_________________1_____1216_____9767488+______7______HPFS/NTFS___(hd0,0)
/dev/hda2____*_________1217_____2441_____9839812+_____83______Linux_______(hd0,1)
/dev/hda3______________2442_____2498______457852+______5______Extended
/dev/hda5______________2442_____2498______457821______82______Linux swap / Solaris

``` I can't see any problem there either.

Sorry but I can't see the problem yet, or I'd help you. I'll think it over for a while and get back to you if I have an idea. At the moment I have never heard of that problem happening to anyone before so I am stumped. :confused:

Regards, Herman

---

### Post by Herman on 2007-02-10
Hello nomowindows,
I have an idea you can try, it might work. Try cutting your Windows boot entry from the bottom of your menu.lst and pasting it above the top of your automagic kernels list. 
Maybe it will show up then.
Don't put it inside your debian automagic kernels list though, or it will be deleted every time you get a kernel update. Above or below the automagic kernels list is okay for a boot entry that belongs to a partition other than the Ubuntu one that the grub menu is in.

```
 # menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
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

 # This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/hda1
 title		Microsoft Windows XP Professional
 root		(hd0,0)
 savedefault
 makeactive
 chainloader	+1

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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root 
```

---

### Post by nomowindows on 2007-02-16
thank yall for the replies. i will try that herman. Im new to all this but is is fun learning as i go.:)

---

