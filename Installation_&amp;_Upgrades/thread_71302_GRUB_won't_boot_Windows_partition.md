---
title: "GRUB won't boot Windows partition?"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by eXcentra on 2005-10-02
This is my first time installing Linux. It took a while but I was able to install Ubuntu (using it right now). 
So I was able to install and run Ubuntu but I can't boot up Windows. GRUB loader says that it can't read that type of partition or something (I can't recall because the message flashes really quickly and goes back to the OS choosing menu). 
Here's what I did to install Ubuntu:
Defragged, partitioned using PartitionMagic
  NTFS (primary)
  ext3 (primary)
  swap (logical)
  fat32 (logical)
I installed grub on the ext3 partition rather than the MBR.

I basically followed this installation guide:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

Any idea what's up?

Edit: If I set the ext3 partition as the bootable partition I get an error message, but if I set the ntfs partition to the bootable partition, it takes me to the OS loader. 

Do you think I should reformat the ext3 partition and start all over?

---

### Post by aysiu on 2005-10-02
[QUOTE=eXcentra]
So I was able to install and run Ubuntu but I can't boot up Windows. GRUB loader says that it can't read that type of partition or something 

...

I installed grub on the ext3 partition rather than the MBR.
[/QUOTE] These two don't seem to go together. If you're getting the Grub boot loader and it's giving you a message, then you must have installed it to the MBR. Otherwise, you'd be using the Windows boot loader, not Grub.

What does your /boot/grub/menu.lst look like? Open up a terminal and type ```
 cat /boot/grub/menu.lst
``` and post the output here.

Also, post the output of ```
sudo fdisk -l
```

---

### Post by eXcentra on 2005-10-02
```
 cat /boot/grub/menu.lst
``` 
excentra@ubuntu:~$ cat /boot/grub/menu.lst
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
chainloader     +1

```
sudo fdisk -l
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           2       16033+  fe  LANstep
/dev/hda2   *           3        3826    30716280    7  HPFS/NTFS
/dev/hda3            3827        5101    10241437+  83  Linux
/dev/hda4            5102        9729    37174410    f  W95 Ext'd (LBA)
/dev/hda5            5102        5293     1542208+  82  Linux swap / Solaris
/dev/hda6            5294        9729    35632138+   b  W95 FAT32

---

### Post by aysiu on 2005-10-02
[QUOTE=eXcentra]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
chainloader     +1[/QUOTE] Well, everything looks good. The only thing I see, and I'm not sure if this is the problem, but in both the commented out example and in my /boot/grub/menu.lst, there's a line that says *makeactive* for the Windows entry.

This is what mine looks like ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

``` It's (hd0,0) instead of (hd0,1) because Windows is on my first partition. It's on your second partition, so (hd0,1) should be fine for you. Unfortunately, [the Grub manual's definition of the term *makeactive*](http://www.gnu.org/software/grub/manual/grub.html#makeactive) isn't terribly informative.

Just for the sake of covering more ground, though, can you follow these directions:

```

sudo mkdir /media/windows
sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
cat /media/windows/boot.ini
``` Then post the output of that?

P.S. Obviously, what's done is done, but that tutorial you used was terrible. It may work for that person, but it's an incredibly convoluted way to set up a dual-boot. Ideally, you would use the Ubuntu installer to resize your NTFS partition, set up a new partition, install Grub to the MBR, and be all set. Well... as I said before, what's done is done. Let's try to fix it.

---

### Post by eXcentra on 2005-10-02
```

sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
excentra@ubuntu:~$ sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
:|

```

cat /media/windows/boot.ini

```
cat: /media/windows/boot.ini: No such file or directory

---

### Post by Emerzen on 2005-10-02
Aysiu & Excentra, I've seen another post-er w/ almost the same problem.  I think there's something wrong w/ the syntax of this part of the menu.lst:
------------------------------------------------------------------------------------------------------
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
**root**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
chainloader +1
-------------------------------------------------------------------------------------------------------
I don't think the word I bolded should be there.  Anyway, here's what my .lst looks like and it work well. It looks like hd0,1 is the correct path.  I would do the following.
-------------------------------------------------------------------------------------------------------
1. Delete everthing BELOW the line w/ automagic in it at the bottom.
2. Add this, save it and reboot/try it.


title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

---

### Post by eXcentra on 2005-10-02
> 1. Delete everthing BELOW the line w/ automagic in it at the bottom.
What's automagic? Can you explain to me?

Also, where can I locate the file and how do I edit it? Please, bear with me. This is my first time.

---

### Post by aysiu on 2005-10-02
[QUOTE=Emerzen]
I don't think the word I bolded should be there.[/quote] No, that word's in my menu.lst, and my dual-boot is fine. I don't think it'd hurt to comment it out, though.

> Anyway, here's what my .lst looks like and it work well. It looks like hd0,1 is the correct path.  I would do the following.
-------------------------------------------------------------------------------------------------------
1. Delete everthing BELOW the line w/ automagic in it at the bottom.
2. Add this, save it and reboot/try it.
title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1 I think this is good advice. And I noticed yours also has *makeactive* in it.

---

### Post by aysiu on 2005-10-02
[QUOTE=eXcentra]What's automagic? Can you explain to me?[/quote] There's a certain part of the menu.lst that's auto-generated by the installer. When you do upgrades to Ubuntu, this part will be automatically changed to reflect the upgrades to the Ubuntu system. Anything below the "automagic" section won't be affected by upgrades.

It's everything between these lines ```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below
``` and this line ```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

> 
Also, where can I locate the file and how do I edit it? Please, bear with me. This is my first time. To edit the /boot/grub/menu.lst, type this in a terminal ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

---

### Post by eXcentra on 2005-10-03
Didn't work. :|

---

### Post by aysiu on 2005-10-03
[QUOTE=eXcentra]Didn't work. :|[/QUOTE] Okay. Please explain exactly what you did and exactly *what* didn't work. We're trying to help as much as we can (and we're volunteers, by the way--just other Ubuntu users), but we can't read minds.

---

### Post by aysiu on 2005-10-03
[QUOTE=eXcentra]
Edit: If I set the ext3 partition as the bootable partition I get an error message, but if I set the ntfs partition to the bootable partition, it takes me to the OS loader. 

Do you think I should reformat the ext3 partition and start all over?[/QUOTE] Honestly, if you haven't done anything to the Ubuntu install since you installed it, it may be easier to do a clean reinstall properly (do *not* follow the directions in that tutorial you originally followed) than to try to fix whatever went wrong.

Put in the Ubuntu installer CD. Press Enter. Select your language and all the "obvious" stuff. 

Then, when you're asked if you want to erase the entire hard drive or manually edit the partition tables, **manually edit the partition tables**.

Select the ext3 one (which appears to be /dev/hda3) to be formatted as ext3 and mounted as /

Then finish and commit your changes.

At a certain point, you'll get a message that looks something like [this](http://users.bigpond.net.au/hermanzone/index/i0092rp.jpg). Click **Yes** to install Grub to the MBR.

Then finish the installation and reboot, and your dual-boot should be set up properly.

---

### Post by eXcentra on 2005-10-03
Sorry.

What I did was edit the file, removing everything under Automagic, including title Other operating systems:
root
then I replaced it with 
title Windows XP
root (hd0,1)
makeactive
chainloader +1

It wasn't able to boot, so I tried putting the root line back in and it didn't boot either.

[b][COLOR="Red"]EDIT: 
This is the error message I get:
[/color][/b]
> 
    Booting 'Windows XP'
root (hd0, 1)
  Filesystem type unknown, partition type 0x7
makeactive
chainloader +1


---

### Post by Emerzen on 2005-10-03
eXcentra, this is a shot in the dark but it's worth a try.  Try changing the line

root (hd0,1) to root (hd0,0)

I'm going to look at the link you used for installing Ubuntu and try to figure out what they had you do.  Otherwise, Aysiu's advice to do a reinstall of Ubuntu as outlined above would most likely work.

---

### Post by aysiu on 2005-10-03
I would either look at some of [these threads](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22Filesystem+type+unknown%2C+partition+type+0x7%22&btnG=Google+Search) or do a clean reinstall, following the steps I outlined in my last post.

---

### Post by kingsidy on 2005-10-03
i am not absolutely sure but i think that the problem is that you installed grub in the ext3 partition instead of the mbr. you might reinstalling grub while putting it in the mbr

---

### Post by aysiu on 2005-10-03
[QUOTE=kingsidy]i am not absolutely sure but i think that the problem is that you installed grub in the ext3 partition instead of the mbr. you might reinstalling grub while putting it in the mbr[/QUOTE] Instructions for doing so are [here](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by eXcentra on 2005-10-03
Well, I just tired reinstalling Ubuntu but when it gets to the GRUB installer, it doesn't even ask if I want to install it onto the MBR or elsewhere. 
I've also tried formatting the Linux partitions and deleting them to see if Windows would boot up but the GRUB loader comes up saying "Error 22." I'm thinking that this is weird because it was supposed to be installed on ext3 which i just deleted, unless during the new installation it installed onto the MBR. 
:confused:
**[color=red]EDIT:[/color]**
So I tried replacing (hd0, 1) with (hd0, 0) and I got:
> 
Booting 'Windows XP'
root (hd0,0)
Filesystem type unkonown, partition type 0xfe
makeactive
chainloader +1
Starting Windows 98...
Type the name of the Command Interpreter (eg., C:\WINDOWS\COMMAND.COM)
A>

I also forgot to mention that GRUB loader doesn't even take me to a menu anymore. It just says to press the ESC key to go to the menu or else it'd just boot-up Ubuntu in 3 seconds.
I'm gonna try and reinstall GRUB.

Edit: Well, I reinstalled GRUB and still nothing...
asdfasdfa;lsdfja;lskdjf;laksjdf

Is there any way I can COMPLETELY uninstall GRUB and start all over with Windows and PartitionMagic and what not?

---

### Post by Emerzen on 2005-10-03
eXcentra,

You've reinstalled Ubuntu?  Can you repost your partitions w/

sudo fdisk -l

Do you want to reinstall both Windows and Ubuntu?  Before doing that, I would reinstall GRUB from a live CD.  Here's a thread w/ directions for that, [http://www.ubuntuforums.org/showthread.php?t=71560](http://www.ubuntuforums.org/showthread.php?t=71560) , but post your fdisk first.

---

### Post by eXcentra on 2005-10-03
root@ubuntu:/home/excentra # fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           2       16033+  fe  LANstep
/dev/hda2   *           3        3826    30716280    7  HPFS/NTFS
/dev/hda3            3827        5042     9767520   83  Linux
/dev/hda4            5043        9729    37648327+   5  Extended
/dev/hda5            5043        5224     1461883+  82  Linux swap / Solaris
/dev/hda6            5225        9729    36186381    b  W95 FAT32

btw, I have no idea what LANstep is but it was there when I partitioned with PartitionMagic...

---

### Post by Emerzen on 2005-10-03
eXcentra,

I was wondering about that LANstep partition myself.  My guess is it may be a utility partition installed by your PC vendor.  In any case, here's how I would proceed but, to be fair, you're having more difficulty than I've ever run into, so I'm really just trouble shooting w/ you and not an expert.  Nevertheless, a Google search for 'error 22' revealed some problem w/ the partition table on that drive.  Further googleing reveals that many people who repartition can run into this problem.  So,

 I would 1st reinstall GRUB from the Live CD rescue mode as outlined in the link I provided above (that should restore your partition table according to what I've read).  Hopefully, that will just work.  ( I think your Ubuntu reinstall didn't work, as it didn't reinstall GRUB)

If you want to find a more experienced user to run this by, I wholeheartedly recommend that!

---

### Post by eXcentra on 2005-10-04
I tried the rescue mode and came up with: 
> 
Due to a bug in sfx_freeze, the following command might produce a segmentation fault when /boo/grub is not in an XFS filesystem. This error is harmless and can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map/boot/grub/device.map
Check if this is correct or not. If any of the lines is incorrect, fix it and rerun the script 'grub-install'.

(hd0) /dev/hda

I've also tried what aysiu mentioned but they didn't work either.

I've tried using a Windows 98SE CD and using the "fdisk /mbr" command but when I booted up, I came up with "GRUB" and only GRUB. It wouldn't boot. Would I have to format and/or delete the Linux partitions and then use "fdisk /mbr"?

[color=red]**EDIT:**[/color] 
So I've tried formatting and deleting the partitions and then using "fdisk /mbr" and it didn't work. Still "GRUB". Any idea wtf is goin' on? 
At this point, I'd rather not fix the problem (although such replies would still be greatly appreciated). I want to mount my NTFS partition but it won't let me. 
I use this command:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)
and get:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
My choice is either to reformat the whole HD (which I cannot do) or make the mounting of the ntfs partition to work. 
Any ideas? 
It's late, time to sleep...

---

### Post by Humanoid on 2005-10-12
I found a solution after trying all possible ways without formatting.

1. Save your Grub to a floppy before this! (sudo grub-install /dev/fd0).

2. Boot your computer with Windows XP cd and start Recovery Console.

3. Run fixboot, fixmbr and say yes to all questions.

4. Run fixboot again. Now it shows no errors.

5. Boot your machine, Windows should start.

If you want now boot to Ubuntu, just use the floppy where you installed Grub at the start.

---

### Post by Cad-Monkey on 2005-10-12
Hey all,

I just had a problem very similar to this, while installing Gentoo on a laptop... in fact... some of you may remember me...

In any case, when I repartititione my free space using fdisk - which is a command line based partitioning scheme that probably tells you a little more while you're working than ubuntu's debian-based partitioning system does - fdisk showed me my single windows partition as two unknown type partitions, and one partition typed Novell Netware. Not knowing how IBM sets up their partition tables, I assumed it to be normal. So I wrote up a bootstrap, a swap, and a root partition. As soon as I gave the system the ok to write the partition scheme, it said there was a problem, of type 22. I still don't know what that means, but in any case, the system had overwritten a bad partition table, confusing the system even more. To get myself out of the mess of not being able to boot my XP partition at all, and not having a Linux system at all just yet, I installed ubuntu, and it did boot. Grub wouldn't load Windows XP, though, much like Excentra's computer doesn't.

The solution, in the end, was to insert a Windows XP cd, and boot into a recovery console. There, the techs from my school did a fixboot, and fixmbr, which installed a fresh partition table, with only one partition on it (NTFS), and a new Windows master boot record. It got my attention that the new partition table showed only one partition on it, not three... I asked the tech who helped me what a Novell Netware partition is used for, and he thought it was just a disk fragment that fdisk misread. I guess it happens occasionally.

Then I proceeded to install a new Linux system with my free space. This time it worked without a single hitch.

Could it be possible that Excentra's Lanstep and and ntfs partitions are really a misread partition table that got locked into a wonky state, like mine did?

Just thought I'd throw that out there. I understand from the posts, if I'm not mistaken, that you haven't tried with a Windows XP cd yet? Maybe you need to run fixmbr on an XP cd, and get a new partition table. Good luck Excentra!

---------------Cad-Monkey

---

