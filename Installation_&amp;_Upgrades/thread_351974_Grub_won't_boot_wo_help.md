---
title: "Grub won't boot w/o help"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by o4tuna on 2007-02-02
OK, I got it installed, finally. But when I reboot, I get grub error 15?
Booted with SGD, "autofix" doesn't, but "boot directly" does get me in...
Any ideas on how I fix it?
It's 6.10
installed to 1st SIDE drive
2nd SIDE & 3 PIDE hard drives in system (no other OS'es) + PIDE dvd
MoBo is about 16 months old, 3ghz athlonXP, 1G ram

figured you'd probably ask for these:

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
# kopt=root=UUID=e3fe101e-bb08-4f85-84f0-11ae7d04e998 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST[/QUOTE]



fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666    7  HPFS/NTFS

---

### Post by Herman on 2007-02-02
Hello o4tuna,
> 15 : File not found  This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.
               For example, if you get this error during booting, maybe Grub is telling you it can't find the specified kernel or initrd.img file. Usually this is because of a mistake in editing your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error or a typo.```
 ## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd**[COLOR=Red]0[/COLOR]**,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd[COLOR=Red]**0**[/COLOR],0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd[COLOR=Red]**0**[/COLOR],0)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```Regards, Herman :)

---

### Post by o4tuna on 2007-02-02
Thanks for the prompt reply, Herman.
Just 'cause I sometimes get things wrong, especially when I assume, I assume I should make the changes you put in red?
I was suspecting that part of the file might be pointing at the wrong drive(s), but I'm not at all familiar with the meanings of the syntax of that file...

---

### Post by o4tuna on 2007-02-02
Poring over the details...
Ok, obviously (hd3,0) is not the SIDE drive /sda (I would assume the first partition, so /sda1), but how do we arrive at (hd0,0)?
And why did setup put it in (hd3,0)? Not sure at the moment but I don't think there was *ever* an OS on that one...

Up higher in the file there are other references to (hd3,0) also, should I change the, too?
-Preceded by a # symbol, would of thought that was commented out, but perhaps the lines with a single # are functional & the ones with more than 1 # are commented out?

---

### Post by Herman on 2007-02-02
>  installed to 1st SIDE drive
2nd SIDE & 3 PIDE hard drives in system (no other OS'es) + PIDE dvd Well you mean have 2 Sata hard disks and 3 IDE disks, is that correct? The two SATA disk are hard disk number 1 and two, and your IDE disks are 3, 4 and 5? And Ubuntu is installed in the first partition of the first hard disk?

Well, hopefully yours will be straight forward, but sometimes it can be a matter for trial and error to get Grub to behave itself properly when we have machines which have both IDE and SCSI (SATA) hard disks sharing the same motherboard. It has something to do with the way the BIOS numbers the drives, compared with the linux kernel, compared with Grub.  I don't understand the problem fully myself yet, I have read about it, that's all. Until now I have never owned a machine which can take SATA drives. Now I have one, but it is still in a box and I haven't had time to set it up and do any experiments. Even when I do, it might be different for different machines (with different BIOSes).
Anyway, I think (I'm hoping), yours will be simple and straightforward since your SATA disks are the first on the list already. 
Grub's numbering system begins counting from 0 (zero), so your first hard disk drive is called (hd0) by Grub. In your case that will be  /dev/sda.
Your second hard disk should be /dev/sdb. Grub would call that (hd1) to my logic.
Grub makes no distinction between IDE and SCSI disks in it's numbering system, but the BIOS always counts SCSI disks first.
I don't see any disk called /dev/hda? I don't know why that would be. :confused:
Your third hard disk would be /dev/hdb, and that should be numbered as (hd2) by Grub, I think.
Your fourth hard disk would be /dev/hdd, and it should be numbered as (hd3) by Grub.
(hd3,0) would mean your fourth hard disk's first partition. 
According to your fdisk ouput that's an NTFS data partition, so you won't be able to boot that.
I think (hd0,0) makes sense. To me it seems like a good probablilty anyway.

>  Up higher in the file there are other references to (hd3,0) also, should I change the, too?
-Preceded by a # symbol, would of thought that was commented out, but perhaps the lines with a single # are functional & the ones with more than 1 # are commented out?```
 ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

```You should leave that part alone for now, but when you get Ubuntu booting correctly then you should probably edit your automagic kernels list as well. The automagic kernels list is a very special part of the menu.lst file that facilitates the grub menu being automagically updated whenever new kernel is installed during an update. If that number is not edited correctly then the booting error will return when you get a new kernel. But wait unitl you get it booting properly first, then edit that part, just in case my guess is wrong about what disk number you need to specify.

I hope it works for you right away without any trouble.
Regards, Herman :)

---

### Post by o4tuna on 2007-02-02
Back to the live cd:mad: 

I edited the menu.lst file (took a bit to figure out how to save it - from the /boot/grub directory #sudo gedit menu.lst seems to get me there...

now it won't boot at all:( 
Error 17 now...
tried a bunch of SGD options, nada... The one I was using before gets me an ntloader is missing error:frown: 

booted from the live cd, mounted the ubuntu drive (yes it's sda1), file seems OK (not corrupt or different)


:biggrin: 
OOOH, OOOOH! I know this one!

> I don't see any disk called /dev/hda? I don't know why that would be
The primary master is the DVD drive!
:biggrin: 

Thanks for the help, glad to know you're learning from this mess, too...

---

### Post by Herman on 2007-02-02
Okay then, sorry about that if it's going to be a matter of trial and error. There is, fortunately, a fast and convenient way to perform the required trials and errors.
This has worked before for others who have had similar difficulties, you can use Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
You can get a command line from either your hard disk installed Grub menu, by pressing 'c', or from SuperGrub Disk, the same way.
You can experiment with that much faster than editing your /boot/grub/menu.lst and rebooting each time.
You can also type specail commands at the Command Line Interface that will get [GRUB's Command Line to investigate your computer]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer") for you and reveal how Grub itself sees your drives.
You can then [Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI") and then use the same commands to edit correctly your /boot/grub/menu.lst entries. (So make notes on paper of the commands you try until you find a combination that works).

I'll be around here for a while if I can help you any further.
Regards, Herman :)

---

### Post by o4tuna on 2007-02-03
OK, went & looked at the linked grub tutorial. Are you the author? Very well done. My biggest beef with Linux docs is they either assume you are a clueless n00b, or a software engineer. Yours filled in the blanks rather nicely.

Spent the next couple hours trying to get the live cd to print just the pertinent pages.

Had to get some sleep.

OK, now we'll give this a try!

hmmmm, it IS reporting everything as being on hd3,0:confused: 

Now I thought I understood the numbering, but that is whack!
Should be:
hd0 Sata1
hd1 Sata2
hd2 PriMaster
hd3 PriSlave
hd4 SecMaster
hd5 SecSlave
Shouldn't it?
But it seems to be plunking the sata drives down in the middle:confused: 

Well, I got it to boot from the command line, now on to re-editing the menu.lst file so it'll boot w/o intervention.
I'll let you know how that worked out in a few minutes

---

### Post by o4tuna on 2007-02-03
:confused: :mad: :confused: :mad: :confused: 

Nope, that didn't work.

Ran through the command line boot:
Now it shows up on hd0,0:confused: :confused: :confused: 

Could the bios be numbering them differently with each boot?
How to make it stop?

Also, it didn't give any of the responses to the root/kernel/initrd commands, just popped back to the prompt...

HMMMMM, just popped into my head, may be important:
When it came up hd3,0 I had booted from the sgd (cd drive)
When it came up hd0,0 I booted from the hdd & waited for it to error out.
Could it be changing the numbering, based on which device it boots from?

---

### Post by Herman on 2007-02-03
Gee, I knew that it would be a little bit tricky, but I didn't think it would changing with each boot.

I have had some weird grub problems myself just with two IDE disks after deleting some filesystems.  I can't imagine how that could have affected Grub, so I guess it's the BIOS that causes all the trouble. That's what others who know more than me say.
It (the fact that some filesystems were missing) also affected the resolution of my monitor display for the operating systems I didn't delete, when I did succeed in booting them.
When I restored the same deleted operating systems again, (I had backed them up with Partimage, (see aysiu's Partimage tutorial, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")), the computer returned to normal. Weird behaviour or what? :confused:
The fact that the monitor display was even affected seems to lend credibility to the notion that it's the BIOSs peculiarities rather than the fault of Grub.
I deliberately added the extra hard disk just to see what grub problems I could simulate, I never had any grub problems at all with any machine with just one hard disk.



I wish I could be more help. Maybe someday after I learn more...

Regards, Herman :)

---

### Post by o4tuna on 2007-02-03
Hi Herman, thanks for the help!
I think I found the culprit:
[https://launchpad.net/ubuntu/+source/grub/+bug/8497](https://launchpad.net/ubuntu/+source/grub/+bug/8497)
sez it's a bug!
involves asus mobo & sata/ide combos.
The solution appears to be editing the device.map file?
I'd really hate to muck this up anymore, would you be so kind as to read that & coach me through making the change(s)?
reading this now:
[http://ubuntuforums.org/showthread.php?p=1781151](http://ubuntuforums.org/showthread.php?p=1781151)

---

### Post by o4tuna on 2007-02-03
current device.map
(hd0)	/dev/hdb
(hd1)	/dev/hdc
(hd2)	/dev/hdd
(hd3)	/dev/sda
(hd4)	/dev/sdb

I think I should change it to:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/hdb
(hd3)	/dev/hdc
(hd4)	/dev/hdd
Am I close?

---

### Post by o4tuna on 2007-02-03
:lolflag: :guitar: :lolflag: 
It booted!
):P ):P ):P ):P

---

### Post by Herman on 2007-02-03
```
 (hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/hdb
(hd3)	/dev/hdc
(hd4)	/dev/hdd
```

I think just give it a try, it won't do any harm. You have a record of what it was originally now, so you could always change it back, not that you would probably want to though, if it isn't working. 
I think what you are about to try makes sense to me. Go ahead! :), and good luck! :)

---

### Post by Herman on 2007-02-03
> :lolflag: :guitar: :lolflag: 
It booted!
):P ):P ):P ):P Hey! :) Excellent! Congratulations, you did it! Well done!

---

### Post by victorcache on 2008-01-09
>It has something to do with the way the BIOS numbers the drives, compared with the linux kernel, compared with Grub.  

1st, Herman, thanks for your site, it's been helpful and very informative.  
2nd, small tidbit to add:  had a 2 disk system with Windows XP on the first one and Unbunu on the other.  Ubuntu was installed 2nd and grub was working fine.  XP couldn't update itself anymore so I REPARTITIONED the Windows disk then reinstalled XP on one of the new partitions I created.  When I tell the BIOS to boot first from IDE0 the Windows disk, Windows boots fine.  When I tell the BIOS to boot first from IDE1 the Linux disk, I get the Grub boot menu but couldn't successfully boot to Linux/Ubuntu or Windows.  

In the process of troubleshooting I found that after booting from the Ubuntu Live CD and running Grub, find /boot/grub/stage1 would say grub was installed on hd1,1.   However when booting off the hard disk, getting the grub menu, then interactively running the same grub command    find boot/grub/stage1   would say grub was installed on hd0,1!  I manually edited the menu.lst and changed it to hd0,1 to fix Linux booting.    

So it seems the "definition" of what's hd0 and hd1 reverses between the time of initial booting and when Linux/Ubuntu is up and running.  Maybe in the first instant of booting the "hd0" is whatever the BIOS was told to boot from???

Recommendation:  check what grub    find /boot/grub/stage1  says after seeing the grub menu, not after booting from a Live CD.

---

