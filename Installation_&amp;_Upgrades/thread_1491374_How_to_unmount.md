---
title: "How to unmount"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-05-23
Using Clonezilla to try to backup (as image) my partition. It gives me an error saying, "**Error**! No **unmounted** disk are found! To use **clonezilla** to save or clone a disk, the source disk must be **unmounted**! "
 
So I tried doing these commands:
 [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279560](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279560) 
(2nd post down) but they didnt recognize the unmount command. Plus when I did mount to see what was mounted, i did NOT see an sda1 or anything like that. I got a bunch of other stuff. ?
 
Is there another command to unmount?

---

### Post by darkod on 2010-05-23
Are you booting with the clonezilla disc? Or you are tyring to use the software from within ubuntu?

If you have booted ubuntu you can't unmount it. That's why the clonezilla image is bootable, burn a cd with it and you can boot with that cd. In that case no partition should be mounted.

---

### Post by new_tolinux on 2010-05-23
> **kakashi_12 said:**
> So I tried doing these commands:
 [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279560](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1279560) 
(2nd post down) but they didnt recognize the unmount command.
Read again. It does not say u**_n_**mount, it says umount ;)

---

### Post by kakashi_12 on 2010-05-23
I'm using the clonezilla live disc
 
Thanks. The command is recognized now! But hda1 is not! :( I tried both hda1 and sda1. And as I said, when i use the "mount" command, it does not see my hard drive. I just get a bunch of other crap.
 
Is there another command that will show me mounted DRIVES, not these dumb directories that i'm seeing. Here's a few examples of what im getting...
proc on....
sysf on...
udev on...
etc

---

### Post by kakashi_12 on 2010-05-23
You know... the darndest thing...
 
I was looking over my partitions and forgot that Win7 is actually my 2nd partition, cause win made a recovery partition in the first partition. So I'm like, "ok, let's try this cmd again with hda2 now. Command works this time, BUT it says partition is NOT mounted. WTF?! HYPOCRITICAL! First it says it is mounted, then it says it isn't?!?!

---

### Post by confused57 on 2010-05-24
I followed the clonezilla live cd instructions here:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

There were no commands to enter, just mostly arrow up or down to  highlight & "enter"...use the savepart just to image a partition.  Your destination partition(disk) would be mounted & your source partition is unmounted.  The instructions are fairly clear & easy to follow.

---

### Post by kakashi_12 on 2010-05-24
I know. the instructions are easy. But in this case, they won't work. I get _errors_.
 
I'v done this before with no errors, so I know how to do it. But now that there are errors, I am trying to fix it.

---

### Post by dino99 on 2010-05-24
the easiest way i know to manage devices and partitions is to use mountmanager and set your prefs with it as you want

---

### Post by darkod on 2010-05-24
> **dino99 said:**
> the easiest way i know to manage devices and partitions is to use mountmanager and set your prefs with it as you want

The OP is talking about using clonezilla live cd. How do you install mountmanager in that and how does it help his question?

The problem is that clonezilla is reporting strange settings about mount/unmount the target partition that needs to be backed up and doesn't want to proceed with the backup.

---

### Post by kakashi_12 on 2010-05-24
Right. And more specifically, it's the source drive that gets the errors (the one being backed up)

---

### Post by kakashi_12 on 2010-05-24
OK... Problem Solved:   (for the most part)
 
I diagnosed the problem as Clonezilla not "seeing" the drive. So I unplugged it from the motherboard (it was plugged into a 6 GB SATA port). Therefore, I guess clonezilla doesn't support 6 GB SATA drives, apparently. Then, I plugged it into a normal SATA port with a normal SATA cable (instead of a SATA 6GB cable).
 
NOW... when I go into clonezilla, it sees the drive fine. No error! Awesome.
 
Now... the question is. If I use this method to RESTORE my image... will it restore it correctly? Being that it's on a different port (not the 6 GB port). It shouldn't matter which port it is on, right? It will still boot the same way I think. That just changes the transfer rate. Right?

---

### Post by SlugSlug on 2010-05-24
df -h  will also show mounted drives

---

### Post by darkod on 2010-05-24
> **kakashi_12 said:**
> OK... Problem Solved:   (for the most part)
 
I diagnosed the problem as Clonezilla not "seeing" the drive. So I unplugged it from the motherboard (it was plugged into a 6 GB SATA port). Therefore, I guess clonezilla doesn't support 6 GB SATA drives, apparently. Then, I plugged it into a normal SATA port with a normal SATA cable (instead of a SATA 6GB cable).
 
NOW... when I go into clonezilla, it sees the drive fine. No error! Awesome.
 
Now... the question is. If I use this method to RESTORE my image... will it restore it correctly? Being that it's on a different port (not the 6 GB port). It shouldn't matter which port it is on, right? It will still boot the same way I think. That just changes the transfer rate. Right?

Yes, there shouldn't be any problem at all. 6GB is I guess the new SATA3. SATA2 port would only limit the transfer rate, there should be no difference in data backup/restore.

Good thing you thought about it. :)

---

### Post by kakashi_12 on 2010-05-24
Thank you. It always feels good to solve a problem you think you can't in IT. Rewarding and Relieving.

---

