---
title: "Problem installing XP to dual boot"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Jayse196 on 2007-02-28
Hi everybody.  I think I'll start off saying that i'm actually running Kubuntu, but figure that that detail doesn't have much of anything to do with my problem.


I was running only Kubuntu, but then realized that I would at least like to have XP there so I would have the option of switching back to it for some apps.  So I rearranged the partitions and set up a new one (10GB for Windows, 60GB for Ubuntu; Windows doesn't need a lot of space :) ).

So, I set up the partitions and everything, and just now popped in the xp cd to install it on the partition, but when I go to install it, it says it can't find a hard drive.

So...does anybody have any advice, or think they might know what's wrong?  I have no problem with just wiping the whole drive clean and starting over again if need be.

any help would be greatly appreciated, and sorry if the answer is actually quite easy...I tried searching around for answers but couldn't find anything.
thanks!

---

### Post by jamb on 2007-02-28
Hi,
have you installed Kubuntu, and after that moved on to install XP?
I did the all this but in opposite order, first partition the HD as you want it, then install XP, and then Kubuntu (the alternative install disk  gives you better control). No problems at all! Happy Linuxing.
FYI, I have also created a third FAT32 partition (where you can share data between the two OS).

Kubuntu 6.06 LTS, on AMD64

---

### Post by renzokuken on 2007-02-28
what is the partition that you want windows to use formatted as (i.e. filesystem?)?

i think xp has a problem reecognising some filesystems.

another issue may be that xp doesnt have the necessary drivers to recognise the drive. is it SATA or IDE. if its SATA you may have put the apprpriate drivers on a floppy and hit F6 when asked by the windows install to load 3rd party drivers so it can recognise the drive. i have to do this on my desktop when i want to install xp.

---

### Post by Jayse196 on 2007-02-28
> **jamb said:**
> Hi,
have you installed Kubuntu, and after that moved on to install XP?


yes, that's what I did.



> **renzokuken said:**
> what is the partition that you want windows to use formatted as (i.e. filesystem?)?

i think xp has a problem reecognising some filesystems.

another issue may be that xp doesnt have the necessary drivers to recognise the drive. is it SATA or IDE. if its SATA you may have put the apprpriate drivers on a floppy and hit F6 when asked by the windows install to load 3rd party drivers so it can recognise the drive. i have to do this on my desktop when i want to install xp.


I'm honestly not sure what type it is, SATA or IDE; I'm on an HP Pavillion dv6000t laptop, if that helps at all.


but at first I noticed the partition for windows wasn't formatted, so I formatted it to FAT32.  Tried installing windows and it still said the same thing, that it couldn't find a drive.  Then I drived hitting F6 when the cd asked me.  After that I got a screen saying that it didn't have a driver and to hit S if I wanted it to look more, or F3 if I wanted to quit.  I hit S, but then it said that it couldn't find a floppy disk with drivers (I don't even have a floppy drive so this makes sense).

Well don't I feel stupid; I just opened up GNOME partition editor (what I used to make the partitions) and realized that the partition where I want to install windows doesn't have a mount point.  I'm assuming this is an important thing to have, right? :oops: But I don't know how to give the partition a mount point, if it's even possible.

thanks again for all your help, sorry if this is kinda a newb question... :)

---

### Post by renzokuken on 2007-03-01
it is possible to mount the windows partition but it shouldnt make any difference. that only mounts it when booted into ubuntu. shouldn't need to do that for an install

---

### Post by jamb on 2007-03-01
Hmmm..
I still suspect that Windows is less flexible in this case. This is how I did it. First back-up all your valuable data to a hard disk drive, e.g. an external USB drive.
Insert the Windows CD and boot the install disk, then go for a new install. Use FDISK to partition the complete drive - note all your data will be lost! 
If you have a SATA drive, Windows will for sure complain and ask for the driver, so you will find out. Assuming your drive is not a SATA drive, continue and remove all partitions.
Set up the primary partition for Windows, then leave the remaining space as is. Format the partition with NTFS, Then continue with the Windows installer. Once done, install Kubuntu, and instruct it to use remaining free space for Linux. That's it.

---

