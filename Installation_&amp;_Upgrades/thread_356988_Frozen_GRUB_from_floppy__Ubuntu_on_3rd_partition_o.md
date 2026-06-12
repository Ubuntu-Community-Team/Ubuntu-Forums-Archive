---
title: "Frozen GRUB from floppy / Ubuntu on 3rd partition of 1st disk"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by picsis on 2007-02-09
Hello,

First of all I apologize if this thread exists already. I did a search about my problem but all I find is people having GRUB installed on MBR.


I'll explain my case:

Long time ago I installed Ubuntu Breeze on 3rd partition of first disk (an IDE disk)

My disks are distributed like:

Disk 1 (40 GB IDE):
Partition 1  Windows 2000 (fat32) 12GB
Partition 2  BLANK (fat32) 12GB (i was going to install xp, but never did)
Partition 3  Ubuntu (/) (reiserfs) 13GB
Partition 4  Swap 1.6 GB

Disk 2 (80 GB SATA) NOT RELEVANT BUT I NAME IT
Divided in 3 fat32 partitions

The thing is that when I first installed Ubuntu, I didn't want (and I still don't want) to install GRUB on MBR, so what I did was a simple copy of GRUB folder to "/boot/grub" on a floppy disk. I dont even remember how I did it (long time ago), but the contents of the floppy are:

/boot/grub/stage1
/boot/grub/stage2
/boot/grub/menu.lst

This worked great for about 5 months now. When I wanted to start Ubuntu, I just entered the floppy and everything went just great. I use Ubuntu from time to time but I am still a newbie.

Ok, I had about one week withouth using Ubuntu and about 3 days ago I tried to access it and all I received was a frozen GRUB screen (just the word GRUB literaly displays) and the same goes every single time I tried to load it.

The only change I have made to the system is to change partition2 (BLANK) which was an extended partition to a primary partition. I mean, now I have 2 primary partitions on disk1

I have tried loading live cd and accesing the Ubuntu installation on HD and copying the /boot/grub directory again to another floppy with success, but the same happens, I get a frozen GRUB.

Is there something I'm missing?

I'm copying my menu.lst contents below:

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST



Again, I apologize if this has been discused before but I didn't find anything related to this.

Thank you in advance for your help

---

### Post by logos34 on 2007-02-09
My guess is that your root parition was renumbered when you converted the extended to a primary.  If so you need to edit menu.lst--root, kernel and groot lines

Check it by booting from the livecd and running
> sudo fdisk -l

Or open up gparted and have a look.

Not sure this line is right either (shouldn't it be 'hda3'?):
# kopt=root=/dev/**hdc3** ro

---

### Post by picsis on 2007-02-09
> **logos34 said:**
> My guess is that your root parition was renumbered when you converted the extended to a primary.  If so you need to edit menu.lst--root, kernel and groot lines

Check it by booting from the livecd and running


Or open up gparted and have a look.

Not sure this line is right either (shouldn't it be 'hda3'?):
# kopt=root=/dev/**hdc3** ro

Hi, thank you for your reply.

Yes # kopt=root=/dev/**hdc3** ro was wrong, I changed although it didn-t make any harm because it was commented.

Here is what fdisk returned and gparted had to say the same, I think everything is right except neither gparted or fdisk says what about partition number, the one that goes inside root and groot, so Im not sure if  that is ok having them on hd0,2.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1567    12586896    c  W95 FAT32 (LBA)
/dev/hda2            1568        3134    12586927+   c  W95 FAT32 (LBA)
/dev/hda3            3135        4835    13663282+  83  Linux
/dev/hda4            4836        5005     1365525   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896    c  W95 FAT32 (LBA)
/dev/sda2            1568        5648    32780632+   c  W95 FAT32 (LBA)
/dev/sda3            5649        9729    32780632+   f  W95 Ext'd (LBA)
/dev/sda5            5649        9729    32780601    c  W95 FAT32 (LBA)

Everything seems to be fine, any other idea? Did I just messed up my Ubuntu install? I can access it by mounting it from live cd so I guess and hope not. 

Thanks again

---

### Post by logos34 on 2007-02-09
> Device Boot Start End Blocks Id System
/dev/hda1 * 1 1567 12586896 c W95 FAT32 (LBA)
/dev/hda2 1568 3134 12586927+ c W95 FAT32 (LBA)
/dev/hda3 3135 4835 13663282+ 83 Linux
/dev/hda4 4836 5005 1365525 82 Linux swap / Solaris

Ok, so it didn't change the numbers...The reason I guessed so is because that's what happened to me a week ago when I reinstalled winxp and repartitioned the disk with an extended partition, the difference apparently being that I ADDED an extended partition (one logical inside) between my primary ntfs (hda1) and linux partitions (hda2 and 3), so it changed my ubuntu / from hda3 to hda4.  In your case you just converted/reformatted an existing partition so it didn't need to change any numbers.

The problem is apparently not the media, because you've tried a different floppy...What about if you change it to boot the older kernel (2.6.12-9-686)?  Try changing the 'default 0' line to 'default 2' just to see if does anything.

You could also do a filesystem check of hda3.  Boot from ubuntu livecd and run 
> sudo fsck /dev/hda3
or
sudo fsck.reiserfs /dev/hda3

If you can access your root partition from the livecd then the situation is not too dire.  But do a backup anyway just in case you end up having to reinstall.

---

### Post by dannyboy79 on 2007-02-09
justr because your kopt line is commented doesn't mean it's not used. my kopt line is commented as well. i have my ubuntu installed on my third hard drive (hdc). this is my grub entry. not all files in linux that have a # doesn;t neccessarily mean it's commented out!

# kopt=root=/dev/hdc2 ro noapic

---

### Post by picsis on 2007-02-10
Hello again

I finally could enter Grub. I just installed WinGrub and now the screen shows up so it seems it was the diskettes I was using, or WinGrub made a miracle, hehehe.

The problem now, which I can't figure out, is that when I try load Ubuntu through regular menu entries (not recovery) it always shows Disk Read Error 26

But if I hit any of the Recovery modes listed, it loads fine.

I'm pasting my menu.lst again so you can check if there is any error there:

```
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Please let me know if you see something particular that could be throwing this error-

Thanks again

---

### Post by dannyboy79 on 2007-02-10
did you boot from a live cd and run a fsck on your UNMOUNTED linux partition. I would sugest this. i tried looking up what error 26 meant for wingrub but din't find anything. I would suggest going back to normal grub. you can install grub on the frist partition instead of on the windows hard drive mbr, you can use he super grub disk to do this for ya, it's an awesome disc and I bet will actually be able to get you booted into linux as it has that option as well. similar to you booting froma floppy previously you could always boot from this cd and go to windows or linux. good luck. here a link to the sgd.[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

