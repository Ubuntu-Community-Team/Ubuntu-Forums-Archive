---
title: "[SOLVED] Grub Ubuntu &amp;amp; Win XP setup help please"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by Biffa2001 on 2007-06-27
I am hoping that to solve this problem will be as easy as changing a setting in my grub file?

this is what I get from fdisk -l :

> Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1346    10811713+   7  HPFS/NTFS
/dev/hda2            1347       14946   109242000    f  W95 Ext'd (LBA)
/dev/hda5            1347       14946   109241968+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         510     4096543+   b  W95 FAT32
/dev/hdb2             511        1240     5863725    f  W95 Ext'd (LBA)
/dev/hdb5             511        1240     5863693+   7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4661    37439451   83  Linux
/dev/hdc2            4662        4866     1646662+   5  Extended
/dev/hdc5            4662        4866     1646631   82  Linux swap / Solaris

and this is what my boot/grub/menu.lst looks like:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro quiet #splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

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


I have 3 HDD's in my PC - I can boot Ubuntu if I put the hdd with it on as my first boot disk on the bios. When I start the PC Grub show up as it should and I can start Ubuntu no probs, but not windows.  

Alternatively, if I put the hdd with Windows on it as my first boot device in my bios, Windows XP will just boot straight off with no Grub showing.

Help!

Thanks in advance.
Steve

---

### Post by logos34 on 2007-06-27
One thing is clear:  Grub is definitely on hdc, the linux drive, and winxp bootloader is on hda.  What I don't get is how you can boot ubuntu with that menu.lst...It doesn't make sense.  In fact nothing makes sense!  Your 'groot' line says (hd2,0)--in grub-speak partition #1 on the THIRD drive, which looks right because it agrees with fdisk and the entries for the hashed-out 2.6.20-15 kernels--but you say you can boot ubuntu using the first entry (the default), which has root at '(hd3,0)'--that would be the FOURTH disk???  Even if it was '(hd2,0)' it still shouldn't work because you've changed the position of the linux drive to first in the BIOS hard disk boot order, in which case it becomes (hd0).  Maybe I've been reading these threads too long...

Did you copy and paste this directly from menu.lst or are those typos?

---

### Post by Biffa2001 on 2007-06-27
Hi, yep this is a direct copy n paste!

Glad I am not the only one who is confused.

Would it be anything to do with the fact that in my bios I can change the boot order of hdd's (instead of them being in the normal order of IDE1 - master then slave / IDE 2 master then slave etc?

My Linux hdd would actually be 2nd on the list but I move it to boot first in my BIos.

---

### Post by logos34 on 2007-06-27
> **Biffa2001 said:**
> Hi, yep this is a direct copy n paste!

Glad I am not the only one who is confused.

Would it be anything to do with the fact that in my bios I can change the boot order of hdd's (instead of them being in the normal order of IDE1 - master then slave / IDE 2 master then slave etc?

My Linux hdd would actually be 2nd on the list but I move it to boot first in my BIos.

Based on the info you provided it looks like hda and hdb are master/slave on the Primary IDE channel (channel0), and hdc the linux drive is master on the Secondary IDE channel (channel1)...Is that right?  But if you change linux hdc to first place in the BIOS **hard disk boot priority** (it is a separate sub-section under 'Boot' -- I'm not talking about the initial screen listing your drives), then it should look something like this:

> **1. Sec. Master: <drive hdc>**  [ ^ moved up from third position]
2. Pri. Master: <drive hda>                              
3. Pri. Slave: <drive hdb>             

The bios now sees it as **hd0**, so the linux root location should be (hd**0**,0), and winxp (hd1,0).  You'd have to edit menu.lst and device.map.  But you say you can boot ubuntu but not windows.  Maybe I'm missing something here big time.

edit: Are you sure this isn't 'menu.lst~' (an old backup)?  It seems like the drives were in a different boot sequence when you updated the kernel to -16.  Was there another drive attached at the time (a fourth hard disk or usb stick)?

---

### Post by logos34 on 2007-06-27
> My Linux hdd would actually be 2nd on the list but I move it to boot first in my BIos.

Ok, so then the linux drive hdc is actually the primary slave and the XP drive hda primary master?  Maybe I got that wrong.  But it really doesn't matter, because it's the BIOS boot order that counts.

Sorry if I didn't give you any solution in my last post, it's just that I'm still trying to make sense of why you can boot ubuntu with that menu.lst.  On the other hand, it's not a mystery why you can't boot windows from grub.  The problem is that there are basically two configurations you can choose from to get grub to boot both OS's, but either way you risk ending up with one or both of them unbootable.  

So I would go the safer route: leave the windows bootloader alone on hda and boot instead to Grub menu on the linux drive hdc. But you'll need to edit the windows entry in menu.lst and device.map, and it might take a few attempts to get it right. Here's what you can try:

Set the **linux drive first** in the BIOS hard disk boot priority and put the** winXP drive in second** position.

Then boot into Ubuntu and backup your menu.lst.

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**

Open menu.lst with superuser priviledges: 

**gksudo gedit /boot/grub/menu.lst**

Change windows entry:

> # This entry automatically added by the Debian installer for a non-linux OS
#[B] on /dev/hda1
title Microsoft Windows XP Professional
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1[/B]

(Windows will not boot unless it thinks it's on the first BIOS boot drive--hence the mapping to swap drive designations).

Now for device.map:

**gksudo gedit /boot/grub/device.map**

Change thus:

> [B](hd0) /dev/hdc
(hd1) /dev/hda[/B]

Now, try rebooting to the grub menu and see if you can get into windows.  (if you get a grub error after choosing windows, post back with the #).

I hope the changes to device.map don't screw up ubuntu, but if it does you can always use the live cd to restore the backed up menu.lst.
 
Give that a shot.

---

### Post by Biffa2001 on 2007-06-28
I will give that a try now thanks.

Just for reference, this is what my device.map looks like before I make any changes:

> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hdd

Right, off to give this a go :-) may be back in a mo, may not...!!

Cheers
Steve

---

### Post by Biffa2001 on 2007-06-28
Right, success!

Windows XP booted no probs.

Ubuntu wouldn't boot - I got "error 15, file not found" - but I've had that so many times before I've worked out you can edit the grub file just for that boot so I got into Ubuntu ok.

I just had to change this in boot/grub:

> title		Ubuntu, kernel 2.6.20-16-generic
root		**(hd3,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

to this:

> title		Ubuntu, kernel 2.6.20-16-generic
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f103d8c2-cec4-4661-b02a-4de16f871db5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

and it all works a ok.

Thanks for the help guys, really appreciate it as this problem has been driving me nuts for over a month as I tried to solve it myself. I had not heard of the device.map file and Win XP needing to think it was the first boot device before so I've learnt something new.

Thanks again
Steve

---

