---
title: "GRUB Dual Boot"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by Zeek00 on 2007-01-19
I have recently rebuilt my computer. I'm running Ubuntu Edgy and windows XP. I installed each OS to a different harddrive in my computer. Maxtor 60GB for Linux, Seagate 20GB for windows. To install windows I had to make the seagate the Master Harddrive and after installing it switch it to slave.

How do I get GRUB to allow me to boot into windows? I installed windows first then Linux. But when I get the GRUB boot screen and choose Windows XP I get an error. Any help?

Zeek

---

### Post by logos34 on 2007-01-19
Post your /boot/grub/menu.lst and device.map files.  

And /etc/fstab.

---

### Post by Zeek00 on 2007-01-19
menu.lst :
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
# kopt=root=UUID=6b5ab9c7-4d3d-460e-a1b4-bdbfb1f785b7 ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

device.map :

```
(hd0)	/dev/hda
(hd1)	/dev/hdb

```

---

### Post by logos34 on 2007-01-19
/etc/fstab too, if you could.

---

### Post by Sefrin on 2007-01-19
I have two drives, the master for my windows system, and the slave for NTFS "storage" and over half the rest for my Ubuntu.  Ubuntu doesn't seem to care and Windows always wants to run a check disc after Ubuntu runs but that's what "press any key to cancel" is for.  :biggrin:

---

### Post by logos34 on 2007-01-19
> title	Microsoft Windows XP Home Edition
root    (hd1,0)

Try instead
> rootnoverify (hd1,0)

---

### Post by Zeek00 on 2007-01-19
yes, because that makes plenty of sense what to do....:roll:

What exactly did you want me to do to that file? Little more specific if you could.

---

### Post by Zeek00 on 2007-01-19
> **Sefrin said:**
> I have two drives, the master for my windows system, and the slave for NTFS "storage" and over half the rest for my Ubuntu.  Ubuntu doesn't seem to care and Windows always wants to run a check disc after Ubuntu runs but that's what "press any key to cancel" is for.  :biggrin:

So what help are you offering?

---

### Post by logos34 on 2007-01-19
> yes, because that makes plenty of sense what to do....

What exactly did you want me to do to that file? Little more specific if you could

In a terminal type:
sudo gedit /boot/grub/menu.lst

then edit the line I referred to above, save it and close.  Reboot and see if you can boot into windows.  

Did you add your windows disk to the fstab file I referred to above?

---

### Post by Zeek00 on 2007-01-19
Don't know How. But the harddisk is already recognized by linux. Mounts it upon startup.

---

### Post by logos34 on 2007-01-19
> Don't know How. But the harddisk is already recognized by linux. Mounts it upon startup.

Then it's already in fstab.

Go to Applications>Accessories>Terminal.

Type
> sudo gedit /boot/grub/menu.lst

Then change the word 'root' to 'rootnoverify'.  

Try it.  May or may not work.  As the Grub page says, 'People with more than one hard disk seem more prone to GRUB problems...'

---

### Post by Zeek00 on 2007-01-19
No, I don't believe it is. Seeing how as when i rebooted and tried to boot into windows I got this:

Error (some #) Device selected not in list.

I also did change the menu.lst file to what was stated earlier.

---

### Post by logos34 on 2007-01-19
> No, I don't believe it is.

What, you don't believe it's in fstab?  But you say it's mounting automatically.  

Can you just post the fstab?

Your grub file looks correct...The root partitions for linux and windows check out and it's got the double 'map' lines critical to get windows to boot on a non-first hard disk.

---

### Post by Zeek00 on 2007-01-19
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6b5ab9c7-4d3d-460e-a1b4-bdbfb1f785b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=40A5-E604  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=9e89056a-d46c-4058-859d-b80085407127 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by logos34 on 2007-01-19
well, hdb1 is there as I thought...You can change 'rootnoverify' back to root because that's not the problem (I assumed this was a ntfs partition, but you've formatted it as fat32)...What about setting the windows slave drive to boot first in bios...can you boot into winxp that way, or did grub somehow mess up the windows bootloader during Ubuntu install?

---

### Post by Zeek00 on 2007-01-19
Well, this is what I did. I had windows XP and Linux on one drive, the 60 gig. I got a 20gig from a friend and decided to move windows over. Windows wouldn't recognize the drive unless I made it Master. As long as i kept it Master i would boot onto it.

When i switched it back to slave and reconnected my 60 gig as the Master and reinstalled linux on that drive. I could only boot into linux and when choosing windows I get that error. So I really don't know what the hell is going on.

---

### Post by logos34 on 2007-01-19
wait, there may be a spacing problem in the menu.lst.  Retype the 'map' lines and hit the space bar once between (hd0)  (hd1).  So your entry will look like this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0)  (hd1)
map		(hd1)  (hd0)
chainloader	+1

---

### Post by Zeek00 on 2007-01-19
There was already only one space.

---

### Post by logos34 on 2007-01-19
> Error (some #) Device selected not in list.
Or is the error you get 'Device not found' or 'Selected disk does not exist'?

> When i switched it back to slave and reconnected my 60 gig as the Master and reinstalled linux on that drive. I could only boot into linux and when choosing windows I get that error. 

You're referring only to the grub menu here?  What about setting the windows slave drive to boot first in the BIOS boot disk priority, so you boot straight into windows, not grub?

---

### Post by logos34 on 2007-01-19
And if that doesn't work, the only other suggestion I have is that you switch the windows 20GB drive back to master and try that arrangement...maybe your windows just refuses to boot from slave position.

---

### Post by Zeek00 on 2007-01-19
I think your right with the Selected Disk does not exist. But setting the Boot BIOS to boot to the slave would only put a Band aide on the problem. I'd rather solve it.

---

### Post by logos34 on 2007-01-19
You might want to go through [this page]("http://users.bigpond.net.au/hermanzone/p15.htm") to see if there is anything you can do to grub to make it boot windows (assuming the problem lies with grub config).

[This page]("http://www.ubuntuforums.org/showthread.php?t=275728&highlight=Dual+Boot+on+Two+Drives") describes two ways to dual boot on dual drives.

---

### Post by logos34 on 2007-01-19
Other thoughts...Did you remember to set the jumper on the 20GB windows drive to 'slave' position or 'cable select'? (if the latter then both drives need to be set for cable select).

---

### Post by Zeek00 on 2007-01-19
Its a seagate harddrive and accord to their website for the ATA harddisk there needs to be no jumpers to be slave and that is how it is setup. The 60GB is already setup as the Master.

Upon installing Ubuntu it also confirmed that the 60GB is the Master and the 20GB is the slave

---

### Post by confused57 on 2007-01-19
You've probably already done this, but you might go into bios and make sure that your slave drive controller is "enabled" or set to "auto".

---

### Post by Sefrin on 2007-01-19
> **Zeek00 said:**
> So what help are you offering?

Basically, I would let Windows have its way and be on the master drive.  Master, slave, it doesn't really matter except to Windows.

Maybe it's the same idea as when you have one drive and everyone says to install Windows first in the (physically) first partition, and everything else after it.

---

### Post by Zeek00 on 2007-01-20
Surprisingly the slave controller was disabled, :lolflag: 

I just assumed it wasn't because I didn't really add a new drive, just swap out an old corrupt and damaged 20 gb for a new one. Thanks for all the help!

---

