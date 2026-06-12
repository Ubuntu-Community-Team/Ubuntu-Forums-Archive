---
title: "GRUB on floppy, edgy on primary slave, no work"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by partriv on 2006-11-15
hey guys, last night I tried to set up a dual boot, using windows XP on my primary master, and installing edgy on my primary slave.  Windows XP was installed already, and has been for a while now.  I installed GRUB on a floppy (fd0).  After installation completed, I rebooted and tried to boot off my floppy, it never loads Grub.  I checked my boot sequence in BIOS, it is correct, my edgy cd was not in the drive, it would just go straight to the windows boot up.

Any ideas on this?  I've setup a few dual boots over the last few years, and messed some stuff up really bad (destroyed MBR's :)), and have had some great successes, so I am relatively familiar with how this works.  Can I not load grub from a floppy if i install ubuntu on a primary slave?  

Also, I have a secondary master that is still untouched.

Thanks!

---

### Post by bulldog on 2006-11-15
The most easiest way to do what you want [except booting from a floppy]

Make the Ubuntu disk master,and install GRUB here in the MBR.
Make your windows disk slave. or secundary master.

Now you have to map your windows entry in GRUB,but that is an easy fix.

This way you can start Ubuntu and windows with GRUB or set your windows as a default boot.
If GRUB fails for what reason,you simply change the boot order in your BIOS and boot windows from it's own loader.

This is the most comfortable way to dual boot and the safest,in my opinion that is :D 

Think about it and if you have any question about it let me know.

---

### Post by partriv on 2006-11-15
I understand that that would be the easiest, but I've already got windows installed as primary master and I am trying to do this without reinstalling windows.  Is it possible to do what I am trying to do?  and do you have any thoughts as to why Grub is not loading from my floppy? Thanks!

---

### Post by bulldog on 2006-11-15
Maybe you can simply change the boot order in your BIOS,that should be the easiest way,but if that's not possible,you have to fysically change the cabels from your hdd [shut down the computer first and make it power free.]

You don't have to reinstall anything but GRUB.

Why it's not booting from your floppy,I have no idea,just check the floppy and see what's on it.
Never did it that way,so can't be of any help there.:D

---

### Post by partriv on 2006-11-15
that's a good thought, about the cables.  I already tried changing the boot order in my BIOS, and when I tried to load off the ubuntu drive, it simply said 'Error Loading OS' :(

Might this be because it's primary slave?  Would that affect me at all?  Should i switch it to secondary master?  D'oh!!

---

### Post by bulldog on 2006-11-15
You have to get GRUB installed to boot Ubuntu.
You have it on a not working floppy so you have to install it to the MBR of the Ubuntu disk.

Then make te Ubuntu disk the first boot device in your BIOS,setup the windows part in your menu.lst and your clear to go.

To install GRUB from the live cd,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0) (or hd1 if your root is on hd1)
```
Finally exit the grub shell
```
quit
```
That is it. Grub will be installed to the mbr.

Now reboot and you will see grub on the Ubuntu hdd.
Open a terminal and type
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
To make a copy for if things messed up :D 
```
gksudo gedit /boot/grub/menu.lst
```
to open your menu.lst and add the following to the end of the file
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by partriv on 2006-11-15
dude thank you so much!  i havent gotten a chance to try it yet but it looks like it will work.

So my last question about this before I try it is: Do i need to load ubuntu on to my secondary master to install grub to its MBR? or does a slave drive have an MBR  that a bootloader can be installed too?

I will try this in a few hours, as soon as i get home from work :)

---

### Post by bulldog on 2006-11-15
Every hard disk has a MBR,don't worry.

Read the tutorial carefully,if you ask where root is you get the location on your second drive [the Ubuntu disk]this would be (hd1) I reckon.

If so the last part is setup GRUB to the MBR and here you have to use the disk which was given to you in question 1

If root is (hd0,1) you setup GRUB (hd0) if root is (hd1,1) you set up GRUB (HD1)

---

### Post by partriv on 2006-11-15
so i did this, and here's what happened:

windows is still bootable
grub is installed on the primary slave, and i can boot to it, but when i try to load ubuntu from it, it says it cannot mount the partition.  any ideas? :(

Next I think i may try to install ubuntu to the secondary master, unless someone has any ideas before i get started on that.

Thanks!

EDIT-----

I've went ahead and switched my drives around, my windows which was primary master is now secondary master, and i've switched a blank drive to primary master to install ubuntu on.  

switching windows from primary master to secondary master and switching the boot sequence in my bios still enables my windows to boot as well!

hopefully just doing a good ol regular install of ubuntu on a primary master should work :-D

---

### Post by confused57 on 2006-11-15
Here's how I have my system set up(similar to what bulldog suggested):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

