---
title: "GRUB Error 21"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by acorn22 on 2006-06-10
I installed Dapper from the alternate disk (low memory machine) and When I try to start, It gives me this.

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21
_
```

This box onyly has one hdd with ubuntu installed. I tried changing the little thing on the back to make it slave and master. neither worked. 

The Ribbon connecting the HDD to my computer has two plugs (one at the end...) I have tried both positions with both slave and master.

I read all the other suggestions, but couldn't really understand them becasue they had to do with 2 drives, one windows. Or they confused the hell out of my with too much code that I don't understand ;)

I do have several rescue cd's and live cd's handy, also. (and a,ll 3 versions of dapper, desktop, server, alt) so whatever I need to do i might have the resources. (but no internet)

thx

---

### Post by yager on 2006-06-10
What is the contents of your /boot/grub/menu.lst file show as the choices for your hard drives? The important parts of my menu are as follows.

```
title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot
```

My understanding is that GRUB must always boots from the (hd0,0) drive regardless of the physical address or location of the drive.  

As an example, the actual physical drive where I have GRUB is the third hard drive in my system.  When I want to play with Linux, I reboot my system, reconfigure the BIOS to look at the third drive first for boot order and I am in.  Works like a charm every time.  When I want to go back to Windows for the wife, I reboot, and change the boot order of the drives.

---

### Post by acorn22 on 2006-06-10
I don't know how to get to that file, since ubuntu is not booting. Can I see it from a livecd? 

I played around with the bios and the different places to plug my hdd into the mobo and which part of the ribbon ect.. and now it loads. But my new problem is it gets stuck at ```
Uncompressing Linux.... Ok, booting the kernal.
``` From here I can see the following:

```
Booting 'Ubuntu, Kernal 2.6.12-36-386'

root (hd0,0 )
filesystem type is ext2fs, partition type 0x83
kernal /boot/vmlinuz-2.6.15-23-386 root=/dex/hdc1 ro quiet
[linux-initrd @ 0x3a03000, 0x5e1529 bytes]
savedefult
boot
incompressing linux... ok, booting the kernal
```

At this point I get the flashing _ and I can type stuff (no efect)


Also, At grub, I can hit esc and see 3 options, mem test, ubuntu, ubuntu safe. (only ubuntu gets stuck)

---

### Post by acorn22 on 2006-06-10
UPDATE:

As I hit enter a new mesage came up:

```
ALERT! /dev/hdc1 does not exist. Dropping into a shell!

BustBox v1/01 (debian 1:1.01-4ubuntu3) Buitl-in shell (ash)
enter 'help' for a list of commands.

/bin/sh: cant access tty; job comtrol turned off
#
#
```

ok

---

### Post by az on 2006-06-10
Grub 21 means that grub was told where your kernel is (the actual file on the hard drive) but the information the is being given to it by the bios is wrong.

Some bioses are buggy, and some are just unable to see the whole hard drive.   You probably changed a setting in your bios that made it more able to see your hard drive, but you may have changed the order of some devices  - now ubuntu can't find itself (it thinks it's on hdc, but it seems to really be hda...)

Keep the current settings and try reinstalling.  Ubuntu will reinstall using the correct device order, this time.  Since you have nothing else on the drive and this is  afresh install, I think that will just be simpler.

---

### Post by acorn22 on 2006-06-10
[QUOTE=azz]
Keep the current settings and try reinstalling.  Ubuntu will reinstall using the correct device order, this time.  Since you have nothing else on the drive and this is  afresh install, I think that will just be simpler.[/QUOTE]

Sure thing. I'll try that right away.

---

### Post by NoWhereMan on 2006-06-10
You may also want to look here:
[http://ubuntuforums.org/showthread.php?t=155684&highlight=grub#9](http://ubuntuforums.org/showthread.php?t=155684&highlight=grub#9)

bye :)

---

### Post by yager on 2006-06-10
[QUOTE=acorn22]I don't know how to get to that file, since ubuntu is not booting. Can I see it from a livecd? 
[/QUOTE]

As I can see from the other responses, you should be on your way to a clean install.

Just in case this does not work, ie Ubuntu does not set GRUB up correctly again, here is what you can do to check what is up.

When GRUB boots to the menu, highlight the safe mode that apparently worked the first time and press "e" for edit. This brings up the menu.lst file entries. 
Check the contents of the kernel line and verify what root= is set to.  Write this down.  
[INDENT]Last time you had /dev/hdc1 for the bad ubuntu line.  This should be something like /dev/hda1 or /dev/sda1 depending on the type of hard drive controller you have.[/INDENT]

Now press the <ESC> key to return to the menu.

Highlight the Ubuntu boot choice and again press "e"
[INDENT]Verify that root (hd0,0) is set.
Next verify that kernel xxxxxxx root=/dev/hda1 is correct.  If not, change this to the proper choice which in your case is most likely hda1.[/INDENT]
Now hit the "b" to boot your newly modified entry.

To fix this long term type the following into a terminal window once you are in Ubuntu.
```
sudo gedit /boot/grub/menu.lst
```
Scroll down and find the error and correct it.  Save the file and you will be good to go from now on.

Hopefully this will all not be necessary but it is always a great idea to have a back up plan.

Let us know how the fresh install works out.

---

### Post by acorn22 on 2006-06-10
Alright, All installed but now it is asking for username and pass (not graphical at all) and I ented them, and they are wrong

arg

---

### Post by yager on 2006-06-10
[QUOTE=acorn22]Alright, All installed but now it is asking for username and pass (not graphical at all) and I ented them, and they are wrong

arg[/QUOTE]

Step 1.  Check outside your window.  Do you see a black cloud following you?  If so, there is no hope for you.;) 

During the install process, it asked you to provide a user name and password.  They are case sensitive so I will ask the obvious first, did you enter your user name with the same capitalization as you provided during the install?  If this still does not get you in, then I hate to say this, but start with a fresh install again since the number of problems you have will take longer to resolve than the time to install again from scratch.

In the case of the graphics, make sure that during the fresh install you set your graphics resolution correctly on the choices given.  If your monitor is not recognized, the distro will default to 1024x768 or some other common denominator resolution that your graphics card is capable of delivering.

If you get past the password problem, type in startx and report back whatever error message you have.  You may want to start a fresh thread for that since your problem is no longer related to GRUB.

---

### Post by acorn22 on 2006-06-10
here we are [http://ubuntuforums.org/showthread.php?p=1122588#post1122588](http://ubuntuforums.org/showthread.php?p=1122588#post1122588)

---

### Post by theanswriz42 on 2006-06-10
I'm having a similar issue. 

I'm trying to get a system up I installed for my roommate. This system is 2 harddrives,  one primary and the other is slave. Windows is on the first harddrive (/dev/hda) and ubuntu is on the second (/dev/hdb). When I boot, I get the Grub Error 21 which is to say that grub doesn't know where to look to find my bootable syatem (as far as i know). 

My menu.lst (got from kanotix) is as follows:

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
default		3

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
# kopt=root=/dev/hdb1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

This looks correct to me so I'm not sure if the problem lies outside of grub. Just to be certain, I re-installed ubuntu and got the same error. Anyone have any suggestions?

Also, when I changed the bios to say: Primary Drive 1: automatic, it sees the drive and identifies it correctly but then I get a grub error 25. Needless to say, I'm a bit confused

---

### Post by acorn22 on 2006-06-10
I had to swap which plugs my hdd was plugged into with my cd drive. idk, worked for me 8-[

---

### Post by yager on 2006-06-10
[QUOTE=theanswriz42]
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

```
[/QUOTE]

You need to change root to (hd0,0).  Grub always boots from this device.  The kernel line is pointing to the correct place.

Step by step directions:
1.  Restart your computer.
2.  At the grub menu highlight the Ubuntu line and press "e".
3.  Highlight the root line and correct the line to read "root  (hd0,0)
4.  Press the "b" key.

At this point, Ubuntu should be starting up with no issue.

To permanently fix this, you need to edit your menu.lst file.  Execute the following command.

```
sud gedit /boot/grub/menu.lst
```

Scroll down to the error in the file and correct.  This will fix this for good.  Be aware that if the distro updates the kernel, there is the chance it will repeat the same error.  Just repeat this process if that happens in the future.

---

### Post by theanswriz42 on 2006-06-10
[QUOTE=yager]You need to change root to (hd0,0).  Grub always boots from this device.  The kernel line is pointing to the correct place.

Step by step directions:
1.  Restart your computer.
2.  At the grub menu highlight the Ubuntu line and press "e".
3.  Highlight the root line and correct the line to read "root  (hd0,0)
4.  Press the "b" key.

At this point, Ubuntu should be starting up with no issue.

To permanently fix this, you need to edit your menu.lst file.  Execute the following command.

```
sud gedit /boot/grub/menu.lst
```

Scroll down to the error in the file and correct.  This will fix this for good.  Be aware that if the distro updates the kernel, there is the chance it will repeat the same error.  Just repeat this process if that happens in the future.[/QUOTE]
Good deal, now how can I edit the file if I can't even get that far in grub? Is there a way in kanotix to let me write to a file?

---

### Post by theanswriz42 on 2006-06-10
[QUOTE=theanswriz42]Good deal, now how can I edit the file if I can't even get that far in grub? Is there a way in kanotix to let me write to a file?[/QUOTE]

Ok, I changed the file using chroot and vi but i am still getting "error 25" in grub.

---

### Post by theanswriz42 on 2006-06-10
Ok, i changed everything and am now getting error 21 again

---

### Post by confused57 on 2006-06-10
[QUOTE=theanswriz42]Ok, i changed everything and am now getting error 21 again[/QUOTE]

If it's a new slave drive, make sure jumper settings are correct.
Does your bios recognize the slave drive?

Use kanotix livecd & see what this shows:

```
sudo fdisk -l
```
The -l is a lowercase "L".
or

```
cat /etc/fstab
```

If all else fails, you may want to try to obtain a different installation cd...the one you're using may be corrupted somehow.

---

### Post by theanswriz42 on 2006-06-10
[QUOTE=confused57]If it's a new slave drive, make sure jumper settings are correct.
Does your bios recognize the slave drive?

Use kanotix livecd & see what this shows:

```
sudo fdisk -l
```
The -l is a lowercase "L".
or

```
cat /etc/fstab
```

If all else fails, you may want to try to obtain a different installation cd...the one you're using may be corrupted somehow.[/QUOTE]
Thanks for the help, i sort of sudo fixed the problem by just making the linux hard drive master and the windows drive slave. Now I am getting grub error 13 which I'll deal with sometime tomorrow :)

---

### Post by yager on 2006-06-10
[QUOTE=theanswriz42]Now I am getting grub error 13 which I'll deal with sometime tomorrow :)[/QUOTE]

Since you changed the physical order of the drives, did you update the location of root from /dev/hdb1 to /dev/hda1?

Back to your earlier question about editing the file:
You can edit the grub menu.lst file directly from the grub menu when you boot up by pressing "e".  This gets you past the first hurdle which if you successfully boot the system then enables your ability to correct the /boot/grub/menu.lst file.
See this link for all of the details on grub.
[http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor](http://www.gnu.org/software/grub/manual/grub.html#Menu-entry-editor)

If you go back into your drive with the Live CD, verify that the referenced kernel file is indeed present and matches the name in the Grub file.  Also confirm the initrd file is also named correctly.  Very low probability of a problem but you never know.

Sorry I did not get back to you earlier, real life requirements took priority.

---

### Post by acorn22 on 2006-06-11
[QUOTE=yager]Sorry I did not get back to you earlier, real life requirements took priority.[/QUOTE]

What's that?

---

### Post by theanswriz42 on 2006-06-11
Haha, it's ok, I completely understand.

I did indeed change the device listings from /dev/hda to /dev/hdb, etc. so that's square. I was able to just chroot in kanotix since I couldn't get far enough in grub before to even edit the boot commands. 

As far as the error 13 stuff, i'll be looking at it later today and try to get that settled.

Cheers

---

### Post by yager on 2006-06-11
[QUOTE=acorn22]What's that?[/QUOTE]

Thats where I interact with other humans in a face to face mode vs. by keyboard or even phone.  

I once tried to just be there in body without the interacting part and the wife called me on that.  Was not a good moment.......  

Women, they have so many words they need to get out and they are not wanting me solve "problems".  I want to solve problems and she wants to marinate in the problem by explaining all of the intricate details of the problem.  It feels like I am being exposed to kryptonite.....  Must..... get ...... away......  Life..... force..... drain....ing.....a...w...a...y.........


Back the wiz's problem, I played around last night in GRUB trying to force an error 13.  I could not pull it off regardless of what I did. I change root, and the kernel line.  In no case was I able to force a 13.  I did get just about every other error number but not a 13.  This leads me to believe that you may not have a good ramdisk image or a bad kernel file.

Try rebuilding the initrd file.  For a 386 kernel:
```
mkinitramfs -o /boot/initrd.img-2.6.15-23-386 /lib/modules/2.6/15-23-386
```
For a 686 kernel:
```
mkinitramfs -o /boot/initrd.img-2.6.15-23-686 /lib/modules/2.6/15-23-686
```

To rebuild the kernel is over my head at this point in time.  There are several good threads on how to do this though.  Check this thread.
[http://www.ubuntuforums.org/showthread.php?t=157560&highlight=build+kernel](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=build+kernel)

One thing just dawned on me, can you successfully log in using the recovery mode version of your kernel?  If so, there is most likely nothing wrong with the kernel or the initrd file.

---

### Post by theanswriz42 on 2006-06-11
The problem isn't that I can't login to the ubuntu system, that all works just fine. When I try to boot into windows is where i'm having the issue now :)

---

### Post by theanswriz42 on 2006-06-11
[QUOTE=theanswriz42]The problem isn't that I can't login to the ubuntu system, that all works just fine. When I try to boot into windows is where i'm having the issue now :)[/QUOTE]

btw, here's the output of fdisk -l:

```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2628    21109378+  83  Linux
/dev/hda2            2629        2758     1044225   82  Linux swap / Solaris
/dev/hda3            2759       24792   176988105   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        8413    67577391    7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS
```

/dev/hdb1 is the windows partition, /dev/sda1 is an external drive for backups.

---

### Post by yager on 2006-06-12
I have never had much luck booting into Windows from the GRUB menu.  Apparently Windows likes to be the first operating system on the first drive in your system otherwise it gets all pissy.

You could try some of the GRUB commands at the GRUB manual page.

What I do is during bootup, I change the boot order of the hard drives to overcome the barrier to logging in.  When I want Linux, I set my external drive sda as the first hard drive for the BIOS to look at.  When I want Windows I change my hda drive to be the first drive.

For the short term, you could do the same by changing the boot order in your system to have te hdb drive be the first drive that the BIOS looks for a boot loader to load the system.  

Sorry I can't be of more help.

---

### Post by confused57 on 2006-06-12
In your /boot/grub/menu.lst, add this to your Windows entry:

map      (hd0) (hd1)
map      (hd1) (hd0)

between the "makeactive" line and the "chainloader  +1" line.

---

### Post by yager on 2006-06-15
Confused, you are the man!!!!  That worked perfectly for me.  I had tried this line but made a mistake of not putting a space between the devices on the map lines.  I did not notice til I pasted your code in.

Again, You da man!!!!

---

