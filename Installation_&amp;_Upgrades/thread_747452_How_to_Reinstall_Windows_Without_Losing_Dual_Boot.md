---
title: "How to Reinstall Windows Without Losing Dual Boot"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by LaneLester on 2008-04-06
I suspect this is answered more than once, but I couldn't come up with the search terms to find the thread.

I have a dual, well, triple boot setup, and I want to install Win2K on sda1. I believe I recall reading that Windows will overwrite the MBR during the install. How do I restore the grub boot from Ubuntu in sda4 after that's done?

Lane

---

### Post by greenstar on 2008-04-06
Directions for exactly that are found in [Community Documentation]("https://help.ubuntu.com/community"). 

The instructions you want are: [Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

HTH

Greenstar

---

### Post by LaneLester on 2008-04-06
Thank you very much.

Lane

---

### Post by greenstar on 2008-04-07
You're welcome.

---

### Post by Curious65 on 2008-04-08
using your link <b>greenstar</b> i was able to get my box to dual boot again so thank you for that.

however what i wanted to do was triple boot like <b>LaneLester</b> but after further reading it seems that i will need three HDDs. 

currently have hda1 - XP Pro; hda2 - ext3 empty; hdb1 - Ubuntu 7.10; hdb2 - Kubuntu 7.10
hda1 and hdb1 are active. if i understand correctly only active partitions can boot so the "menu.lst" that is in the Kubuntu install on hdb2 and has all three OS doesn't matter since it isn't on an active partition. and even if i make it active and grub shows Ubuntu as an "other operating system" since that partition is no longer active it won't boot if selected.

---

### Post by Curious65 on 2008-04-08
i am attaching the Kubuntu menu.lst for clarity. reading it sure makes it look like i could triple boot except for that pesky active partition thing.

when i run grub> find /boot/grub/stage1 what is returned is: (hd1,0) and (hd1,2)

if i do this:
grub> root (hd1,0) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub

the computer boots to grub with Ubuntu and Windows as selections.

if i do this:
grub> root (hd1,2) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub

i get an error 17. which is where i started after the Kubuntu install. thanks to you folks that's fixed.

---

### Post by greenstar on 2008-04-08
You can do triple-boot on one hard drive, provided your partitioning scheme allows it, and your disk has enough capacity. You can only have 4 primary partitions, of which an extended partition is one. To get around this limitation, create a big extended partition and then create multiple logical partitions within. You'll see what I mean when you get there. Your partitioning scheme will likely be similar to this: 

NTFS (Primary) for Win
Linux-Swap (Primary) to be Shared between your distros
Linux (Primary) Your choice of filesystem
Extended (Primary) Contains the rest of your partitions
>>Linux (Logical) Your choice of filesystem
>>Linux (Logical) Your choice of filesystem

If you wanna get fancy, you can create yet another logical partition for your /home directories (each distro needs it's own home - they don't like to share), and then create directories for each distro's /home. So the Home partition will have, say, an Ubuntu directory, a Kubuntu directory, and a SuSE directory. Inside those directories go the /home for the respective distro. You can even wait to move your /home there after installation and then delete /home from / and put a symlink to your new /home location.

Also, see [this thread]("http://ubuntuforums.org/showthread.php?t=450879") about creating a shared FAT32 partition to share data between Operating Systems. You can read more detail about partitioning [here]("http://www.pcguide.com/ref/hdd/file/struct_Partitions.htm").

Hope I didn't just overload you with TMI.

HTH,

Greenstar

---

### Post by Curious65 on 2008-04-08
> **greenstar said:**
> 
Hope I didn't just overload you with TMI.


no it's not too much i'll just need time to absorb it. it doesn't address the "only active partitions are bootable" part of my post but i could have misunderstood that. 

i wanted to look at my partitions using QTParted but it says i must be root and i have yet to figure out how to get into root at will. usually when you have to be root the box pops up, you log in and presto. but not always and with Ubuntu it seems to hide it. unless one must use the terminal and that isn't my strong point.

---

### Post by greenstar on 2008-04-08
Download & burn Parted Magic [LiveCD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads").

You have to unmount partitions before you can change them, so a LiveCD or LiveUSB works better & easier. At ~42MB it's a small download for a LiveCD.

Greenstar

---

### Post by Curious65 on 2008-04-08
ok i burned Parted Magic and booted to it but the format is different from QTParted and i exited it. i can boot to QTParted from a Knoppix live CD and it's what i'm used to. sorry to appear ungratful but i'm confused enough as it is :)

one more question before i have to get some sleep. in your post #7 you didn't address the active partition subject. i have been reading your link to partition details and it talks about boot loaders being able to set active partitions as needed. from the link:
"It analyzes the primary partitions on the disk and then presents a menu to you and asks which operating system you want to use. Whichever one you select, it marks as active, and then continues the boot process from there."

since my HDD list in post 5 looks a lot like yours in post 7 what happens if i just set hdb2 as active? i'll have to use the "sudo grub" setup to change the path to the Kubuntu menu.lst but (to me) it looks like that might work.

if i get into repartitioning, with or without extended partions, then there's a good chance i'll have to reinstall all three OSs. or not. right now i need to walk away and let all this perk in the back of my head. 

thanks again.

---

### Post by greenstar on 2008-04-09
> **Curious65 said:**
> 
hda1 and hdb1 are active. if i understand correctly only active partitions can boot so the "menu.lst" that is in the Kubuntu install on hdb2 and has all three OS doesn't matter since it isn't on an active partition. and even if i make it active and grub shows Ubuntu as an "other operating system" since that partition is no longer active it won't boot if selected.


I need you to break that into manageable pieces and ask me again. I'm not quite sure of the question, actually I think it's probably several questions in one. :-k

Greenstar

---

### Post by Curious65 on 2008-04-09
have to go to work. will be back in about  7 hours and try explaining what i meant.

---

### Post by Curious65 on 2008-04-09
ok let's start with an abbreviated "menu.lst" that was created when Kubuntu installed.
above the line there is:
title		Ubuntu 7.10, kernel 2.6.22-14-generic [this should be the Kubuntu install]
root		(hd1,2)

then the recovery mode one
then memtest86+

then the line for "other operating systems"
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hdb1) [this is original Ubuntu]
root		(hd1,0)

then the line for generic
memtest86+

etc,etc.

now let us clear up something else. /dev/hda1 has a root of (hd0,0) so from the we can assume (yeah i know about assuming :)) that hda1 and partition (hd0) are the same. that said then hdb1 and (hd1) are the same and are physically the second hard drive first partition. 

now i have two HDD and each drive has two partitions.
/dev/hda1 is windows -- this is the active partition for this HDD
/dev/hda2 is empty and formated as ext3
/dev/hdb1 is Ubuntu 7.10 -- this is the active partition for this HDD
/dev/hdb2 is Kubuntu 

when i run grub> find /boot/grub/stage1 what is returned is: (hd1,0) and (hd1,2)
that tells me that if i run the grub setup steps using either of those values the computer should boot. but it doesn't if (hd1,2) is used. 

if you use the file browser to navigate to (hd1,2) the menu.lst shown above is found. 

except for there being an additional operating system  the only basic difference in (hd1,0) and (hd1,2) is that the first is on an active partition and the second isn't. and your link and other places i've read say that to boot from a partition it must be active. and you can only have one active partition per HDD. then  there is this from your link:
"There are programs specifically designed for this task; they are usually called boot managers or boot loaders. What a boot manager does is insert itself into the very beginning of the boot process, sometimes by setting up a special boot manager partition and making itself the active partition. When you boot up the PC, the code in this partition runs. It analyzes the primary partitions on the disk and then presents a menu to you and asks which operating system you want to use. Whichever one you select, it marks as active, and then continues the boot process from there."

grub is a boot loader so what i'm currently thinking is run the grub set up and point it at (hd1,2) then boot into QTParted and make the second partition of the second drive active. then reboot and pray. 

thanks again for your help. i reread all the above and it makes sense to me but if i knew what i was doing i wouldn't be here.

---

### Post by greenstar on 2008-04-10
I've been really busy with work today. I'm going to have to look closely at the info you gave me in the last post and let it stew for a bit. 

Greenstar

---

### Post by Curious65 on 2008-04-10
well i've been playing with this problem and have decided that the active partition part doesn't matter. or it matters only in that the MBR is on an active partion.

when you do the grub> setup (hd0) thing it writes grub from whereever it is to the MBR if i'm not nuts. or if i learned anything so far. 

in my particular case:
grub> root (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82
   Partition num: 5,  Filesystem type unknown, partition type 0x82

and if i use (hd1,0) then ubuntu/windows load as options.

if i use (hd1,2) then it's error 17 time.

i have tried this several time making either partition one or two of /dev/hdb active and it makes no difference. i get a dual boot to what i had before installing Kubuntu or i get nothing, no boot. 

it may be that my install is bad although looking at the menu.lst it sure seems ok. maybe the problem is in the stage 1.5 file or something related to the boot sequence. in that case i would't know how to fix it even if i could get into the file. 

i downloaded super grub disk but haven't tried it yet. i also read about problems with the device map but that isn't the problem here. 

if nothing else i'm learning which is always a plus. 

thanks again. if you have any thoughs about this newest post or just want to wish me good luck either would be appreciated.

---

### Post by greenstar on 2008-04-10
I've still not been able to grok all that stuff you posted in the last few posts, the info is convoluted and would be far more usable/understandable if presented like data rather than a story.:confused:

It would help if you posted the contents of your /etc/fstab and /boot/grub/menu.list so I can see the relevant info as data.

The following occured to me after skimming over your last couple of posts. Setup GRUB for the way it will boot win & ubuntu and then just copy the boot lines from the grub menu.list on your kubuntu and paste it into the menu.list on your ubuntu in the appropriate place.

Before you edit grub's menu.lst back it up with:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
```

HTH,

Greenstar

---

### Post by Curious65 on 2008-04-10
sorry about the narrative. from the Ubuntu install:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=d0189195-c367-417e-913b-a7210b17d908 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=f06a9435-8bd1-4ff6-b2fe-a7ce096ce83b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto  0       0

> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
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

from the Kubuntu install:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=cb063d83-a600-4f2d-8335-b30ce1a986cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=c0bbf595-7574-416f-9a11-38cf2c3e5769 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec 0       0

> ## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb063d83-a600-4f2d-8335-b30ce1a986cb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb063d83-a600-4f2d-8335-b30ce1a986cb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d0189195-c367-417e-913b-a7210b17d908 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot



ok, googled /etc/fstab but don't understand it yet except in a vague way. will read up more on it later. also looked up UUID and will read more on that later. looks like "menu.lst" starts an OS booting and /etc/fstab mounts the various drives. 
***BTW that second floppy is a 5 1/4 drive just because i thought it would be fun to have.

re the editing of menu.lst when you say "appropriate place" i'm thinking you mean under the "other operating systems" part. and if so i'll have to use the "root (hd1,2)" and won't i be back where i started? but hey it's worth a try tomorrow. 

in any case one more thank for the time you have put into this. i really do appreciate it. as does my wallet because the other choice seems to be another HDD. fortunately this box has a raid M/B and i can add a drive if needed.

---

### Post by greenstar on 2008-04-11
> **Curious65 said:**
> in any case one more thank for the time you have put into this. i really do appreciate it.

You're welcome. 

I don't think I even suggested the obvious yet:
From within Ubuntu, do:```
sudo update-grub
```Tell me what you get.

---

### Post by Curious65 on 2008-04-11
> **greenstar said:**
> 
Tell me what you get.

> dave@linux1:~$ sudo update-grub 
[sudo] password for dave: 
Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.22-14-generic 
Found kernel: /boot/vmlinuz-2.6.20-16-generic 
Found kernel: /boot/memtest86+.bin 
Updating /boot/grub/menu.lst ... done 

nothing changed. i'm thinking it just used the old one w/o Kubunu.

haven't tried editing the menu.lst yet.

---

### Post by Curious65 on 2008-04-12
did the edit to menu/lst by adding the Kubuntu install below the windows install in "other operating systems".

once i had an edited menu'lst i rebooted to the OS selection screen .... there was Kubuntu just as promised. so i selected it, hit enter

error 18: Selected cylinder exceeds maximum supported by BIOS

no idea why i'm getting this. although the total HDD size isn't reported correctly in the BIOS that didn't (and doesn't) seem to matter for the Ubuntu install which is on the same drive. don't remember running a HDD overlay when doing the Ubuntu install but may have and if that is only on/in the (now) first partition well ......

will have to play with this some more. when all this is corrected i'll post a follow up. it may be a few days :)

---

### Post by Curious65 on 2008-04-15
hi **Greenstar** perhaps you thought i'd given up. but no, i prevailed and (finally) got the triple install to work.

not only that but i did a manual install ..... not the guided one .... WOOT

if nothing else i've learned a lot. the install of Kubuntu is on HDD one with the Windows install where i wanted it all along.  HDD two has the good Ubuntu install and the won't boot Kubuntu install. at some point i'll delete that and clean up the present menu.lst to get rid of it there also. 

besides wanting to brag a bit i also wanted to thank you again for your help. the link to "recovering Ubuntu after installing Windows" was a big help. not only early on but even today when during a Kubuntu install the grub installer had a fatal error and quit. 

so to recap: triple install working
                  thanks again

---

### Post by greenstar on 2008-04-18
Glad I could help.:)

Greenstar

---

