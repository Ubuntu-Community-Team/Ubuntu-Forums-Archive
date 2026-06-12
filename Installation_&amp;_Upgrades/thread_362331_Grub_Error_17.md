---
title: "Grub Error 17"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by rsampaio on 2007-02-15
I searched on the forums but could not find any answers except somebody requesting the fdisk -l and menu.lst files

I am receiving Stage 1.5 error 17 right when I boot my pc, the menu doesnt even load. I have just upgraded to the latest version of edgy eft.

so without further ado:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       28608   229793728+   7  HPFS/NTFS
/dev/hda2   *       28609       30320    13751640   83  Linux
/dev/hda3           30321       30401      650632+   5  Extended
/dev/hda5           30321       30401      650601   82  Linux swap / Solaris

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
# kopt=root=UUID=553f45e3-5a25-4fb1-a48d-7c195bb1436b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-8-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-8-generic root=UUID=553f45e3-5a25-4fb1-a48d-7c195bb1436b ro quiet splash
initrd		/boot/initrd.img-2.6.20-8-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-8-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-8-generic root=UUID=553f45e3-5a25-4fb1-a48d-7c195bb1436b ro single
initrd		/boot/initrd.img-2.6.20-8-generic

title		Ubuntu, memtest86+
root		(hd0,1)
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
```

Thanks in advance!

ps: I am trying to dual boot between my Windows Xp and Ubuntu, ubuntu being hda2.

---

### Post by rsampaio on 2007-02-15
So I've tried to reinstall ubuntu and the error persists... I edited the post above with the new menu.lst and etc...

Sorry to bother once more :(

---

### Post by rsampaio on 2007-02-15
bump

---

### Post by geek_Man on 2007-02-15
You might try reinstalling GRUB. Go to the terminal and type: 
```
sudo grub
root(hd0,1)
setup(hd0)
quit
```

Hopefully that'll fix it. Post back if it doesn't.

EDIT: If you tried this before I edited this post, you might have to do it again (I changed setup(hd0,1) to setup(hd0) which is what it should be).

---

### Post by rsampaio on 2007-02-15
Thanks for your prompt help geekman, I tried your solution but it didnt work for me... this is the output I got on terminal:
```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 

```

When I rebooted the error persisted...

---

### Post by Herman on 2007-02-16
Hello rsampaio,
That's the first example I have seen with filesystem UUID code completely replacing the old familiar root=/dev/hdx,y at the end of your kernel line in your menu.lst file.

Cool!

Perhaps that's where your problem will be though. You should try to verify that the filesystem UUID number in your menu.lst matches your actual filesystem UUID.
Here's [Grub Error 17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17"), that's why I think that this is a likely thing to look at.
Here's a little about filesystem UUID numbers and how to find out what your filesystem UUID numbers are. [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")
You should probably use this command, open a terminal and for best results make the terminal Window expanded to the full size of your monitor for the output to be easist to read,
```
ls /dev/disk/by-uuid/ -alh
``` Compare the results of that with the UUID number in your menu.lst. You can copy and paste the UUID number from the terminal to your menu.lst if that's the problem, overwriting the old UUID number.

I hope that's the right answer. If you still need more help, you are welcome to keep asking questions.

Regards, Herman :)

---

### Post by rsampaio on 2007-02-16
Thank you very much for your prompt help. But before I read the post I just decided to do a clean install and settle with windows inside qemu. Thank you all for your hard work :)

---

### Post by phoenix9262 on 2007-02-16
ok guys, i'm a total noob at linux, and this is my first attempt at it and this i what i got: Error 17. Nothing will load. I have windows XP on my main HDD and Ubuntu on my second HDD. I thought this would work, and in worse case i won't lose all my windows work. But like i said, nothing loads, not even when i unplug one HDD and try to use the other. And remember, i'm a total NOOB at this. Help?

EDIT: i just checked the partitions, 1Gb for the swap, 10 for ext 3. the rest (roughly 129Gb) is NTSC for windows.

---

### Post by Herman on 2007-02-16
Hello phoenix9262,
_Method 1)_ If you download (for free) a [Super Grub Disk,]("http://supergrub.forjamari.linex.org/") you should be easily able to boot up either Windows or Ubuntu (or any other operating system). SGD can be burned to A CD or a floppydisk or a USB, depending on which file you choose to download. That is the most user freindly tool we have.
Visit this page for instructions, [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
[LEFT]Since the error will likely be in your /boot/grub/menu.lst, the way to boot with SuperGrub Disk will be: [COLOR=DarkRed]'English Super Grub Disk'-->'Gnu/Linux'-->'Gnu/Linux Advanced'-->'Boot Gnu/Linux Directly'-->'Same Root and Boot Partition'-->(then choose either IDE or SCSI disk)-->(select hdb, your second disk)-->(select which partition has Ubuntu in it)-->... and Ubuntu will boot.[/COLOR]
[/LEFT]
 Then when Ubuntu is booted, if you can post a copy here of two things, the bottom of your menu.lst file and a look at your partition table from fdisk, and maybe your device.map file as well. I will give you the commands here to obtain those files, and then someone can help you fix it permanently,
```
sudo fdisk -lu
``````
sudo gedit /boot/grub/menu.lst
``````
sudo gedit /boot/grub/device.map
``` Someone can give you specific help you when we see the output from those commands.

_Method 2)_ Another way is to try out Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and boot your computer that way and take notes of the exact commands you used that worked and then fix your menu.lst with them when your system boots.
That is a good way to solve booting problems with Grub.

_Method 3)_ A third method is to boot the Ubuntu Desktop LiveCD and use the sudo fdisk -lu command the same as already given above.
Then for the other two commands you'll need to 'mount' your Ubuntu filesystem (partition) first. The other two commands given above will need to be slighly modified to find the information we need to know to help you. 
But first, here is how to mount your Ubuntu filesystem in a Live CD, 
[                           Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
If you have never 'mounted' a filesystem in your life before, you may prefer to take the [same page, and start reading it down from the top]("http://users.bigpond.net.au/hermanzone/p10.htm"), I think it is explained pretty well, but if you have trouble, let me know.
Commands to use will be,```
sudo gedit /media/ubuntu/boot/grub/menu.lst
``````
sudo gedit /media/ubuntu/boot/grub/device.map
```The main idea is, the problem is probably caused by a mistake in your /boot/grub/menu.lst file, and someone can tell you how to fix it. Here is an illustrated explanation about what the /boot/grub/menu.lst file is and where to find it, and just about all about it. [Orientation........(for new users only)]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation")

Use whichever of those methods you think will be the easiest for you.
Do not worry, you will not lose any files, (well not from bootloader problems anyway). 

Regards, Herman :)

---

### Post by geek_Man on 2007-02-16
Can you do what I told rsampaio and post your menu.lst file and the output of "sudo fdisk -l"? The directions are above.

EDIT: Or do what Herman says...

---

### Post by phoenix9262 on 2007-02-16
well, i got this "Error 18, selected cylinder too big for BIOS"

EDIT: I'm running the liveCD. what should i do now?

---

### Post by Herman on 2007-02-16
Are you using IDE disks or SATA? If you have IDE disks, are you using cable select or jumper settings?
> nothing loads, not even when i unplug one HDD and try to use the other Grub error 18 can have any of several possible causes, but as you did mention uplugging your hard disks, please unplug them again and double check your connections (cables) and jumper settings. make sure they are the same as when you installed Ubuntu. 
Otherwise, can you tell me more about your hard disks? Is the one with Ubuntu on it new, and if so, is it a rather large one?
And which method were you trying when you got the grub error 18? SuperGrub Disk?

Regards, Herman

---

### Post by phoenix9262 on 2007-02-16
ok, my main disk with windows is 40GB, the one with linux is 160. so, i just reforammtted some stuff to erase it al, so now i can get into windows.

EDIT: does linux on a slave cause that problem?

---

### Post by Herman on 2007-02-16
> ok, my main disk with windows is 40GB, the one with linux is 160. so, i just reforammtted some stuff to erase it al, so now i can get into windows.
EDIT: does linux on a slave cause that problem? These grub errors are a great help to begin with, for troubleshooting and problem solving but they are really only a beginning point. They don't always tell us *exactly* what's wrong. That's why we need the other info to go with it. We almost always need the output from those commands I gave earlier. Then with the combination of all that info, we can start making some sense out of it. Sometimes we can see what's wrong right away, other times we need to just keep trying different possibilities until we get it to work.

Here's a few brief hints about [Grub error 17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

And here are a few clues about  [Grub error 18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18"), but these can't exactly tell us everything, we still need to do more investigating and use our heads a little and maybe try a few ideas. Sometimes we can easily solve problems right away, the first try, sometimes it takes longer. 

Linux on a slave is no problem. Check your BIOS and see if it is able to handle such a nice large hard disk maybe? Perhaps you have an 137GB hard drive limit in your BIOS and you can flash your BIOS with a newer version to fix the problem. (I'm just guessing.)
Also, check in CMOS (BIOS settings) that LBA is enabled. That has solved grub error 18 problems for one or two people in the past.

Regards, Herman :)

---

### Post by phoenix9262 on 2007-02-16
ok, yes, it handles the full 160Gb (more precisely, 149), but i don't know what LBA is. also, i'll upload that menu stuff next time i'm on.

---

### Post by Herman on 2007-02-16
Chances are if your computer is less than 5 years old or so, it will be able to handle almost any size hard disk.

LBA is '[Logical Block Addressing]("http://en.wikipedia.org/wiki/Logical_block_addressing")', and means (roughly speaking) that instead of having the BIOS working with the hard disk in the old fashioned CHS (Cylinders, Heads and Sectors), it works by counting the number of sectors from the first sector, sector 0, upwards. That's how Linux got over the 7.8 GB BIOS hard disk size limit. 'Other' operating systems then adopted the idea too. It would be unlikely to have LBA turned off in your CMOS, it would be on by default, and not many people would want to turn that off. But it is a possibility, (just something to check). It has been reported in the past to have been found switched off, (who knows how), and caused Grub error 18 for someone. Just switching it back on solved their problem.

Regards, Herman :)

---

### Post by phoenix9262 on 2007-02-17
ok, here's the stuff

EDIT: I reformatted everything to get rid of grub and linux, but here's the specs on the system. also, i'm reinstalling linux onto my main drive, so i'll send the info back when it's done:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   270679184   135339561    7  HPFS/NTFS
/dev/hdb2       270679185   291162059    10241437+  83  Linux
/dev/hdb3       291162060   292206284      522112+  82  Linux swap / Solaris

Disk /dev/sda: 1004 MB, 1004699136 bytes
31 heads, 62 sectors/track, 1020 cylinders, total 1962303 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62     1960439      980189    b  W95 FAT32

Damnit, I killed windows, i reformatted the NTFS into a linux partition. This is gonna be a while for fixing...

---

### Post by Herman on 2007-02-17
>  I have windows XP on my main HDD and Ubuntu on my second HDD.Hello phoenix9262,
Thanks for the fdisk output. It looks like you have three drives there, one IDE dirve of 40 GB, and IDE drive of 160 GB, plus a smaller SCSI drive of almost 1 GB. Is that a USB thumb drive or jumpdrive? Or some other kind of a small drive maybe? 
Well in any case, Grub seems to find SCSI (or SATA) disk's MBRs particulary attractive. Did you install Ubuntu while you had a USB thumb drive plugged in? Is it a possibility then, Grub could be in your USB thumbdrive's MBR?

Regards, Herman

---

