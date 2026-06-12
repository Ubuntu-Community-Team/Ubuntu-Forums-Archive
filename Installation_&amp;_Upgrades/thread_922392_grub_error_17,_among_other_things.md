---
title: "grub error 17, among other things"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by wriggary on 2008-09-17
Hi, new Ubuntu user here.

Having some problems getting my ubuntu 8.04.1 to boot. (betcha it isn't the first time you've heard that!)

Now, its not that I'm not technically adept.  I've stumbled my way around a few live distros, had some fun. (dsl and slax) I thought I was ready for the big time:  Dual Booting into a installed distro.  And, of course, I had to take the hard way about it.

Due to space concerns (physical, i have another computer but there is no room to hook it up... small apartment), and some important (and expensive) educational software of my spouse's, Vista isn't leaving sda (150 gb SATA) anytime soon.  nor is the bootloader. 

But i thought "Hey, it's okay.  My (erm... her) $299 wal-mart special (Compaq- Built early '07) allows me to select a boot device at startup, so i'll just install the bootloader on the second hard drve, and select the device to boot ubuntu from whenever I want to load Ubuntu.

So, after a thorough defrag of my media storage drive (150G PATA), I used the included partitioning tool on the install cd to shrink the ntfs partition roughly 11 gb, set up a (initally ext3, now reiserfs hoping that would change something) 10gb root partition and a 1024 mb linux swap area.  On the last step of the install under the advanced options, I changed the bootloader location away from (hd0) to sdb, the MBR of the media disk.  The install finished with no complaints, and kindly asked me to remove the Ubuntu CD from the tray.  I obliged, and pressed enter to restart the computer.

A few seconds later, ESC to select the boot device... selected the WD internal drive...

Grub loading stage 1.5

Grub error 17.

mmmkay.

Now, I understand why this is happening, I think anyway.  When I select the WD media drive in the bios, It fools the computer into thinking that the second HD was actually installed first, making it sda or (hd0).  So, when the root= argument gets passed to grub, its looking on the SATA drive (vista) for a kernel image to boot.  and it can't make sense of the filesystem.  Hence error 17.

Now, I guess where i'm getting stuck is not knowing how to flog grub in just the right way.  I get no option for command line grub, not even the grub gui. just error 17.  So, how to do I go about updating and installing grub (maybe it would look better with the hyphens), and essentially telling it that "hey, this is where I want you to install the bootloader, but you're going to think its on the other hard drive when I reboot.  This is where it really is."  Any help or hand-holding would be appreciated.

Now, I know you're going to need some info from me.  Be right back, have to boot the livecd and get it.

---

### Post by wriggary on 2008-09-17
```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18705   150247881    7  HPFS/NTFS
/dev/sda3           18706       19457     6040440    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a9c9276

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18183   146047996    7  HPFS/NTFS
/dev/sdb2   *       18184       19332     9229342+  83  Linux
/dev/sdb3           19333       19457     1004062+  82  Linux swap / Solaris


```

hmm, for some reason it didn't mount sdb... be right back

---

### Post by wriggary on 2008-09-17
Back again.  Sorry, fingerprint on the disk.

```
ubuntu@ubuntu:/media/disk/boot/grub$ cat device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

```
ubuntu@ubuntu:/media/disk/boot/grub$ cat menu.lst
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
# kopt=root=UUID=0ba0ee31-a500-4d03-89e2-edcc812fce28 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ba0ee31-a500-4d03-89e2-edcc812fce28 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ba0ee31-a500-4d03-89e2-edcc812fce28 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


```

Now, I think I have to change the root= argument on the Ubuntu kernel entries to read (hd0,1) and delete the Vista entries, then reinstall grub, but how does one do this from the livecd environment?

---

### Post by caljohnsmith on 2008-09-17
Based on the menu.lst you posted, it looks like Grub actually got installed to your Vista HDD. So to first to get Grub working, boot your Live CD and try this:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will install Grub to the master boot record (MBR) of your Ubuntu HDD. Make sure it is the first in your BIOS boot order, and then reboot. If that works and you get a Grub menu, you can change your Ubuntu entries to use (hd0,1) instead of (hd1,1), and that will probably be all it takes to boot Ubuntu. Let me know how it goes.

---

### Post by wriggary on 2008-09-17
```
grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd1)"...  19 sectors are embedded
.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+19 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```


Rebooting.

---

### Post by wriggary on 2008-09-17
Well, still getting grub stage 1.5 error 17 before the grub gui ever loads. 

hmm.  let me try actually changing the boot device order, instead of just pressing esc to pick the boot device during bios start

---

### Post by caljohnsmith on 2008-09-17
Wriggary, I think I see what your problem might be: your Ubuntu install begins at about 150 GB point on your 160 GB HDD, and some older BIOSes can't "see" anything beyond 137 GB on start up. That could explain your Grub error 17, because Grub wouldn't be able to access its files if they are beyond the reach of the BIOS.

I would recommend moving the beginning of the NTFS partition on that disk by about 10-20 MB, then creating a small ~10 MB partition with that free space and using that as a dedicated Grub partition. If you want to try having a dedicated Grub partition, it is not hard to do once you make the small partition at the beginning of your HDD. I think there's a strong possibility that will solve your problem, as I've seen this exact problem before.

---

### Post by wriggary on 2008-09-17
Okay.  

Now, how would be the easiest way to set this up, given my idiocy when it comes to grub?

In the Ubuntu installer, if I were to create this partition and select that first 20mb partition and set its mount point as /boot, would it do what we need it to do?  No need to worry about lost data, I've never been able to boot that partition.

Or, would it be easier to do it from the live disk's grub term?  of course other settings would have to be changed, i belive.

I'll give it a stab after work tonight.  

Funny, I never thought of my BIOS being "older" but thats what you get for $299 :)

---

### Post by caljohnsmith on 2008-09-17
> **wriggary said:**
> Okay.  

Now, how would be the easiest way to set this up, given my idiocy when it comes to grub?

In the Ubuntu installer, if I were to create this partition and select that first 20mb partition and set its mount point as /boot, would it do what we need it to do?  No need to worry about lost data, I've never been able to boot that partition.

Or, would it be easier to do it from the live disk's grub term?  of course other settings would have to be changed, i belive.
First make sure you have your data on you sdb1 partition backed up if possible. Next, boot your Ubuntu Live CD, and open the partition editor:
```
gksudo gparted
```
Be sure to select your sdb disk in the drop-down list in the upper-right corner. The important thing to remember with gparted is that it doesn't actually do anything until you hit "apply", so that is your insurance against mistakes. Then just shrink your NTFS sdb1 partition by about 10-20 MB at the beginning, create a new primary partition there, and format it to be ext3. That should be it takes to create the partition. Let me know how it goes.

---

### Post by wriggary on 2008-09-19
Sorry for the long wait between replies.  GParted took a little over four hours to finish, at I needed at least a little sleep between my shifts.  Once I got off work yesterday morning I ran the installer again, mounting the 20mb partition as /boot, and restarted after the install finished.

Grub error 27?   either way, great news, because stage two actually loaded. In the grub gui, I edited the root (1,3) arg to read root (0,3) and it loaded just fine.  

Now, how to I update the grub installed on the mbr to read root (0,3) all the time?  my confidence is shot :(

On a separate note, I had read about the BIOS read limit on a few pages, but somewhere someone had tossed out a figure for "older BIOS'" being older than 1998 or so, and I figured that wouldn't be a problem, since my computer has SATA support in the bios.  Either way, thanks much for the help!

---

### Post by Bucky Ball on 2008-09-19
Open terminal and paste:

**sudo nano /boot/grub/menu.lst**

This is probably not the same as yours, but note where I have changed it (in bold) ...

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze Vista - Longhorn (loader)
root            **(hd0,3)**
savedefault
makeactive
chainloader     +1
```

Change the bold section to whatever is required.

---

### Post by caljohnsmith on 2008-09-19
> **wriggary said:**
> Sorry for the long wait between replies.  GParted took a little over four hours to finish, at I needed at least a little sleep between my shifts.  Once I got off work yesterday morning I ran the installer again, mounting the 20mb partition as /boot, and restarted after the install finished.

Grub error 27?   either way, great news, because stage two actually loaded. In the grub gui, I edited the root (1,3) arg to read root (0,3) and it loaded just fine.  

Now, how to I update the grub installed on the mbr to read root (0,3) all the time?  my confidence is shot :(

On a separate note, I had read about the BIOS read limit on a few pages, but somewhere someone had tossed out a figure for "older BIOS'" being older than 1998 or so, and I figured that wouldn't be a problem, since my computer has SATA support in the bios.  Either way, thanks much for the help!
That's great news you now have your Grub menu on start up, and that you were able to temporarily edit it to boot into Ubuntu. All you need to do now, like you asked, is make the change permanent. Just open a terminal when you are in Ubuntu (Applications > Accessories > Terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
Just change all the (hd1,3) references to (hd0,3) for the entries that you manually changed on start up. Save, and your done. :)

P.S. I don't know why you feel your confidence is shot, because you did a great job of getting it working. :)

EDIT: Sorry, didn't see your post first, Bucky Ball.

---

### Post by Bucky Ball on 2008-09-19
[quote=caljohnsmith]p.s. I don't know why you feel your confidence is shot, because you did a great job of getting it working. :smile:[/quote]

+1

---

### Post by wriggary on 2008-09-20
Oh yeah, for some reason I thought this needed to be loaded into the boot sector.  but thats what e2fs_stage_1_5 does, doesn't it.  makes the filesystem readable during boot :)

Thanks a bunch guys.  Left the computer to download a whole bunch of updates while I slept, and guess who I found messing around with the desktop cube when I got up?  ol' wifey don't-mess-with-my-vista.  I think shes having a little too much fun.

---

