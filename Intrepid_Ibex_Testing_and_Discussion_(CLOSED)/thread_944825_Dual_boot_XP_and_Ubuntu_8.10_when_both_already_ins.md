---
title: "Dual boot XP and Ubuntu 8.10 when both already installed"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chromejs10 on 2008-10-11
Wasn't really sure where to put this but here is my problem.

I already have Ubuntu 8.10 installed on one partition of my laptop. Then I popped in the Windows XP CD and installed Windows on a separate partition. Whenever I boot up it goes into windows. 

My question:
How do I make it so that I can dual boot between the two? Right now in Windows, it isn't showing the Linux partition so that I can select it as default.

How can I make it so that every time i restart/bootup my computer, a menu will come up asking me if I want to boot into linux or windows? 

Thanks a lot for any help!

*NOTE: when I installed windows XP, it told me it was going to deactivate the other partition (Linux) and said I would have to reactivate once I finish installation.

---

### Post by geirha on 2008-10-11
Windows isn't so friendly towards linux. When you install Windows, Windows will overwrite the master boot record (mbr), and only allow itself to boot. Not too hard to overwrite the mbr with grub again though. Read [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by chromejs10 on 2008-10-11
> **geirha said:**
> Windows isn't so friendly towards linux. When you install Windows, Windows will overwrite the master boot record (mbr), and only allow itself to boot. Not too hard to overwrite the mbr with grub again though. Read [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

alright i've give that a try thanks.

---

### Post by chromejs10 on 2008-10-11
I did all the quickstart stuff and now it boots directly up into ubuntu without any option of going into windows. I then followed the 

6. If, after installing grub, Windows will not boot you may need to edit /boot/grub/menu.lst (That is a small "L" and not the number 1 in menu.lst) 

but still nothing.

In the part that said: 

Type the following and press enter:
find /boot/grub/stage1

Using this information, set the root device:
grub> root (hd0,1)

the find showed (hd0,0) so i changed the second line to grub> root(hd0,0). Is that correct?

---

### Post by caljohnsmith on 2008-10-11
You don't need to run those grub commands if you can successfully boot into Ubuntu; the only thing you need to do is add to your menu.lst an entry for Windows. If you want help with that, please post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by chromejs10 on 2008-10-11
***@***-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbd669df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   146480669    73240303+  83  Linux
/dev/sda2   *   146480670   232476614    42997972+   7  HPFS/NTFS
/dev/sda3       232476615   234436544      979965   82  Linux swap / Solaris

Disk /dev/sdb: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders, total 192426570 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   192410504    96205221    7  HPFS/NTFS



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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=2409f365-f522-4913-854d-fee11acc3bae ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

 title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
 rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
 makeactive
 chainloader +1

---

### Post by caljohnsmith on 2008-10-11
OK, open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And where it says "hiddenmenu", put a pound sign in front of it:
```
#hiddenmenu
```
Next change the Windows entry at the end of the file to:
```
title Windows XP
rootnoverify (hd0,1)
chainloader +1
```
Save, quit gedit, reboot, and let me know what happens. :)

---

### Post by chromejs10 on 2008-10-11
> **caljohnsmith said:**
> OK, open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And where it says "hiddenmenu", put a pound sign in front of it:
```
#hiddenmenu
```
Next change the Windows entry at the end of the file to:
```
title Windows XP
rootnoverify (hd0,1)
chainloader +1
```
Save, quit gedit, reboot, and let me know what happens. :)

Thanks a lot. The menu now comes up (but it also shows like 8 things for Ubuntu, what is all that? and do i need it?)

The only thing, the menu only shows up for like 1 second, not enough time to change to Windows XP. Is there a way to make it appear for a longer time?

Thanks a lot.

---

### Post by caljohnsmith on 2008-10-11
> **chromejs10 said:**
> Thanks a lot. The menu now comes up (but it also shows like 8 things for Ubuntu, what is all that? and do i need it?)

The only thing, the menu only shows up for like 1 second, not enough time to change to Windows XP. Is there a way to make it appear for a longer time?

Thanks a lot.
Sure, in your menu.lst, just change the line "timeout 3" to however much time you want in seconds, like maybe 10 seconds:
```
timeout 10
```
Also, to restrict the number of kernels that show up in the Grub menu (those are all the Ubuntu entries you are referring to), if I remember correctly all you need to do is change the "#howmany" line to:
```
#howmany 2
```
That will show only two kernels in the Grub menu, but you have to save the file and then do:
```
sudo update-grub
```
In order for the change to actually happen. Try that, and after running the update-grub command check the menu.lst again to make sure it doesn't show all those entries for Ubuntu. Then reboot, and let me know how it goes. :)

---

### Post by chromejs10 on 2008-10-11
> **caljohnsmith said:**
> Sure, in your menu.lst, just change the line "timeout 3" to however much time you want in seconds, like maybe 10 seconds:
```
timeout 10
```
Also, to restrict the number of kernels that show up in the Grub menu (those are all the Ubuntu entries you are referring to), if I remember correctly all you need to do is change the "#howmany" line to:
```
#howmany 2
```
That will show only two kernels in the Grub menu, but you have to save the file and then do:
```
sudo update-grub
```
In order for the change to actually happen. Try that, and after running the update-grub command check the menu.lst again to make sure it doesn't show all those entries for Ubuntu. Then reboot, and let me know how it goes. :)

Worked like a charm. Thanks so much! Man...how do you guys know all this. lol

---

### Post by bodhi.zazen on 2008-10-11
> **chromejs10 said:**
> Worked like a charm. Thanks so much! Man...how do you guys know all this. lol

ancient Chinese secret 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

