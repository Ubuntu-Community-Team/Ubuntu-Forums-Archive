---
title: "Grub installation lost XP"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Fishbowler on 2008-04-13
Good Afternoon,

Perhaps someone can point me in the direction of some grub configuration advice?

I've got a Xubuntu file server and I love it muchly, so I took the decision yesterday morning to get Ubuntu going on my desktop, with a view to adding Vista shortly thereafter.

Before I started, I had 2 partitions, one extended containing XP (not sure why the XP installer chose that), and one other holding data. I realised that I'd need a further 3 partitions - one for Vista and 2 for Linux (inc swap). That would bring me up to 5. My solution (perhaps unwise) was to, after shrinking it, convert the data partition into a second logical partition within the extended partition in which XP resided. It took 12 hours to do, but I got it done.

I then found that XP wouldn't boot. As it turns out, the partition I'd moved was active and had been holding the NTLDR, boot.ini, etc. My solution was to create the Vista partition next, copy the booting bumpf to it, set it to active, and voila - I was back into Windows, and still had free space at the end of my drive for linux.

Next, I used the Ubuntu 7.10 Live CD to install Ubuntu. I let it install grub, got to the Ubuntu desktop, ran the software updates, saw my NTFS drives on the desktop - all was normal. Then I tried booting Windows again.

Grub recognised 3 XP installations. Two gave Error 12 when attempting to boot. One actually tried and gave "%systemroot%\system32\hal.dll could not be found" etc.

After searching around, I found information about using map commands, and why they were used for Windows. This didn't work either.

Please feel free to ask for more back-story or state information. Here is the disk layout according to fdisk and according to me (i.e. in disk order and with real labels). Following that is the grub config file as it stands.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       31901   256236750    f  W95 Ext'd (LBA)
/dev/sda2   *       38719       38913     1566337+  82  Linux swap / Solaris
/dev/sda3           31902       37639    46090485    7  HPFS/NTFS
/dev/sda4           37640       38718     8667067+  83  Linux
/dev/sda5               2        2550    20474811    7  HPFS/NTFS
/dev/sda6            2551       31901   235761876    7  HPFS/NTFS

```


```
 
 - Extended Partition (sda1)
    - Windows XP (sda5)
    - Data (sda6)
 - Vista (sda3)
 - Linux / (sda4)
 - Linux Swap (sda2)

```


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

<snip>

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Professional
map		(hd0,0) (hd0,4)
map		(hd0,4) (hd0,0)
root		(hd0,4)
#savedefault
#makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Professional
root		(hd0,5)
savedefault
makeactive
chainloader	+1

```

*Any* suggestions welcome.

TIA.

Fishbowler

---

### Post by Pumalite on 2008-04-13
Vista and XP, both need primary partitions to boot. From there you can create an 'extended' partition within which you can have as many logicals as you want. Ubuntu is happy in a logical

---

### Post by Fishbowler on 2008-04-13
XP was always in an extended partition, with the boot.ini on the the second (a primary). Now it's on the third (also a primary).

Before installing Ubuntu, this situation worked.

Surely, therefor, it's just a case of getting the Grub settings right?

---

### Post by Pumalite on 2008-04-13
Post a screen shot of Gparted

---

### Post by prshah on 2008-04-13
> **Fishbowler said:**
> 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       31901   256236750    f  W95 Ext'd (LBA)
[color=red]/dev/sda2   *       38719       38913     1566337+  82  Linux swap / Solaris[/color]
/dev/sda3           31902       37639    46090485    7  HPFS/NTFS
/dev/sda4           37640       38718     8667067+  83  Linux
/dev/sda5               2        2550    20474811    7  HPFS/NTFS
/dev/sda6            2551       31901   235761876    7  HPFS/NTFS

```


Why is your _swap_ partition set as bootable and no other?

---

### Post by Fishbowler on 2008-04-13
Here is the screenshot requested.

---

### Post by Fishbowler on 2008-04-13
Which should be bootable?
And what's the best way to go about doing it?

---

### Post by Pumalite on 2008-04-13
Whick partition is your main Windows?(Vista?)
I still suggest your partitions for Windows should not be within an extended partition.

---

### Post by Fishbowler on 2008-04-13
The 19.53GB partition is XP.
The 43.96GB partition is the partition I created for Vista, but is empty aside from ntldr, ntdetect.com and other Windows-related files.

---

### Post by Pumalite on 2008-04-13
use Gparted and move the boot flag to sda5
Remove the mapping in menu.lst for XP

---

### Post by Fishbowler on 2008-04-13
Done. I'll reboot and let you know how it goes.
Thanks for your help! :)

---

### Post by Fishbowler on 2008-04-13
Same result.

The first XP launcher gives the hal.dll missing error
The second gives "Starting Up..." or some such, but gets no further.
The third gives Error 12,

---

### Post by Pumalite on 2008-04-13
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)
I suggest you start from scratch after backing up everything.

---

### Post by Fishbowler on 2008-04-13
Could I not use a partitioning tool to bring Windows out of the extended partition?
I'd have to drop the Vista partition for the time being, but it'd surely save me the headache of backing up, re-installing, restoring, reconfiguring, etc?

Other than that, given that the system was booting pre-grub, is there anything I can do to circumvent grub, or to reconfigure grub?

---

### Post by Pumalite on 2008-04-13
I wish I could help you, but I cannot think of any other way. Maybe someone else has an answer.

---

### Post by Fishbowler on 2008-04-13
I've scrapped the Vista partition and made the DATA partition primary again (as they were before I ever started partitioning).

I attach a new screenshot.

Given that /dev/sda3 has the boot.ini on it, and is flagged bootable, what would be the proper grub settings now?
Is there a way to get grub to re-scan to adapt to my changes?

---

### Post by Herman on 2008-04-13
:) Hello Fishbowler,
Your problems have nothing at all to do with GRUB and everything to do with Microsoft Windows and the way Windows dual boots in the first place.

When you first install more than one Windows in your computer, you need GRUB or some other boot manager to 'hide' the first Windows installation from the next one you want to install.
If you do that then they will each install in a primary partition and each retain thier own boot loader files and each remain independant of one another.
You can use GRUB in a dedicated GRUB partition for that, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), or you can use GRUB from a CD or floppy disk, or you can use [GAG Boot Manager]("http://gag.sourceforge.net/") or a hard disk partitioning program to 'hide' your Windows partition before installing the next one.
[GRUB and MultiWindows]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_")
If you don't, Microsoft is programmed if it detects another Windows, to set up a Microsoft style dual boot, in which your vital boot loader files get copied to an older Windows installation in a primary partition, and the new Windows will be installed in a logical partition. Here's a link about that, [Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") by Dan Goodell, particulary note this page, [Background - Multibooting Principles]("http://www.goodells.net/multiboot/principles.htm").

By co-incidence I have just been running a lot of experiments with this over the weekend, and what I found out is that you CAN boot Windows in a logical partition with GRUB.
You should copy your boot loader files ntldr and NTDETECT.COM back into Windows XP, (I don't know anything about Vista), and either paste in a boot.ini file or run BOOTCFG /REBUILD om the partition from a Windows recovery console to generate or repair the boot.ini file.

Then, you do as Pumalite suggested earlier and use GParted to place the boot flag on the logical partition.

GRUB can't put the boot flag on a logical partition, only a primary partition.
The boot flag is the main thing you need to boot Windows.
When GRUB tries to do it, it can't and gives you GRUB error 12 and gives up.
You need to delete the 'makeactive' command from your /boot/grub/menu.lst boot stanza for Windows in the logical partition in order for GRUB to skip that and not be stopped by that problem.
You may (most likely) need to use GRUB's 'hide' and 'unhide' commands to hide the other Windows installations too.
Then you should be able to boot Windows in a logical partition.

GRUB can do it if you know how, it's Windows that causes all the problems.

Regards, Herman :)

---

### Post by Pumalite on 2008-04-13
Live and learn. Cheers Herman.

---

### Post by Fishbowler on 2008-04-13
Thanks to everybody for their help so far!
Bored of brain-aching with this logical malarkey, as I have been for yonks now, I used a partitioning tool to make the logical a primary.

I now have:
 - Windows
 - (Data)
 - Linux
 - Linux Swap

What do I need to do to make Windows run again?

The boot flag wasn't enough, and neither was root (hd0,1).
I've tried a couple of the options on Super Grub Disk (like "Boot Windows") but that's not having it either.

---

### Post by Pumalite on 2008-04-13
If you have Windows in sda1, 'root' should be (hd0,0)

---

### Post by Fishbowler on 2008-04-13
Just so I'm sure, after setting sda1 as boot, I should have menu.lst set to the following:

```
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Do I need the makeactive line??


Thanks again for all your efforts.

---

### Post by Pumalite on 2008-04-13
Let's take a goo look at how you left your stuff. Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Fishbowler on 2008-04-13
Good plan.
Here's the state of things at the moment.
Partitions have changed. Grub menu hasn't.

```

dan@DeckTwo:~$ sudo fdisk -lu
[sudo] password for dan:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e552e54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16128    40965749    20474811    7  HPFS/NTFS
/dev/sda2       622004670   625137344     1566337+  82  Linux swap / Solaris
/dev/sda3        40965813   512489564   235761876    7  HPFS/NTFS
/dev/sda4       604670535   622004669     8667067+  83  Linux

Partition table entries are not in disk order
dan@DeckTwo:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Microsoft Windows XP Professional
root            (hd0,2)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title           Microsoft Windows XP Professional
map             (hd0,0) (hd0,4)
map             (hd0,4) (hd0,0)
root            (hd0,4)
savedefault
makeactive
chainloader     +1


```



Thanks yet again!

---

### Post by Pumalite on 2008-04-13
You don't need mapping since you have only one hard drive.XP should be (hd0,0) Ubuntu is fine. Eliminate or comment out the redundant XP.

---

### Post by Herman on 2008-04-14
> Thanks to everybody for their help so far!
Bored of brain-aching with this logical malarkey, as I have been for yonks now, I used a partitioning tool to make the logical a primary.

I now have:
 - Windows
 - (Data)
 - Linux
 - Linux Swap

What do I need to do to make Windows run again?

The boot flag wasn't enough, and neither was root (hd0,1).
I've tried a couple of the options on Super Grub Disk (like "Boot Windows") but that's not having it either.:) Good idea! That's another way to do things.

Now you just need to copy your ntldr file and your NTDETECT.COM file and a boot.ini file into the root (top directory) of your Windows 'C: drive' (partition) you are trying to boot. 
The reason for that is because GRUB doesn't actually boot Windows by itself, rather, it wakes up the Windows boot loader, (ntldr), and ntldr boots Windows. 
It wakes up ntldr by 'chainloading' (tickling) Windows boot sector. 
So, you need the three vital Windows boot loader files to be inside your Windows 'C:' drive in order for Windows to boot.
You can copy in those files from another Windows even, if you have to, but since you already have them in your data partition, just copy those and paste then into your Windows partition.

Your boot.ini file for Windows in a first partition will look something like this, if it has the wrong partition number in it you might need to edit it with the right partition number, which will now be (1).
```
[boot loader]
timeout=30              
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)WINDOWS="Microsoft Windows XP Professional" /fastdetect
```Your /boot/grub/menu.lst entry for Windows should look like this, 
```
<snip>
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5e22802f-4f90-48ff-9554-7626d416283f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[COLOR=Sienna][B]title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/B][/COLOR]
```You need to keep the 'makeactive' command now, it's only when you had it in the logical partition that you didn't want it.
The 'makeactive' command tells GRUB to set the boot flag on that partition and GRUB can now, because it's now a Primary partition like any normal Windows installation. :)

It should boot when you put in the Windows boot loader files.

---

