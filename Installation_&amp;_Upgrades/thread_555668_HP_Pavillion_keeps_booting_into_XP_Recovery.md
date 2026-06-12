---
title: "HP Pavillion keeps booting into XP Recovery"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by MartnicK on 2007-09-20
I have made a lot of searching (spent hours, used different approaches of search expressions) on and off the Ubuntuforums and reading about dual booting on two separate hard drives but still I haven't found the answer I need, so here we go:

I have a HP Pavillion about two years old.
It runs XP Home on first SATA 160 GB
It runs Ubuntu 7.04 on second SATA 250 GB
So I have two functioning installed SATA HDs, one with Ubuntu Linux, and one with XP Home.

My problem is that how i twist and turn, editing Menu.lst, switching the boot order in BIOS, swithing the cables on the motherboard, I end up successful booting into Ubuntu via GRUB but fail booting into XP Home. My dear HP instead boots into the "XP Recovery" function which results in the famous blue screen (since i have not put the recovery CD into the DVD-Reader, because I have no intention or need to recover anything...).

For the record I have tried to install Ubuntu both with the XP drive disconnected aswell as connected during installation (of course the "Ubuntu drive" was connected during all my attempts, haven't gone completely mad I hope :) )

Result of fdisk -l  (parden the Swedish headers):

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       20672   156280288+  44  Okänd (Okänd translated: Unknown; by the way shouldn't the recovery partition be seen here?)

Disk /dev/sdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Utökad (Utökad translated: Extended)
/dev/sdb5           30025       30401     3028221   82  Linux växling / Solaris


Is there any clue out there on how I can get GRUB to boot into XP Home instead of "XP Recovery"?

Thanks in advance!

Best Regards,
MartnicK

---

### Post by logos34 on 2007-09-20
that's an odd listing for sda1--do you have a Symantec GoBack on the recovery partition?  XP Home should show up as sda2 with a partition type code of '7 HPFS/NTFS'.

Can you see and/or access windows from linux?  If not, does gparted detect it? (if so post screenshot)

---

### Post by MartnicK on 2007-09-20
Yes I have Symantec GoBack installed, would removing it be of help (it haven't helped me when i hoped it would in another situation...)?
I will get back on the gparted detection.

---

### Post by logos34 on 2007-09-20
don't remove it just yet...hopefully it's just the partition table that's messed up and your XP install is still there.  A utility like TestDisk might fix it (use with care).

---

### Post by MartnicK on 2007-09-20
Heres a screenshot from GParted on the partition/s for the XP disk.

Note that there is no problem running either disk. The problem is to get a dual booting up and running that can handle the "handover" from GRUB to boot XP, and that GRUB is located on the Ubuntu HD.
HW-wise the XP is on the SATA1 on the motherboard, but the BIOS is set to boot from the SATA2 HD (i.e. Ubuntu HD).

Small disclaimer:
Have made a re-install of Ubuntu today without opening the desktop and (just like before) let the Ubuntu install take the whole 250GB disc (XP on 160 GB disc) but this time with the XP disc connected hoping that everything should get settled, so I just make the assumption that Ubuntu haven't messed anything up (thats the point with Ubuntu/Linux right :) ) without running the whole check list.

---

### Post by logos34 on 2007-09-20
> **MartnicK said:**
> Note that there is no problem running either disk. The problem is to get a dual booting up and running that can handle the "handover" from GRUB to boot XP, and that GRUB is located on the Ubuntu HD.

HW-wise the XP is on the SATA1 on the motherboard, but the BIOS is set to boot from the SATA2 HD (i.e. Ubuntu HD).

Oh, then in that case the problem is you need 'mapping' so you can [boot XP on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Post your /boot/grub/menu.lst.  If you just reinstalled ubuntu with the xp disk connected, there should be an entry in menu.lst, it's just that it needs to be slightly edited.

Still don't know what is going on with fdisk--sda1 I see is actually your XP partition (fat32 not ntfs).

---

### Post by MartnicK on 2007-09-20
Below is a copy of the whole original menu.lst from the installation (since you did not ask for a specific part of it).
(the smilies in the beginning is automatically added by this forum, but maybe that goes without saying..?)

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
# kopt=root=UUID=f80cf9aa-106e-4e4e-8f0e-e3a09983cf68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f80cf9aa-106e-4e4e-8f0e-e3a09983cf68 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f80cf9aa-106e-4e4e-8f0e-e3a09983cf68 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f80cf9aa-106e-4e4e-8f0e-e3a09983cf68 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f80cf9aa-106e-4e4e-8f0e-e3a09983cf68 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by logos34 on 2007-09-20
> **MartnicK said:**
> Below is a copy of the whole original menu.lst from the installation

What do you mean 'original'?  Is this the one you're using now?  Because I'm confused...it seems that the ubuntu disk was second at the time of reinstall (hence the 'root hd1,0'), but you say you set the ubuntu disk first in the bios order and are booting directly to grub on that drive.  If that's the case it should only work with menu.lst showing root at (hd0,0).  But if grub is instead on the mbr of the windows drive, then XP should boot with the existing entry.

Check in gparted that sda1 is activated:

right click sda1>manage flags>check 'boot' box 

Or try 'rootnoverify' for XP:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
**rootnoverify** (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by MartnicK on 2007-09-20
Hi again and great thanks for helping me out!

I have read through the previous posts and the Menu.lst, and I can't see anything contradictory...

> 
Note that there is no problem running either disk. The problem is to get a dual booting up and running that can handle the "handover" from GRUB to boot XP, and that **GRUB is located on the Ubuntu HD**.
HW-wise the **XP is on the SATA1 on the motherboard**, but the **BIOS is set to boot from the SATA2 HD (i.e. Ubuntu HD)**.


So the Ubuntu disc is connected to the second SATA port on the motherboard (i.e. SATA2) and BIOS is set to boot from SATA2 first in order of the two HDs.

The main problem is when i choose "Windows NT/2000/XP" in GRUB, and GRUB should hand over (is this a correct image of what should happen?) to SATA1 (i.e. XP disc). Then the XP disc starts the Recovery instead of starting up XP Home.

Regarding the Menu.lst; By original I mean that the previously posted complete version of my Menu.lst is the backup version from the latest install (always backup before making changes, right?) since I made an attempt to "boot into the second partition" after making a wild guess that the recovery partition was before the actual XP, see below for an example.
The below is of course not working, it was my last attempt before starting this thread.
At the moment I am only booting Ubuntu on the PC in question, which is working fine.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,**[COLOR="Red"]1[/COLOR]**)
savedefault
makeactive
chainloader +1

I will test the rootnoverify tomorrow (going back to the original Menu.lst of course).

The time is getting late on this side of the planet, so I will double check things tomorrow and get back.
P.S. Yes, I am a notorius Linux newbie. Just to explain the wild guesses. D.S. :)

---

### Post by logos34 on 2007-09-20
> **MartnicK said:**
> So the Ubuntu disc is connected to the second SATA port on the motherboard (i.e. SATA2) and BIOS is set to boot from SATA2 first in order of the two HDs.

That's what I undertstood you to mean.

> The main problem is when i choose "Windows NT/2000/XP" in GRUB, and GRUB should hand over (is this a correct image of what should happen?) to SATA1 (i.e. XP disc). Then the XP disc starts the Recovery instead of starting up XP Home.

yes, that's a good way to put it...to be more precise it 'chainloads' the windows bootloader.  

> Regarding the Menu.lst; By original I mean that the previously posted complete version of my Menu.lst is the backup version from the latest install (always backup before making changes, right?) since I made an attempt to "boot into the second partition" after making a wild guess that the recovery partition was before the actual XP, see below for an example.

The below is of course not working, it was my last attempt before starting this thread.

At the moment I am only booting Ubuntu on the PC in question, which is working fine.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,**[COLOR="Red"]1[/COLOR]**)
savedefault
makeactive
chainloader +1

That's what I would have tried next--hd0,1 since it is supposed to be the second partition.

Something is very odd here...fdisk only detects the Symantec recovery partition (taking up the entire disk!) while gparted shows the disk as one big fat32 XP partition...And you say the only problem is that you can't boot windows from grub.  You've tried root hd0,0 and hd0,1, and neither work.  If rootnoverify doesn't do it, I guess you could try the map commands just for the hell of it, but I doubt it will work.

> title Windows NT/2000/XP
root (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

Something I didn't mention earlier: check the Bios to make sure that the hdd detect is set for 'auto', not 'user', manual, chs, etc.

TestDisk may be able to help sort out any errors in the partition table.

---

### Post by MartnicK on 2007-09-21
Oh boy...
Made the double check I mentioned in a previous post, and I have to quote myself again:
> 
Small disclaimer:
Have made a re-install of Ubuntu today without opening the desktop and (just like before) let the Ubuntu install take the whole 250GB disc (XP on 160 GB disc) but this time with the XP disc connected hoping that everything should get settled, so I just make the assumption that Ubuntu haven't messed anything up (thats the point with Ubuntu/Linux right ) without running the whole check list.

It seems that the Ubuntu install put the GRUB in the MBR of the XP disc after all.
There were no *clear* indication during the installation process that anything should go that way, otherwise I would have gone with the "disconnect the XP Drive during install" method again.

However **the main question remains, which means that if GRUB would have booted up XP and Ubuntu as expected, I would never have known the position of GRUB until (much) later when reaching a higher level of knowledge in the subject.**

**This issue is still important since I have not seen any other thread with this exact question, though I know that several PCs are shipped with this really Windows-trapping setup.**

I have made some more investigations and it seems that the partition with recovery is the one that "runs the booting show" i.e. has some kind of flag set to "boot". Saw it when i used a Gnome utility that shows info on the hardware setup (cannot check the name of it know since I'm on another PC at the moment).
I will post a screenshot later.

Another annoying part of it is that when I try to boot the PC, with the Recovery DVD I burned using the HP SW that the PC came with, in order to start the Recovery Console for repairing the MBR a message is showing that says something like "No OS is installed or bad sectors. Press Enter for complete recovery". Not very promising.
This I will have a talk with HP Support about.

If there is any leads about **the main issue** I would be glad to receive them.
In the mean time I will check the forums for a way to reach the Windows disk from Ubuntu, and another way to fix the MBR.

Maybe I should look for another Boot Manager (have seen posts on something called Super GRUB, could that be the cure here?)

Many thanks for the help so far!

Best regards.
MartnicK

---

### Post by Pumalite on 2007-09-21
Super Grub is great: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Study it carefully and I'm sure you'll get something useful out of it.
P.S. The culprit here is the 'recovery partition'. Their way of selling you a computer without a disk and keeping you a prisoner.

---

### Post by logos34 on 2007-09-21
I thought grub was on the XP drive.

As to the 'main' issue, you are right, there's no clear indication on the live cd where grub is being written to.  There's an inconspicuous button 'Advanced' on one of the install screens you have to click to bring up a grub-install dialog box where your can change it.  Hopefully the devs will get around to making the grub part more user-friendly.

I was thinking maybe the partition tables were messed up but maybe you have a few bad sectors like the utility program suggests.  Find a way to access windows from ubuntu and backup your files before you try 'complete recovery'.

For the third time: you might want to try TestDisk first.  It may be able to straighten out the partition table.

---

### Post by MartnicK on 2007-09-22
Regarding TestDisk;
I have installed it via the Synaptic GUI, but I can't find any entrance in any of the menus. Is it strictly CLI based (I have seen that the command is possible to run from a Terminal)?

Regards,
MartnicK

---

### Post by logos34 on 2007-09-22
yep, type testdisk in terminal

---

### Post by MartnicK on 2007-09-23
Hi again, sorry about the delay.

I have now run TestDisk, can you make anything out of the screenshot?

The shaky bit is that I really don't know what would happen if I would run TestDisk in order to try to restore any part of the HD. What is the worst case scenario? Is it advisable to use TestDisk in this case?

P.S. This is the last time I buy a PC with this kind of setup for Recovering Windows. PCs should be delivered with a CD/DVD with the OS *period*.
(cannot yet say that it's the last time I buy a PC with Windows yet, but in the meantime I get more and more familiar with Ubuntu/Linux so...)

---

### Post by logos34 on 2007-09-23
> P.S. This is the last time I buy a PC with this kind of setup for Recovering Windows. PCs should be delivered with a CD/DVD with the OS period.

Agree 100%.

screenshot: that's the disk you want to check - sda 160gb.  Make sure backup any saved files in windows parititon, assuming you are able to mount it in ubuntu.

I'm only telling you what I'd do--it's up to you.  But I'd personally opt to run testdisk before going through the recovery process.  It just seems to me that it's the partition table on sda that's screwed up, but I could be wrong and maybe there are bad sectors or other errors on the XP partition.

Make sure to read the testdisk documentation on the website [and this page]("http://www.users.bigpond.net.au/hermanzone/p21.html").  Don't save/write any changes to disk until you're sure.

EDIT: It's not clear to me if you tried Super Grub Disc, as pumalite suggested, to restore the windows bootloader/boot XP.  Be sure to give that a shot first because if it works you may be able to avoid all the rest.  The only thing is you'd have to switch the Bios to boot each OS.

---

### Post by MartnicK on 2007-09-23
logos34, the last link you posted had a sublink to a very interesting walkthrough for as far as I could see this very action!
(of course in a successful case, let's hope I will have one aswell)

Bad examples are for some reason harder to find than good ones...
What is the worst case scenario in this case? What could be damaged by TestDisk?

Just me thinking without making research on the subject:
Is it rather "simple" to understand how the partition table should look based on what filesystem it is (correct term?), or what principle does TestDisk use to "re-write" or "re-create"  the partition table?

I will now gather the facts and make a decision on how to proceed. Since there are a few things to consider regarding risks and suitable precautions before taking the final step, it may take some time (hopefully not too long though) before I do it however I will post the results later on.

I appreciate the help and the pointers very much!

Best Regards,
MartnicK

EDIT: I have made an attempt to boot with Super GRUB, but I got the impression that Super GRUB prompted for fixing the MBR which made me a bit shaky. What is the worst case scenario for fixing the MBR with Super GRUB?

---

### Post by logos34 on 2007-09-23
What is the worst case scenario in this case? What could be damaged by TestDisk?
...Is it rather "simple" to understand how the partition table should look based on what filesystem it is (correct term?), or what principle does TestDisk use to "re-write" or "re-create" the partition table?

The [official ]("http://www.cgsecurity.org/wiki/Running_TestDisk")and unofficial documentation links I gave you do a much better job of explaining it that I can.  Here's what [one recovery result looks like]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS").  

_*So did you try using Super Grub to boot windows_?

---

