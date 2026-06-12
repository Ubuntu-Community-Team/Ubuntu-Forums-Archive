---
title: "Hardy Hero messed up my Vista boot loader..."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by ssylvan on 2008-04-26
Hi,
Here's how I had my PC set up before installing Hardy Heron. Originally I had just windows XP installed on hard drive 0, then I installed Vista on hard drive 1. Vista put a boot menu (on hard drive 0) which let me choose between XP and Vista. 

Then I installed Hardy Heron on hard drive 0 (i.e. nuking XP, while keeping Vista on hard drive 1). This overwrote my boot loader (that used to let me choose between XP and Vista) and will only load Ubuntu. So now I have no way of getting into Vista anymore. I tried changing the boot order of the hard drives, thinking that the hard drive 1 would have a straight "load Vista and nothing else" loader on it, but got an error saying that there was no NTLDR.
Next I tried adding the following to /boot/grub/menu.lst, but it just said "Starting" and then nothing happens.

title         	Windows Vista
root         	(hd1,0)
chainloader	+1

So, how can I get back into my Vista installation, preferably without having to re-install it (I don't have a disc, since I got my Vista copy from MSDN online, and I just mounted it in XP using Daemon tools and installed it without having to burn it - a very convenient feature that ubuntu should copy, btw! Anyway, this makes it a bit tricky to re-install Vista at this point, since I don't have any DVDs laying around...)?

---

### Post by Pumalite on 2008-04-26
Super Grub can fix your Vista MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by ssylvan on 2008-04-26
Thank you, that looks promising.

Just to make sure I've got this right, I can use this tool to fix up the MBR on hard drive 1 where Vista is installed (essentially pretending that hard drive 0 doesn't exist, booting into it by switching the boot order around in BIOS), and then once I've done that the GRUB boot menu that I have on hard drive 0 should work right?

I still want to dual boot into linux/vista, so I don't want to boot *just* into Vista or anything!

---

### Post by Pumalite on 2008-04-26
Post:
sudo fdisk -l

---

### Post by ssylvan on 2008-04-26
Here it is. Vista is on sdb1.

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x106a106a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8556    68726038+   7  HPFS/NTFS
/dev/sdb2            8557       19457    87562282+   f  W95 Ext'd (LBA)
/dev/sdb5            8557       19457    87562251    7  HPFS/NTFS


---

### Post by Pumalite on 2008-04-26
I assume you are on Ubuntu Libe CD. Mount the partition:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
Post:
cat /media/sda1/boot/grub/menu.lst

---

### Post by ssylvan on 2008-04-26
I'm not on the Live CD, I'm in the installed ubuntu. Booting into it works fine, it's just booting into Vista that doesn't work. I added the final entry (the Vista one), the rest was what I got after installing ubunu (which I did do from the Live CD, if that matters)

> 
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=5be82dd6-665b-4aa7-b0d5-9f2fcf84a800 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5be82dd6-665b-4aa7-b0d5-9f2fcf84a800 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5be82dd6-665b-4aa7-b0d5-9f2fcf84a800 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title         	Windows Vista
root         	(hd1,0)
chainloader	+1



---

### Post by Pumalite on 2008-04-26
Add this after memtest:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows Vista
rootnoverify (hd1,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by ssylvan on 2008-04-26
Should that be "savedefault" rather than "savedafault"?

---

### Post by Pumalite on 2008-04-26
Sorry for the typo. You are right.

---

### Post by ssylvan on 2008-04-26
Just tried it, it still says that it can't find the "NTLDR". So I guess I need to run that supergrub thing to fix the MBR on the Vista disk?

---

### Post by Herman on 2008-04-26
Excuse me for interrupting, but try this, 
```
title             Windows Vista
root             (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader    +1
```Regards, Herman :)

---

### Post by Pumalite on 2008-04-26
Thanks.

---

### Post by ssylvan on 2008-04-26
Herman, tried that, same error.

---

### Post by ssylvan on 2008-04-26
I also tried using the supergrub thing to fix the MBR on hard drive 1, and it still says it can't find "NTLDR"... I'm not sure Vista works the same way as XP does w.r.t. boot loading so maybe it doesn't work?

---

### Post by Herman on 2008-04-26
'[NTLDR is missing, press any key to restart]("http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to").' is an error message from Windows, and usually it means that the boot.ini file or whatever the Vista equivalent of that might be, contains the wrong hard disk or partition numbers.
You installed Vista in hard disk0, (your first hard disk).
Now, it's in hard disk1 (your second hard disk).
The pair of map commands is supposed to fool Windows into thinking it's in the first hard drive so it'll boot up without the need for you to go and edit boot.ini in Windows.

Are you sure you are entering the pair of map commands correctly? Without any synatax errors?

---

### Post by lemming465 on 2008-04-26
> **ssylvan said:**
> ... I installed Hardy Heron on hard drive 0 (i.e. nuking XP, while keeping Vista on hard drive 1). This overwrote my boot loader (that used to let me choose between XP and Vista) and will only load Ubuntu. 

The boot process goes something like this:
[LIST=1]
[*]BIOS loads 446 bytes of initial boot code from the MBR (first sector of the first disk).
[*]MBR finds the "active" partition and load the first sector of that
[*]the secondary boot loader block loads up to 8K more of boot code from the reserved space at the start of the active partition
[*]the full secondary boot loader finds its preferred boot partition and loads the boot menu selector (grub, or vista bootmgr)
[*]user picks an OS
[*]boot selector code either loads the chosen OS (grub -> linux) or starts the OS specific loader.
[*]the OS specific loader (NT: ntldr; Vista: winload) loads the OS
[/LIST]

Your vista problem is that vista put all the goodies it needed on the XP partition, which you nuked.  So the repair strategy is going to have to get them back.  Boot your Vista install CD in recovery mode and have it repair the boot structure on the second hard drive.  At that point the grub "chainloader +1" ploy will probably work again.  Worst case scenario you'd have to put a FAT or NTFS c: partition back on the first hard drive and let it use that.

Make sure that partition sdb1 is marked "active", either in its partition table or in the grub entry that chains to it.

The [Wikipedia windows boot process]("http://en.wikipedia.org/wiki/Windows_Boot_Manager") article has some more details about what Vista is trying to do.  

What you really want to follow is the [microsoft vista boot repair]("http://support.microsoft.com/kb/927392") instructions.

Microsoft tends to think they own the universe, so if they clobber your primary hard drive MBR code in the course of fixing Vista, then you'll have to do a second round fix to get Linux booting back.  There should already be directions for that around here somewhere; come back if that bites you.

---

### Post by Herman on 2008-04-28
Hello lemming465,
Thanks for your excellent information, I knew Windows will do that when more than onw Windows is installed in the same hard disk without 'hiding' the existing Windows, but I didn't know Vista would do that when it is installed on a different hard disk. No wonder ssylvan's Vista wouldn't boot! I will try to learn more about Vista.
Regards, Herman :)

---

