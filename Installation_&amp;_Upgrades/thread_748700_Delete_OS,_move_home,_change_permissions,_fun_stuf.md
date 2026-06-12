---
title: "Delete OS, move /home, change permissions, fun stuff?"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2008-04-07
OK, right now I've got Ubuntu 8.04 installed on my 30GB drive, and Ubuntu 7.04 installed on my 200GB drive. The /home directory for the 8.04 installation used to be on the big drive, but apparently when I installed 7.04, it moved the 8.04 /home to the 30GB drive. What I ultimately want to do is delete the 7.04 installation, and move the /home in 8.04 to the 200GB drive.

I'm also wondering, do I need to change the 200GB drive to be non-bootable after this? And do I need to do anything special to GRUB so that it doesn't give me the option of booting 7.04 anymore? I would rather not have to reinstall (although if that's the cleanest way to do it, so be it).

Here is my fdisk -l:
```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006bfb7

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3493    28057491   83  Linux
/dev/hda2            3494        3649     1253070    5  Extended
/dev/hda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000681c4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         121      971901   82  Linux swap / Solaris
/dev/hdc2   *         122        3751    29157975   83  Linux
/dev/hdc3            3752       23944   162200272+  83  Linux
/dev/hdc4           23945       24321     3028252+   5  Extended
/dev/hdc5           23945       24321     3028221   82  Linux swap / Solaris

```

So basically, I think I need to delete the extended partition on the 30GB drive which is the current /home, and delete the extended partition in the 200GB drive, because I did give the install a smaller partition than the whole drive itself. Am I right? How do I do it?

Thanks,
Dan

---

### Post by Pumalite on 2008-04-07
This might help:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dbsoundman on 2008-04-07
Thanks. I had seen that site before, but I wasn't sure if I had a special situation with the OS deletion and boot permission changes and such...

-Dan

---

### Post by Pumalite on 2008-04-07
You can just delete Feisty and if you have trouble with Grub; reinstall it:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(separate home will take care of it's own permissions)

---

### Post by dbsoundman on 2008-04-07
So, use gparted to delete the Feisty partition, and move /home?

-Dan

---

### Post by Pumalite on 2008-04-07
Move /home first. Then delete Feisty.

---

### Post by dbsoundman on 2008-04-07
Ok, but I'm a little confused as to **how** I delete Feisty. I thought I shouldn't just delete the files, since that would leave me an empty partition. Or should I delete the files, move /home, resize the partition?

-Dan

---

### Post by Pumalite on 2008-04-07
Sure you can delete the partition where Feisty is. That will leave you with 'free space' that you can use as you wish. Post a screen shot of Gparted.

---

### Post by dbsoundman on 2008-04-07
OK, here are my partitions as seen in GParted:
First, the 200GB drive:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=65230&stc=1&d=1207609726[/IMG]

And the 30GB drive:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=65231&stc=1&d=1207609726[/IMG]

From the looks of it, it actually looks like I got the drive partitions mixed up when I installed Feisty, and put it on the larger partition in the 200GB drive instead of the smaller one. In that case, I don't have to move my Hardy /home, which is good.

So what's the "correct" way to delete that partition and give that space over to the /home directory?

-Dan

---

### Post by Pumalite on 2008-04-07
I have problems advising you because hdc2 has a mount point of /home. It should be only / if it were Feisty.

---

### Post by dbsoundman on 2008-04-07
Well, this is the partitions from the point of view of Hardy, so I figured it would show it's known partitions only. Here's what I think is going on:
Hardy install is on hda.
Hardy /home is on the first partition  of hdc. Feisty installation and Feisty /home are on the second partition of hdc.

That's my theory, but I'm ultimately not sure what in the world I did.

-Dan

---

### Post by Pumalite on 2008-04-07
hdc3 has a mount point of /media/disk. How do you explain that? In other words, I'm not sure where Feisty is. Sorry.

---

### Post by Pumalite on 2008-04-07
One more idea. Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from. That will show the drives/partitions unmounted and maybe we'll get different results.

---

### Post by dbsoundman on 2008-04-07
I've got the liveCD, I will try that out later. I think it's mounting the rest as /media/whatever because in Hardy's eyes, it is just a partition with no particular use to it. At least in my thinking, it would make sense that the directory titles are static. It's also possible that I made myself a linux dual boot the wrong way. But it works...

-Dan

---

### Post by Pumalite on 2008-04-07
Boot Gparted Live CD and post a screen shot.

---

### Post by dbsoundman on 2008-04-07
I will do that. Maybe tomorrow, if not tonight.

Can you take actual screenshots in there? I wasn't aware of that...I figured I would just be taking a picture or something.

-Dan

---

### Post by Pumalite on 2008-04-07
There is a camera icon at the bottom for just that purpose.

---

### Post by dbsoundman on 2008-04-08
I booted GParted, and it actually told me the same thing that the other session of GParted did, except this one didn't tell me the mount points (i.e. /home, /, etc.). I am almost sure that the large partition on the 200GB drive is Feisty, because GParted shows that there is ~10GB left in the first partition of that drive, and that is how much is left in my /home in Hardy, so I'm pretty sure that's the one. I've already got everything backed up, so if something goes crazy, I'll just reinstall and reconfigure what I have to.

-Dan

---

### Post by Pumalite on 2008-04-08
Good luck.

---

### Post by dbsoundman on 2008-04-09
Deleting the partition worked fine, no problems at all, but when I boot up, I still get the option of booting the now-nonexistent OS in the grub menu. I looked at the link provided earlier to reinstall grub, but I'm not sure if this is my particular situation, because I'm not trying to restore grub so much as just get rid of the menu where I have the choice of booting 7.04 or 8.04. Do I just go through that process, or is there a different way?

Thanks,
Dan

P.S.: If I use an older LiveCD is that a problem?

---

### Post by Pumalite on 2008-04-09
Edit /boot grub/menu.lst and comment out the entries that are not pertinent anymore.

---

### Post by dbsoundman on 2008-04-10
Now I have another interesting problem: I checked out /boot/grub/menu.lst, and all the Hardy kernels are listed, but none of the Feisty ones are, but when I start up, I still have the option of booting Feisty. Did I somehow miss something?

-Dan

---

### Post by Pumalite on 2008-04-10
You mean the Grub menu includes Hardy and Feisty? If so, you missed something in menu.lst

---

### Post by dbsoundman on 2008-04-10
Here it is, maybe I did miss something:
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
# kopt=root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro

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

title		Ubuntu hardy (development branch), kernel 2.6.24-15-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-rt
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-rt root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro single
initrd		/boot/initrd.img-2.6.24-15-rt

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-rt root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-rt
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-rt root=UUID=30e8f9b8-542a-4bc8-9afc-6a85f3562a01 ro single
initrd		/boot/initrd.img-2.6.24-12-rt

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I see some interesting options in there...colors? Anyway, hopefully I'm just blind and missing the important part.

-Dan

---

### Post by Pumalite on 2008-04-10
Your menu.lst is fine. Apparently Feisty is a ghost coming out of nowhere.

---

### Post by dbsoundman on 2008-04-11
Ok, I think I just figured something out...I searched my filesystem for files named menu.lst, and got 10 hits total. Here they are:
/boot/grub
/home/boot/grub
/home/usr/share/doc/grub/examples
/home/usr/share/doc/memtest86+/examples (file called grub-menu.lst)
/home/usr/share/ubuntu-docs/ubuntu/sample (3 from this directory, files called grub-menu.lst_*, the star representing various appendages to the title)
/usr/share/doc/grub/examples (this one is actually a menu.lst)
/usr/share/doc/memtest86+/examples (grub-menu.lst)
/var/lib/ucf/cache (:var:run:grub:menu.lst)

I'm thinking that at least one of those is the problem.

In fact, the one in the /home directory (/home/boot/grub) lists the feisty install as well as hardy. What's also interesting is that I accidentally let it boot into Feisty today, and I actually got the Feisty login screen. When I tried to login I couldn't, but just getting the login screen makes me wonder if some of the Feisty files got moved to my Hardy /home partition for some reason.

So, does anyone know what files should be removed/modified here? I have no idea why it got this way but it is rather strange.

Thanks,
Dan

---

### Post by Pumalite on 2008-04-11
I guess you'll have to check them one by one. Any menu.lst, that contains Feisty, delete it (not the one in /boot/grub with Hardy in it). There must be a better answer, but I don't have it.

---

### Post by dbsoundman on 2008-04-11
Ok, one other thing. Should my /home directory contain all these things?
```
dan@blackdiamond:~$ dir /home/ -l
total 140
drwxr-xr-x   2 root root  4096 2008-04-05 23:46 bin
drwxr-xr-x   3 root root  4096 2008-04-05 16:46 boot
lrwxrwxrwx   1 root root    11 2008-04-05 16:07 cdrom -> media/cdrom
drwxr-xr-x  53 dan  dan   4096 2008-04-11 17:33 dan
drwxr-xr-x  12 root root 40960 2008-04-05 16:47 dev
drwxr-xr-x 124 root root 12288 2008-04-11 16:29 etc
drwxr-xr-x   2 root root  4096 2008-04-05 16:07 home
drwxr-xr-x   2 root root  4096 2008-04-05 16:09 initrd
lrwxrwxrwx   1 root root    37 2008-04-05 16:29 initrd.img -> /boot/initrd.img-2.6.20-15-lowlatency
lrwxrwxrwx   1 root root    33 2008-04-05 16:11 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  17 root root  4096 2008-04-05 17:30 lib
drwx------   2 root root 16384 2008-04-04 20:31 lost+found
drwxr-xr-x   4 root root  4096 2008-04-11 16:28 media
drwxr-xr-x   2 root root  4096 2007-04-12 05:11 mnt
drwxr-xr-x   2 root root  4096 2008-04-05 16:09 opt
drwxr-xr-x   2 root root  4096 2007-04-12 05:11 proc
drwxr-xr-x   9 root root  4096 2008-04-06 17:11 root
drwxr-xr-x   2 root root  4096 2008-04-05 17:31 sbin
drwxr-xr-x   2 root root  4096 2008-04-05 16:09 srv
drwxr-xr-x   2 root root  4096 2007-04-04 06:47 sys
drwxrwxrwt   6 root root  4096 2008-04-11 16:29 tmp
drwxr-xr-x  12 root root  4096 2008-04-05 23:37 usr
drwxr-xr-x  14 root root  4096 2008-04-05 16:27 var
lrwxrwxrwx   1 root root    33 2008-04-05 16:29 vmlinuz -> boot/vmlinuz-2.6.20-15-lowlatency
lrwxrwxrwx   1 root root    30 2008-04-05 16:11 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic
-rw-r--r--   1 root root  1338 2008-04-04 22:50 xorg.conf.copy

```

I'm thinking a lot of that is leftover feisty stuff, am I right? if so, I will delete it, but obviously I don't want to delete stuff I need. This stuff, by the way is in /home, NOT /home/dan.

-Dan

---

### Post by Pumalite on 2008-04-11
It looks like you have an entire filesystem inside of your /home. They don't belong there.

---

### Post by dbsoundman on 2008-04-11
Heh...that's what I was suspecting...just so I'm sure, what of those do I want to keep? Basically is there anything other than /dan that I want to keep in my home folder?

-Dan

---

### Post by Pumalite on 2008-04-11
Make sure you have Hardy intact hanging from '/', then delete all except Hidden Files (just in case) and save 'dan' too.

---

### Post by dbsoundman on 2008-04-12
Well, I have to start over now.

Apparently, somehow Hardy wasn't hanging intact from '/', and so when I deleted those folders, suddenly everything on my taskbars and desktop disappeared, windows wouldn't open, etc. I panicked, rebooted, and found that I got grub error 15, meaning grub was gone.

So now, I'm attempting to reinstall. I basically have to format my install drive and start over, and hope that some of the files on my /home are still there, though I may format that too, since it was such a mess too.

So, basically, THIS IS A VERY BAD IDEA. Apparently there are important things in the home folder that should stay there. I just have to hope I can get things back to where they were before...

-Dan

---

### Post by Pumalite on 2008-04-12
Sorry to hear that. Good luck.

---

