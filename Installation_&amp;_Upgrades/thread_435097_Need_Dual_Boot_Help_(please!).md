---
title: "Need Dual Boot Help (please!)"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by parnelljw on 2007-05-06
Background:

Dell 8100.  Two hard drives.

C: (previuosly Windows ME) - now Ubuntu 6.06
D: win xp.

Prior to ubuntu install - i had dual boot option for ME or XP.  Now, dual boot option is gone and only have Ubunto boot options (regular, recovery and memtest).

How/what is easiest way to recover dual OS boot options.  

I'm an ubuntu TOTAL NEWB - so please be very detailed.

And THANK YOU (my wife's gonna kill me if i don't recover the XP boot option).

---

### Post by jml on 2007-05-06
It is my assumption that you had Windows ME installed on this computer first, then added Widdows XP later as a dual boot option.  And then you removed Windows ME and Installed Ubuntu on ME's partition?  If my assumptions are correct, the problem may be solved by re-installing your OS's in a specific order.  Windows likes to be on the first drive/partition that boots on your computer and it does not play well with GRUB, the boot loader Ubuntu uses.  Windows must be the first OS installed on your computer.  So the first thing I would do would be to back up any data that you do not want to loose.  Then reinstall Windows XP.  If XP says that there is a portion of the hard drive it does not recognize, that will be your Linux partition, (the one with Ubuntu on it.)  If you want you can let the Windows installer reformat that portion to NTFS, the Widdows XP file format, (that wiwll erase everything on the Ubuntu partition.)  After Windows is installed and working, Boot the Ubuntu live/install cd and select the first option offered.  After Ubuntu boots, you can click on the install CD icon to re-install Ubuntu.  Once that is done, and you re-boot, you should have dual boot capability with Widows XP.  Hope that this helps.

Joe

---

### Post by hal8000 on 2007-05-06
Post your /boot/grub/menu.lst file.

It may be just a matter of editing this file.

You also need to state which hard drive is master and which is slave, or if they are on the same connector. Also post the output of

sudo fdisk -l /dev/sda

sudo fdisk -l /dev/hdb

---

### Post by parnelljw on 2007-05-06
thanks Hal.

here's info:

Menu.lst
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
# kopt=root=/dev/hda1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


MY Sda maps to a usb thumb drive (i think) - so i won't post particulars

MY HDB is as follows:
40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
units=cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start        End     Blocks         Id     System
/dev/hdb1 *        1           4865   39078081   55    EZ-Drive


So - a little more detail.  The previous poster was correct in that my C drive, a 60GB drive was the original (and is still master) drive preloaded with Win ME.  I added the 40GB drive at a later time (slave) and subsequently loaded XP to that drive.

Obviously, if i can just change my menu.lst settings or other files - that'd be easiest.

Thank you so much Hal.

---

### Post by hal8000 on 2007-05-06
Hi Parnelljw,

The reason windows isnt booting is because there is no entry in menu.lst........  however this may not be the end of your problems.

Ubuntu has been installed on the first partition of your first drive   hd0,0 or hda1, this is what windows would call C: drive, so you may have inadvertently wiped out windows.

If however the drives have been swapped and your think windows is on the slave drive then include the following lines modify menu.lst including a windows stanza as follows


title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
boot


title Windows XP
 root (hd1,0)
 makeactive
 chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST


You may find it easier to use gedit so try

gksu  gedit /boot/grub/menu.lst

and copy the lines above into grub. Windows always wants the first partition so the lines would try and load windows from partition 1 on the second hard drive, hdb1 or hd1,0 in grub terms.
Hope that helps

---

### Post by parnelljw on 2007-05-06
thanks Hal.

I'm quite confident that I installed XP on it's own drive.  

XP is now an option within the GRUB boot options, but rec'd the following error message when selecting XP

"invalid system disk
replace the disk, and then press any key"

any ideas?

---

### Post by confused57 on 2007-05-06
> **parnelljw said:**
> thanks Hal.

I'm quite confident that I installed XP on it's own drive.  

XP is now an option within the GRUB boot options, but rec'd the following error message when selecting XP

"invalid system disk
replace the disk, and then press any key"

any ideas?

You might need a couple of mapping lines:
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by louieb on 2007-05-06
I like confused57 believe you need to re-map your drives. (this will fake XP out and make it think its on the 1st drive).   
What I want you to do is unplug any external drives. Then list the partition table.
Open Applications>Accessories>Terminal ```
sudo fdisk -lu
```  copy and paste the output here. it should look something like this: 
```

lou@gameu:~$ sudo fdisk -lu
Password:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63      128519       64228+  83  Linux
/dev/hda2          128520      915704      393592+  82  Linux swap / Solaris
/dev/hda3          915705    21398579    10241437+  83  Linux
/dev/hda4        21398580    58621184    18611302+  83  Linux

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    16482689     8241313+   7  HPFS/NTFS
lou@gameu:~$


```If it look something like the above then try this menu.lst entry
```

title Win XP Home
                map (hd0) (hd1)
                map (hd1) (hd0)
                rootnoverify (hd1,0)
                makeactive
                chainloader +1
                boot


```Both the fdisk and the menu.st entry are from a  PII 400 with Ubuntu on master and XP on slave.
If things look very different or it doesn't work post back with the partition table listing from fdisk.

---

### Post by tubeamp on 2007-05-07
Hi,
This is what I have added to menu.lst to boot into Win XP from Grub. (Windows is on Primary IDE master, Ubuntu and Grub on Second IDE Master (hdc)):_


title Win XP Home
unhide (hd1,0)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
boot

Hope this might help. (Ubuntu was installed with Windows drive disconnected from PC)

---

### Post by parnelljw on 2007-05-12
Hi louieb - thanks for your help.  would've responded sooner but was traveling and trying to carry around a Dimension 8100 on a plane doesn't work well (hey...maybe that's why they make laptops!)

you asked for partition table.

here it is

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   117081719    58540828+  83  Linux
/dev/hda2       117081720   120101939     1510110    5  Extended
/dev/hda5       117081783   120101939     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    78156224    39078081   55  EZ-Drive


The 40GB drive (hdb) is the WinXP drive.

anyone's help is greatly appreciated.

---

### Post by confused57 on 2007-05-12
If you had a pen drive connected when you installed Ubuntu, you might want to post the output of:
```
gedit /boot/grub/device.map
```

Since your XP drive(hdb)  was dual booting OK with ME on hda, I would assume your bios hard drive controllers are enabled or set to "auto".

---

### Post by louieb on 2007-05-12
> **parnelljw said:**
> 
/dev/hdb1   *          63    78156224    39078081   **55  EZ-Drive**
The 40GB drive (hdb) is the WinXP drive.

I've got no clue what a partition type of 55 E-Z-Drive is never seen one.  
Did a Google of **55 e-z-drive **you may want to do the same. It appears to be some private brand of NTFS. Don't have a clue if GRUB can boot to it. 
But here is a little info on it.
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-1.html")

---

### Post by parnelljw on 2007-05-12
thanks louie.

hey, a question though...what if i bought something like magicboot? or someother boot app?  any ideas if that'd help?

---

