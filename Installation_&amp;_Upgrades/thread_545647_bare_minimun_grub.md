---
title: "bare minimun grub"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-09-07
I've blown grub's menu.lst up. the backup menu.lst_backup file has the same problems not working. when the OS is powred up, grub presents no system to boot into. I'm running Feisty with the latest kernel. As I had Ubuntu Studio installed it was a low latency kernel.

I don't even get offered a recovery mode.

Help!

---

### Post by merlinus on 2007-09-07
More info would be useful, e.g. dual-booting.

And you might post /boot/grub/menu.lst and /etc/fstab along with sudo fdisk -l.

-merlin

---

### Post by banewman on 2007-09-07
This is the entry for the lowest kernel on my system : 
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f9a6eed6-a55e-46df-b4b4-86101458a16a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
 hope it can help if you can edit it with a live cd.:)

---

### Post by Mark_in_Hollywood on 2007-09-07
First: 

for Merlinus

This is a stock Dell Dimension 4100 running two hard disks as Pri Master and Pri Slave

It never was set to dual booting in the sense of a windows side and a linux side. Both disk were linux, Pri Master was Feisty (ver. 7.04) and the Slave is: Dapper (ver 6.10). 

Originally set up with a Canonical Desktop CD (not alternate cd). The install process found both drives. Named the Pri Mstr sda and the Pri Slv sdb, I think.

Grub would present a list of both drives and over time as I updated the kernel, the pri mstr or Feisty drive grew longer until there were 5 or 6 kernels/recovery kernels.

How do I find the correct UUID? Is that drive specific?

God! This is a fright. Thanks for the support.

---

### Post by merlinus on 2007-09-07
**sudo fdisk -l**

will show your partitions.

**blkid**

will show their uuids.

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1185     9518481   83  Linux
/dev/sdb2            1186        1240      441787+   5  Extended
/dev/sdb5            1186        1240      441756   82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="9dea8cc1-82db-49a6-85fe-cf8d41d5f398" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="82ad16ec-a20d-406e-ba15-becd1f1e6342" TYPE="swap" 
/dev/sdb1: UUID="69cb2cb9-d64c-41bf-8d35-bb801f3e48c0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="dc169449-d95f-4aaf-b8cc-31ed6a286fb9" TYPE="swap"

so is the /dev/sda1: the correct line for pasting into grub?

---

### Post by merlinus on 2007-09-07
If feisty is on your first hdd, then yes, the uuid for sda1 is the correct one for use in the menu.lst ubuntu kernel stanzas.

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-07
1. Where are the kernel stanzas? After the automagic?

2. At boot time, I see an plain text screen that is part of Grub, I assume. There were no drives being listed at last boot, but now, the OS? is finding the 2nd hard drive. The /boot/grub/menu.lst shows no devices 'named' sd**a** 

3. I don't see where this should go. Does Grub or someparts of the kernel/software get some from a part of the kernel, here and there. That is, is what I'm seeing a composite of lines (data) off the hard drive and not literal lines from a file? 

banewman gives me his "Grub" boot screen as:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f9a6eed6-a55e-46df-b4b4-86101458a16a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I don't see anything remotely similar in /boot/grub/menu.lst, so merely adding the proper UUID doesn't seem the right change here, but . . . well that's my question. 

4. Can I "rebuild" the Grub boot menu by hand, if necessary? When I <ESC> the countdown, I see something like (pardon my faulty memory)

>root

that is the only line I see to edit. Can I remove the word "root"?

---

### Post by merlinus on 2007-09-07
Post your /boot/grub/menu.lst.

And do not change anything else at the moment....

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-07
As it appears on the LiveCD

/media/disk/boot/grub/menu.lst

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
# kopt=root=UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 ro

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

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdb1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# Lines following added by MP on 9/7/07 to add windows hard drive.
#title           Windows
#root            (hd1,0)
#savedefault
#makeactive
#map             (hd0) (hd1)
#map             (hd1) (hd0)
#chainloader     +1

---

### Post by merlinus on 2007-09-08
So your menu.lst is pointing to sdb1.  Is that the correct linux installation?

Also, what is the boot order of your hdds?

-merlin

---

### Post by banewman on 2007-09-08
At boot grub displays the ubuntu operating systems as :
```
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
```
but of course with your numbers. Do you get something similar to this?

---

### Post by Mark_in_Hollywood on 2007-09-08
Pointing to sdb1 -- is that correct?

NO

it should be sd**a**1

and Bamewan, yes

that is what the boot screen looked like, but with different kernel numbers.

---

### Post by merlinus on 2007-09-08
Then try changing all the linux references in menu.lst from (hd1,0) to hd(0,0).

And dev/sdb1 to dev/sda1.

-merlin

---

### Post by merlinus on 2007-09-08
And delete all the parenthetical references except the one that says:

(recovery mode)

This may not be totally necessary, however,  You can see if it works before doing this, but they seem to be your comments, and not part of the original file.

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-08
OK

1,0 

replaced to

0,0

I'm going to reboot and I'll either have more questions or mark this post solved.

---

### Post by Mark_in_Hollywood on 2007-09-08
After editing menu.lst to 0,0 instead of 1,0 the system still has no bootable kernel. However now, selecting any from the list of available kernels/recover OSs, gives:

Error 15 file not found

kinda' reminds me of old DOS.

---

### Post by merlinus on 2007-09-08
I assume you are mounting your sda1 partition from the live cd??

What is in /boot? You should have kernel-related files and folders.

And you still may need to change some entries in menu.lst, so post only the relevant (linux-related) lines.

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-08
I can only guess how "sda1 partition from the live cd??" is loading. I put the Canonican issued CD in the drive and push the power button.

As I look over /boot is see files relating to what I see at boot time, e.g.,

2.6.20-16-lowlatency


I've never pasted a screen shot before so I hope you can see what you need. It is the list of files in /boot. Other than that, I can't quite understand what it is you want to see. Sorry.

---

### Post by merlinus on 2007-09-08
Looks good to me....

What about your revised menu.lst?

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-08
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
# kopt=root=UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 ro

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

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdb1) (on /dev/sdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

# The lines below: title, root, kernel, initrd, savedefault, boot, commented #out by mp on 9/7/07 to install windows drive
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# Lines following added by MP on 9/7/07 to add windows hard drive.
#title           Windows
#root            (hd0,0)
#savedefault
#makeactive
#map             (hd0) (hd1)
#map             (hd1) (hd0)
#chainloader     +1

---

### Post by merlinus on 2007-09-08
Any lines, except for title, that refer to partitions need that part deleted.

For example,  kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash

Delete root=/dev/hda1

BTW, have you considered simply reinstalling ubuntu to sda?

-merlin

---

### Post by Mark_in_Hollywood on 2007-09-08
Re-installing would be the least good idea for the time being.

One last quesiton, please, you say:

[B]Any lines, except for title, that refer to partitions need that part deleted.
For example, kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
Delete root=/dev/hda1[/B]

Where is the title line? Seen during boot? in the file menu.lst?

Do you mean delete from "root=/dve/hda1" and leave whatever follows?

Do I know a partition by the addition of the number after the letters?

---

### Post by banewman on 2007-09-08
Mark, the lines in the menu.lst have to match the files in /boot. There will be tar files named - initrd... - what are they if you can?

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f9a6eed6-a55e-46df-b4b4-86101458a16a ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

This is the first entry in menu.lst for os's and the first I see at grub boot time. The file it refers to is :
initrd..img.2.6.20-16-generic

---

### Post by confused57 on 2007-09-08
You could try a direct kernel boot entry for Feisty:
```
title  Feisty
root  (hd0,0)
kernel  /vmlinuz root=UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 ro quiet splash
initrd  /initrd.img
boot
```

This entry may boot Dapper:
```
title  Dapper
root  (hd1,0)
kernel  /vmlinuz root=/dev/hdb1 ro quiet splash
initrd  /initrd.img
boot
```
To boot Dapper, you'll need to mount your Dapper root partition, open your /etc/fstab & make sure that /dev/hdb1 is the device for / .

---

