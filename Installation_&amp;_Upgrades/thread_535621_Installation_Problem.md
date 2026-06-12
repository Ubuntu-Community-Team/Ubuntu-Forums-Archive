---
title: "Installation Problem"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by 38Super on 2007-08-26
Hi,
I'm brand new to Linux - found the Ubuntu site and decided to give it a try.

My machine is an Athlon XP2500 with 512Mb ram and two hard drives.  My primary HD (the drive with my WinXP operating system) is a 36Gb SCSI drive with about 26Gb of free space.  My secondary (data) drive is an 80Gb IDE drive with 33Gb of free space.

Ubunto loads and runs fine from the live CD (Ubuntu 7.04 i386).  When I go to install, I get to the partition page and the "Guided" (top) selection wants to set up a partition on my secondary drive, not on the bootable drive with my windows operating system.  I'm guessing I will have to use the "Manual" setup and install to my primary HD, but have no idea how to proceed.  The "all is lost" message is a real attention getter when you're messing with HD partitions for the first time.

Any advice will be greatly appreciated.

Cal
Windham, ME

---

### Post by Pumalite on 2007-08-26
If you have XP; defrag several times, erase all temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and 'shrink' the XP partition. Then you can create 500 MB to 1 GB for /swap; 10 GB for '/'; and the rest for home. Then install. (after you shrink, format the new partition ext3, even if it's not necessary )

---

### Post by 38Super on 2007-08-26
I follow you only as far as defrag and erase temp files.  The rest of the partitioning process is WAY beyond my experience level.

If I were to disable my secondary HD, would the canned Ubuntu installation procedure deal with it from there?

Thanks

---

### Post by maybeway36 on 2007-08-26
I think if you put it on your secondary hard drive, it will edit the primary hard drive's boot loader to point to Ubuntu's boot menu (with a choice between Linux and Windows.) If you do install it on the spare drive and it doesn't boot, at least you can still use Windows.

---

### Post by merlinus on 2007-08-26
If you are willing to put in the time to learn, here is a good place to start:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

### Post by Pumalite on 2007-08-26
Here is another:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/](http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/)

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

---

### Post by 38Super on 2007-08-26
Thanks for all the information.  I'll do some more research and decide on a plan.  I'll let you know how it works.

---

### Post by 38Super on 2007-08-28
OK - after reading a number of threads regarding installation and dual boot systems I came to a couple of conclusions.  Ubuntu should work fine if installed to the slave drive.  The dual boot selection will be controlled by GRUB (?) and point to the new installation.  The "Guided" installation will set an appropriate partition size and an appropriate swap file size.

I went ahead with the "Guided" installation.  Everything seemed to work fine.  Upon completion I was given the choice to leave the CD in place and continue with the "Live CD" session or remove it and use the installed platform.

I removed the CD and restarted the machine - there was no dual boot selection offered - WinXP started as always.  I inserted my live CD and rebooted to run Ubuntu.  From within Ubuntu I can see my new disk (approx 17.8 Gb) and my swap file (something like 800Mb?).  Within the new disk I can see various Ubunto directories - Grub, root, etc.  I'm doiing this from memory as I'm not at that machine.

I'm thinking that the installation was basically successful and that now I have to somehow point to the dual boot manager.  Where do I go from here?

Thanks

---

### Post by Pumalite on 2007-08-28
Re-install Grub with this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by 38Super on 2007-08-28
Per your suggestion , I opened the Terminal and ran through the GRUB installation as follows -

sudo grub
grub> find boot/grub/stage1
  (hd0,1)
grub> root (hd0,1)
grub> setup (hd0)
  Checking if "/boot/grub/stage1" exists . . . yes
  Checking if "/boot/grub/stage2" exists . . . yes 
  Checking if "/boot/grub/e2fs_stage1_5" exists . . . yes
  Running "embed /boot/grub/e2fs_stage1_5 (hd0) . . . 17 sectors are embedded
  Succeeded
  Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2            
    /boot/grub/menu.lst . . . succeeded
  Done.
grub> quit
ubuntu@ubuntu:~$ sudo grub
probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

At this point I waited about 10 minutes for some sort of verification that the "probing devices" process was completed.  After 10 minutes, there was no response and I shut down and re-booted.

WinXP . . . again/still.  No indication of a dual-boot process.

Should I have waited longer - until some sort of confirmation appeared?  If not, what's next.

Ubuntu is kicking my A$$!

Thanks for the help.

---

### Post by Pumalite on 2007-08-28
Did you use the Live CD with this thread: [http://ubuntuforums.org/showthread.php?t=224351?](http://ubuntuforums.org/showthread.php?t=224351?)

---

### Post by 38Super on 2007-08-28
Yes - I was running on the live CD.

---

### Post by Pumalite on 2007-08-28
Post: cat /boot/grub/menu.lst
blkid
sudo fdisk -l (small L)

---

### Post by 38Super on 2007-08-28
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-08-28
You will have to manually mount your ubuntu partition in order to post /boot/grub/menu.lst.

If you need instructions, post back, but the other two commands from Pumalite should work, and will be needed.

-merlin

---

### Post by 38Super on 2007-08-28
I don't know what you mean by "manually mount"

---

### Post by merlinus on 2007-08-28
That's ok, but results of the other two commands are needed (sudo fdisk -l and blkid}.

-merlin

---

### Post by 38Super on 2007-08-28
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7644    61400398+   7  HPFS/NTFS
/dev/hdd2   *        7645        9861    17808052+  83  Linux
/dev/hdd3            9862        9964      827347+   5  Extended
/dev/hdd5            9862        9964      827316   82  Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2007-08-28
What do you think Merlin?

---

### Post by merlinus on 2007-08-28
Boot from the live cd and manually mount your ubuntu partition.

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdd2 /media/ubuntu

```

Then post results of:

```

cat /media/ubuntu/boot/grub/menu.lst

```

-merlin

---

### Post by 38Super on 2007-08-28
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdd2 /media/ubuntu
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=cb62548e-2bd9-46f7-a951-d56fc086b0f3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cb62548e-2bd9-46f7-a951-d56fc086b0f3 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cb62548e-2bd9-46f7-a951-d56fc086b0f3 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-08-28
From what I can see in /boot/grub/menu.lst, ubuntu is on your first hard disk (hd0,1) and xp on the second (hd1,0).  But if I read correctly, they are reversed in your boot order, no?

Perhaps that is at least part of the problem.

You also might change root to rootnoverify in your xp stanza.

-merlin

---

### Post by 38Super on 2007-08-28
As you no doubt have figured out, I use a computer but know very little about what makes 'em work.  When you start talking about the boot order and xp stanza, you're WAY over my head.

---

### Post by merlinus on 2007-08-28
Look in your BIOS to see the boot order of your hard disks, and try changing it so hdd is before sda.

You can edit the file this way.  Open a terminal, and enter this:

```

sudo cp /media/ubuntu/boot/grub/menu.lst  /media/ubuntu/boot/grub/menu.lst_old
gksudo gedit /media/ubuntu/boot/grub/menu.lst

```

Look for these lines near the bottom:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

And change root to rootnoverify.

Save the file, remove the live cd, and restart.

-merlin

---

### Post by 38Super on 2007-08-28
ubuntu@ubuntu:~$ sudo cp /media/ubuntu/boot/grub/menu.lst  /media/ubuntu/boot/grub/menu.lst_old
cp: cannot stat `/media/ubuntu/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-08-28
Have you done anything since manually mounting ubuntu?

-merlin

---

### Post by 38Super on 2007-08-28
No - just the BIOS change and restarted from the live CD.

---

### Post by merlinus on 2007-08-28
Yep, thought so,  Follow the steps to manually mount ubuntu from my earlier post, and then edit /media/ubuntu/boot/grub/menu.lst as indicated in a more recent post.

Then post output of:

```

cat /media/ubuntu/boot/grub/device.map

```

-merlin

---

### Post by 38Super on 2007-08-28
Do I edit by enterint "edit" and the file name at the prompt?

ubuntu@ubuntu:~$ edit /media/ubuntu/boot/grub/menu.lst
Warning: unknown mime-type for "/media/ubuntu/boot/grub/menu.lst" -- using "application/*"
Error: no write permission for file "/media/ubuntu/boot/grub/menu.lst"
ubuntu@ubuntu:~$

---

### Post by merlinus on 2007-08-28
Read edited last part of my last post about posting device.map before restarting.

```

gksudo gedit /media/ubuntu/boot/grub/menu.lst

```

will allow you to edit that file.

-merlin

---

### Post by 38Super on 2007-08-28
That opens a "gedit" window with a tab that says "menu.lst", but nothing on the page.

---

### Post by merlinus on 2007-08-28
Did you mount your ubuntu partition before trying this?

-merlin

---

### Post by 38Super on 2007-08-28
Yes (?) - by entering

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdd2 /media/ubuntu

---

### Post by merlinus on 2007-08-28
Well, menu.lst is in there, because you were able to post it awhile ago.

So try again, please, and this time copy-and-paste into the terminal window using Shift-Insert.

```

gksudo gedit /media/ubuntu/boot/grub/menu.lst

```Also, if you did not get an error that /media/ubuntu already existed when last using the mkdir command, I suspect there are other problems.

But let's try this first.  And be sure to also post 
```

cat /media/ubuntu/boot/grub/device.map

```
-merlin

---

### Post by 38Super on 2007-08-28
That time it worked fine - must have been a typo?

ubuntu@ubuntu:~$ gksudo gedit /media/ubuntu/boot/grub/menu.lst
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/device.map
(hd0)   /dev/hdd
(hd1)   /dev/sda
ubuntu@ubuntu:~$

---

### Post by 38Super on 2007-08-28
Should I try to reboot now?

---

### Post by merlinus on 2007-08-28
Yeah, give it a go.  device.map seems correct.

Let's hope for the best....

-merlin

---

### Post by 38Super on 2007-08-28
Merlin -

It looks like this round is going to have to go to the penguin.  Rebooted into WinXP.

You've been juggling multiple threads all night - I'll give you a break and sign off for now.  Thanks for all your time - I'll be back tomorrow evening.

Take care,
Cal

---

### Post by merlinus on 2007-08-28
BTW, what is on the NTFS hdd1 partition, and what is on the NTFS partition on sda1?

This also may be causing confusion.

-merlin

---

### Post by 38Super on 2007-08-29
How do I tell what is on the various partitions?

---

### Post by Pumalite on 2007-08-29
They are all Windows format. You must know since you made them and filled them up. We are trying to determine where is the 'bootable' Windows. I'm sure one is the system and the other is Data.

---

### Post by 38Super on 2007-08-29
Drive C: is my primary drive - one big partition with WinXP installed and all or most of my programs.

Drive D: was also a single partition and was used for data and a couple of games.  The Ubuntu installer formed a 17-18Gb partition on this drive for the Ubuntu system files.

Does that answer your question or do you need more technical details?

Cal

---

### Post by nne2 on 2007-08-29
hi-brand new to ubuntu.  i have downloaded ubuntu to desktop and there it sits.  i am unable to open it-winxp keeps asking what i want to use to open this iso file.  adobe and firefox do not work.
any help appreciated.  ed.

---

### Post by merlinus on 2007-08-29
@nne2:

First of all, start a new thread and do not hijack this one.

Having said that, you need to burn the .iso file to a cd as a disk image, not a data disk, at no more than 4x and then boot your computer from it.

-merlin

---

### Post by 38Super on 2007-08-29
Burn the downloaded .iso(?) file to a CD, change your system BIOS boot sequence to look at the CD drive first, and reboot your machine with the CD in the drive.  This will get you into a "Live CD" session.  There are software routines available that will check the CD to make sure it's error-free.

If you have problems, post a new thread.  There are some very talented people on this site who will get you through the installation - I'M NOT ONE OF THEM :)

Cal

---

### Post by 38Super on 2007-09-01
I think I'm getting closer -

I downloaded the SuperGRUB file and burned the CD.  I booted with this CD in the drive and booted to the SuperGRUB screens.  I ran through a few options including fixing or re-installing 
GRUB, and fixing the Ubuntu boot selection (I don't remember exactly what the wording was).

Now I can boot from the SuperGRUB CD, select the Ubuntu operating system, remove the CD, and run along fine in Ubuntu.

Tell me I'm close to having the dual boot system sorted out.

Cal

---

### Post by merlinus on 2007-09-01
Good, but can you boot normally and get to the grub menu?

If not, use supergrub to reinstall grub, not just to boot ubuntu.

-merlin

---

### Post by 38Super on 2007-09-01
I just tried again - used the SG CD to re-install GRUB - and I still boot to good ol' WinXP.

As part of the SG disc routine, I come to what must be similar to the dual boot selection window.    I can select Ubuntu and boot to Ubuntu or I can select WinXP and boot to WinXP.

The SG disc presents several screens before I get the option to start Ubuntu.  A language selection screen, a few screens of text, a couple of screens that require me to select the (hd0,1) HD region, and finally the screen that allows me the selection of an OS.

I can run through the procedure again, if the exact sequence would give you any better idea of the process.  At the moment I'm downloading some 119 program updates to Ubuntu through the Update Manager and will wait to try something new until that is finished.

Any ideas?

Cal

---

### Post by merlinus on 2007-09-01
[LIST=1]
[*]boot SGD
[*]English Super [COLOR=#000000]Grub[/COLOR] Disk
[*]Gnu/Linux
[*]Fix Boot of Gnu/Linux ([COLOR=#000000]GRUB[/COLOR])
[*]select your Linux partition
[*]see message, 'SGD has succeeded'
[*]you're done! reboot[/LIST]-merlin

---

### Post by 38Super on 2007-09-01
That's what I did -

Boot from the SG disk
First screen - quick flash - Super Grub Disk
Then -
English Super Grub disk - select
Several text screens
GNU/Linux - select
Text screen
Fix boot of GNU/Linux (GRUB)
    SGD has succeeded!
Auto GRUB install
    SCD has succeeded!

Reboots to WinXP.

Cal

---

### Post by merlinus on 2007-09-01
Post results of

```

sudo fdisk -l

```

-merlin

---

### Post by 38Super on 2007-09-01
cal@SilverAMD:~$ sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7644    61400398+   7  HPFS/NTFS
/dev/hdd2   *        7645        9861    17808052+  83  Linux
/dev/hdd3            9862        9964      827347+   5  Extended
/dev/hdd5            9862        9964      827316   82  Linux swap / Solaris
cal@SilverAMD:~$

---

### Post by merlinus on 2007-09-01
Yeah, by now I had kinda figured you must have two hdds.  So grub is not being installed to the correct hdd and/or partition.

This may help:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

-merlin

---

