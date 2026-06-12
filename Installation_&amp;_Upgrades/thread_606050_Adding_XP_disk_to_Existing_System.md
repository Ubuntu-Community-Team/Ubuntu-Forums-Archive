---
title: "Adding XP disk to Existing System"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by NiceCup OfTea on 2007-11-07
Hi,

I want to end up with a dual boot system but I'm coming at it from a slightly different angle.  I have a machine that boots to Ubuntu (7.10) and I have a hard disk from our old Windows machine.

I'd like to be able to simply add the Windows disk as a second drive in the Ubuntu box and get grub to be able to boot from it.

So far I have tried so of the grub editing suggested in the forums and elsewhere and only managed to break my Ubuntu boot.  Error 17 'cos the partition table got mangled.  Now I have recovered that I thought I'd ask if anyone has done this before and is there a quick way or is it just a bit harder?

Obviously I don't want to have to re-install either OS and I don't want to lose any data on either disk - just to make life interesting.

Any ideas - most dual boots seem to start with Win and then install LInux.

Thanks

---

### Post by dabl on 2007-11-07
If my rapidly-depleting memory cells are right, the Win XP installed OS is "wired" with hardware information from your old PC -- RAM, disk drive count, chipset drivers, and maybe other stuff.  I'm not sure your theory of operation is going to hold up, even if you get to where you can boot it.  :confused:

---

### Post by bulldog on 2007-11-07
Shouldn't be to hard to do.
Only thing you have to do for sure **the ubuntu hdd MUST be the first master boot device and the windows must be the secondary or slave**

Then make a few changes to the menu.lst and you're done.


@Dabl
a good point you have there thanx.
But in most cases you can boot in safe mode and remove the old drivers and settings if necessary.

---

### Post by Pumalite on 2007-11-07
I'm with dabl. I'd be interested in knowing the outcome.

---

### Post by bulldog on 2007-11-07
> **Pumalite said:**
> I'm with dabl. I'd be interested in knowing the outcome.

In safe mode there are no drivers loaded in windows and you can remove all the drivers completely.
I know because I did it more than once myself.
On the other hand you're right,nothing beats a clean install certainly when it's windows :)

---

### Post by Pumalite on 2007-11-07
Yeah..and what about the rest of the hardware. Remember this comes from an 'oldie'

---

### Post by bulldog on 2007-11-07
I don't think that matters too much.
What isn't there will not work and what is,well you have to install drivers for it again.
The most important thing is drivers for the chip set and motherboard features and maybe the graphics can be a show stopper,but they can be removed.

---

### Post by Pumalite on 2007-11-07
We'll see how the OP does.

---

### Post by NiceCup OfTea on 2007-11-08
Thanks for the input.

I'd forgotten that Windows ties itself to the hardware and that may well be the big killer for a 'quick fix'.  The hard drive comes from a old machine, but I also bought over the graphics card from that machine - one less thing to worry about.

I think that (re)installing windows on the second drive may be the quickest answer though.  But then I lose my windows UIDs.

I think I need to talk to the person who will use the Windows most Mrs Cup ofTea.  She may not want to lose her emails etc.

---

### Post by Pumalite on 2007-11-08
You are right. I'd be careful with that. OTOH, you can backup everything before you install.

---

### Post by NiceCup OfTea on 2007-11-08
With all the backing up etc I think that's a job for the weekend.

Once I get the Windows installed how do I get grub to offer Windows as an option.  I know I have to add something to the menu.lst file but the examples I've seen vary in content.  In fact it was using one of those examples that broke my partition table earlier this week.

If anyone has any suggestions of good examples to copy I appreciate it.

Time to give up for the night and see the end of the football.

---

### Post by bulldog on 2007-11-08
It should be the second hdd first partition so it should be something like this.
```

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by rabiddachshund on 2007-11-10
I'm trying to do something similar to this except the original drive has windows and I'm adding a drive with gutsy. Originally I had 2 disks and one sata cable so the windows drive wasn't there when I installed gutsy. I added bulldog's entry to menu.lst but it didn't work. I got a second cable and reinstalled Gutsy so that Grub would automatically configure it and now Grub gives XP as an option but when I select it it says that the disk isn't there. :confused:

edit: If I unplug the Gutsy drive, windows boots fine.

---

### Post by Pumalite on 2007-11-10
Boot Live CD and mount drives/partitions. Post from Terminal:

sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by rabiddachshund on 2007-11-11
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455   302744924   151316235    7  HPFS/NTFS
/dev/sda3       302760990   312496379     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0cbbb01e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   384660359   192330148+  83  Linux
/dev/sdb2       384660360   390716864     3028252+   5  Extended
/dev/sdb5       384660423   390716864     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```

I'm assuming you're looking for the actual menu.lst :)

```
ubuntu@ubuntu:~$ cat /media/disk-1/boot/grub/menu.lst
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
# kopt=root=UUID=2600b668-01b2-41c0-a952-dd000d1cfdfe ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2600b668-01b2-41c0-a952-dd000d1cfdfe ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2600b668-01b2-41c0-a952-dd000d1cfdfe ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Dell Utility Partition
root            (hd1,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Windows XP Media Center Edition
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:~$ 

```

Thanks for the help. Seeing as I know very little about Sata, does it matter if I switch the cables around on the motherboard? I have 4 ports and 2 cables which I've been moving around because I have to unplug the Ubuntu disk to get windows to boot.
Edit: one of them is blue. I guess that means that that's the one it boots from. Also, when I try to boot into windows from grub, it gives error 21: selected disk does not exist. :(

---

### Post by Pumalite on 2007-11-11
First backup:
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.back
gksudo gedit /boot/grub/menu.lst

Edit all the ubuntu entries to 'root  (hd1,0)'
Edit Windows entry to 'root  (hd0.1)'
Save, exit, reboot.

---

### Post by rabiddachshund on 2007-11-13
I assume you meant the windows entry to have a comma instead of a period.
Booting windows now gives an error 12: invalid device requested.
Booting Ubuntu now gives error 21: Selected disk does not exist.

I tried to format and install Feisty but now my wireless keyboard doesn't work.It's 2 years old though so I guess it's about that time. I hope this isn't a sign. :(

---

### Post by Pumalite on 2007-11-13
Change this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
To this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
Add the changes to all the Ubuntu entries and 'kropt'
And this:
title           Windows XP Media Center Edition
root            (hd1,1)
To this:
title           Windows XP Media Center Edition
root            (hd0,1)

Save, exit and reboot.

---

### Post by NiceCup OfTea on 2007-11-14
Just thought I'd give you all an update on progress (or lack) so far.

Through lots of use of the Windows recovery console I have managed to get the windows boot.ini correctly set up so it's looking in the right place.

Now it complains that hal.dll is corrupt or missing.  As Dabl pointed out Windows likes to keep it's own record of all the hardware and this is the dll for that job.

Currently working through the Google'd suggestions for fixing this.

At some point I will get so p****d off with this that I'll cave in a do a complete re-install of Windows.

Many thanks to bulldog for his menu.lst entry which is working a treat.

Stone the crows! It's just started working - as I type - booting into Windows from my hard disk.  Not out of the woods yet it's asking for activation... and it failed to activate and then logged me out - bummer!

Says I have to phone our lords and masters in Redmond to be allowed to use this OS I bought....

Oh well, enough for tonight, that was 2.5 hrs of unremitting pain so it's time to do something else.

---

### Post by rabiddachshund on 2007-11-20
> **Pumalite said:**
> Change this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
To this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
Add the changes to all the Ubuntu entries and 'kropt'
And this:
title           Windows XP Media Center Edition
root            (hd1,1)
To this:
title           Windows XP Media Center Edition
root            (hd0,1)

Save, exit and reboot.

I finally got my keyboard replaced *and* had some free time to mess with it. I did what you said  but neither disk boots. I managed to change it back by booting from the live cd but now that I think about it, Ubuntu boots fine. Why would I change that?

Are we positive that this is a problem with menu.lst and not something else?

---

### Post by rabiddachshund on 2007-11-20
> **Pumalite said:**
> Change this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
To this:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
Add the changes to all the Ubuntu entries and 'kropt'
And this:
title           Windows XP Media Center Edition
root            (hd1,1)
To this:
title           Windows XP Media Center Edition
root            (hd0,1)

Save, exit and reboot.

I finally got my keyboard replaced *and* had some free time to mess with it. I did what you said  but neither disk boots. I managed to change it back by booting from the live cd but now that I think about it, Ubuntu boots fine. Why would I change that?

Are we positive that this is a problem with menu.lst and not something else?
device.map shows

(hd0)    /dev/sda
(hd1)    /dev/sdb

so they're labeled correctly and I can mount/browse the windows disk but... wait a minute. Is the disk not mounting correctly during startup or something?

edit: D'OH! Bios had the sata port turned off. Turned it on an windows boots perfectly. Thanks to Scunizi (sp?) from the irc chat room for providing this link:
[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
Now I'm off to figure out how to get my Linksys wmp54g to work.

---

