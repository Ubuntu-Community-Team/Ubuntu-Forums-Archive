---
title: "[SOLVED] dual boot xp (sorry to make a new one but ive tried all the other threads)"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by roy430 on 2008-09-25
STORY SO FAR:
Had XP installed on the first partition on the slave hard drive. 
Installed Ubuntu on second HDD (dont recall what partition)

Then I could no longer boot into XP, wasnt in grub list, tried editing the list file, couldnt get it too boot. So ended up running the fixmbr command off of a windows xp install cd recovery prompt. This caused the computer to say 'invalid partition table'. 
I then ran a few partition apps and got a 'NTLDR is missing, ctrl+alt+del to restart' error on boot. Then downloaded and ran this bootdisc [http://ntldrismissing.com](http://ntldrismissing.com)  and am currently using its boot manager (i think). But at least im able to boot XP now. So then I wiped the second drive, installed ubuntu on the first hdd first partition (sda1 yeah?) and put the grub thing in that partition as i was following a guide which had me copy /boot/grub/stag1 to d:\ubuntu.ini (d is my windows drive) and add that to my boot.ini. However if select my linux option it just freezes for a few seconds then restarts, if i then choose the linux option a 2nd time in a row i get a hal.dll error.  

Umm i will try to get a print out of the partition setup next. 

Also - i have been through this thread
[http://ubuntuforums.org/showthread.php?t=908157&highlight=dual+boot&page=2](http://ubuntuforums.org/showthread.php?t=908157&highlight=dual+boot&page=2)
and it has not helped, i am still stuck using this windows boot manager...

Any help would be greatly appreciated, 
Geoff.

Partition set up:
[http://i33.tinypic.com/2lc1yjl.jpg](http://i33.tinypic.com/2lc1yjl.jpg)

Any more information required? I tried to get it all in...sure i forgot something.

---

### Post by caljohnsmith on 2008-09-25
The method you describe of adding the Ubuntu Grub boot loader to your Windows boot.ini file is really not necessary in your case I think; or at least it's not necessary until we know for sure that Windows can't be booted from Grub on your Ubuntu drive, which we don't know yet. And I've only seen a few rare cases where Windows would not boot with Grub but would with the Windows boot loader.

Since you have Windows and Ubuntu on separate drives, can you set your BIOS to boot the Ubuntu drive first? If you can do that, then you could install Grub to the MBR (Master Boot Record) of your Ubuntu drive, and then we can add Windows as an entry to your Grub's menu to make it accessible too. With that setup you would always boot your Ubuntu drive, but the Grub menu would give you a choice of either Ubuntu or Windows. Does this sound workable for you?

Also, for completeness, please post the output of:
```
sudo fdisk -lu
```

---

### Post by roy430 on 2008-09-25
That sounds great. I have swapped the boot order and it still just jumps to the windows boot manager thingo. 

Will grab now (via rescuae disc?)
Thanks for reply.

Also - I have removed the HDD that contains windows and it just gets boot failed, please insert system disk error. but that could be due to the wrong cable set up/boot order and stuff...

(heres fdisk -lu output...took me a while to remember how to mount the fat32 drive from the rescuecd so i could use that as a dropbox) 


Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf183f183

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+  83  Linux
/dev/sda2        62910540    67103504     2096482+  82  Linux swap / Solaris
/dev/sda3        67103505    77593949     5245222+   b  W95 FAT32
/dev/sda4        77593950   312576704   117491377+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x804263cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   102414374    51207156    7  HPFS/NTFS
/dev/sdb2       102414375   312576704   105081165    f  W95 Ext'd (LBA)
/dev/sdb5       102414438   312576704   105081133+   7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-09-25
OK, to make sure you have Grub installed in the MBR of your Ubuntu drive, boot your Live CD, open a terminal (applications > accessories > terminal) and do the following:
```
sudo grub
grub> find /boot/grub/stage1
```
The above command should return your Ubuntu partition in the form of (hdX,Y), for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Next do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda1 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
If you have any problems with the above steps, let me know. Otherwise be sure to post the output of all the above steps.

---

### Post by roy430 on 2008-09-25
Ok will try now, by live cd (thats just booting off the ubuntu cd yes?) sorry im a bit new to all this linux.

btw- fdisk -lu output is above.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf183f183

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+  83  Linux
/dev/sda2        62910540    67103504     2096482+  82  Linux swap / Solaris
/dev/sda3        67103505    77593949     5245222+   b  W95 FAT32
/dev/sda4        77593950   312576704   117491377+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x804263cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   102414374    51207156    7  HPFS/NTFS
/dev/sdb2       102414375   312576704   105081165    f  W95 Ext'd (LBA)
/dev/sdb5       102414438   312576704   105081133+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=dcbbd9eb-4b35-4875-90a6-0f9171305b65 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=dcbbd9eb-4b35-4875-90a6-0f9171305b65 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=dcbbd9eb-4b35-4875-90a6-0f9171305b65 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by caljohnsmith on 2008-09-25
> **roy430 said:**
> Ok will try now, by live cd (thats just booting off the ubuntu cd yes?) sorry im a bit new to all this linux.

btw- fdisk -lu output is above.
Yes, the Ubuntu CD is sometimes called a "Live CD." :) By the way, how did you post "sudo fdisk -lu"? Are you able to boot into your Ubuntu install on your HDD? If so, how are you doing it?

---

### Post by roy430 on 2008-09-25
no i have a linuxrescue disc that i borrowed from someone, and then i did
mkdir /mnt/osshare
mount -t vfat /dev/sda3 /mnt/osshare
fdisk -lu > /mnt/osshare/fdisk.txt

Then rebooted into windows and posted it.

---

### Post by caljohnsmith on 2008-09-25
OK, try booting your Ubuntu HDD and let me know exactly what happens on start up. If you get the Grub menu, try Ubuntu and let me know what happens.

---

### Post by roy430 on 2008-09-25
ok  -  if i actually physically disconnect my XP HDD it boots into ubuntu- currently doing some drive checking due to unclean shutdown apparently. 
- ill try and reconnect XP drive and swap boot order around in bios again..

almost there i think -THANKYOU SO MUCH- Im currently booting into ubuntu bia grub with both HDD connectected, just have to restart and make sure XP is accessible.

WOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!
btw- it worked :P
Just a few quick question how do i change default item on grub menu?

---

### Post by caljohnsmith on 2008-09-25
That's great news you can boot either Ubuntu or Windows now from the Grub menu. :) To change the default OS that Grub boots, just change the line near the top of your menu.lst that has "default 0" right now. Keep in mind that Grub's numbering starts with 0 instead of 1, so "default 0" means the 1st OS in the Grub menu, "default 1" means 2nd OS, etc. When you are in Ubuntu, to edit the menu.lst just do:
```
gksudo gedit /boot/grub/menu.lst
```
Anyway, cheers and have fun. :)

---

### Post by roy430 on 2008-09-25
Ah cool, thanks very much :D

---

