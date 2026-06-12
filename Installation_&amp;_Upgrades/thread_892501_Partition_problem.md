---
title: "Partition problem"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by tehMurloc on 2008-08-17
I managed to solve my first problem (thanks for help), but now I have a new problem =(

I booted the computer from install disk and selected "try Ubuntu without affecting system" or something like that. The install works like normally, but on partition section it shows no partitions at all. Message like this pops up: "No root file system defined. Please correct this from the partition menu,"

I've got a screenshot of this: [Imageshack link]("http://img374.imageshack.us/my.php?image=screenshotqr6.png")

Thanks for your help

---

### Post by az on 2008-08-17
It should offer you the choice of guided partitioning or manual partitioning.  If you go into manual partitioning and try to go forward without setting any partitions up, you get that error.

You either need to use guided partitioning (where the installer does the partitioning for you) or create a root and swap partition yourself.

If you intend to dual boot, be sure to not pick the "use entire disk" option since that will erase anything you already have on the disk.

---

### Post by tehMurloc on 2008-08-17
> **az said:**
> It should offer you the choice of guided partitioning or manual partitioning.  If you go into manual partitioning and try to go forward without setting any partitions up, you get that error.

You either need to use guided partitioning (where the installer does the partitioning for you) or create a root and swap partition yourself.

If you intend to dual boot, be sure to not pick the "use entire disk" option since that will erase anything you already have on the disk.
It offers me no choice between manual and automatic =(
First, it asks me for language
Secondly, it asks me for location
Thirdly, it asks me for keyboard layout
Fourth is the screen in the screenshot image, no choices offered

And I'm not going to dual-boot it, only Ubuntu

---

### Post by az on 2008-08-17
My first guess is that no hard drive is detected.  Is this so?  When you boot the live cd, are you able to see a hard disk?

If you open a terminal, what is the output of

sudo lshw -C disk -short

(That will LiSt HardWare, looking only for disks.)

---

### Post by Andropov on 2008-08-20
hey, i was reading this conversation and it was such a tease, I was having the exact same problem.  I went ahead and ran that command for you and this is what it returned.

H/W path            Device      Class       Description
=======================================================
/0/100/f.1/0.0.0    /dev/cdrom  disk        CD/DVDW SH-S182M
/0/100/f.1/0.0.0/0  /dev/cdrom  disk 

I did a couple other things are you are defently correct, Ubuntu is not recongizing the hard drive.  Currently I have PClinuxOS installed on my computer, im making the switch on the advice of a friend.  Any help would be greatly appriciated.

---

### Post by Pumalite on 2008-08-20
How many drives do you have?

---

### Post by Andropov on 2008-08-20
just one 500g sata seagate hard drive.

---

### Post by Pumalite on 2008-08-20
Try editing your boot line (of the Live CD) and adding all_generic_ide at the end of the line.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by sandysandy on 2008-08-20
did u get option for alloting partition for [COLOR="Red"][SIZE="6"]/[/SIZE][/COLOR] (root)

post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] from live Cd.
regards

---

### Post by jmate24 on 2008-08-20
To correct My Fellow Posters... Check the Bios and see if the SATA hard drive is using RAID or IDE if it is using RAID then Switch it to IDE. I had that same accident and I had to hit my head on the underside of my desk to remember that.

---

### Post by Pumalite on 2008-08-20
Read this thread carefully:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57](http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57)

---

### Post by Andropov on 2008-08-21
Sandy ~ Nothing happened when i did sudo fdisk -lu

As for editing the boot line, i think i missed where im supposed to be, so I'm working on finding how to edit that.

---

### Post by Andropov on 2008-08-21
Pumalite wins.  Thank you so much for the help, it took me a few minutes to figure out why I couldn't figure out how to edit the boot line but I had to throw on F-lock and then i could hit f6.  then from there it was a pretty simple step to put in all_generic_ide, rebooted onto live CD and cake.

---

### Post by tehMurloc on 2008-08-30
> **jmate24 said:**
> To correct My Fellow Posters... Check the Bios and see if the SATA hard drive is using RAID or IDE if it is using RAID then Switch it to IDE. I had that same accident and I had to hit my head on the underside of my desk to remember that.
I switched it into IDE and now my computer doesn't boot at all O.o

---

### Post by az on 2008-08-30
> **tehMurloc said:**
> I switched it into IDE and now my computer doesn't boot at all O.o

Boot the live cd and check to see what drives are detected.  It may be that their order has changed and that your montherboard is trying to boot the wrong drive.  That's an easy fix.

---

