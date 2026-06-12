---
title: "Cannot mount laptop's CD-ROM"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2010-03-01
Hi all,

Seems every time I run the update on my Lucid install something happens to the CD-ROM mounting. Yes, I know it's Alpha, but I'm not seeing other posts about this so am not exactly sure what to think.

Attached is the system report and the fstab. Originally, the fstab had something different in there, which I changed to match the system report, but still no go. (report was too big to attach so snipped out middle part that dealt with system memory).

When I try manually mounting I'm getting errors:

$ sudo mount /dev/cdrom /media/cdrom0
mount: /dev/sr0: unknown device

Where is the sr0 coming from???

Robert

---

### Post by mc4man on 2010-03-01
Your fstab is wrong, for the moment edit it to this ( may not be the only issue you have..

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

It's possible /dev/sr0 would also be ok though I'd stick with what's been used to date - /dev/scd0

(only mentioning that because starting in lucid for an autorun script I have for audio cd's from multiple drives I had to change scd* to sr* for it to work right (in the script - not fstab

---

### Post by Robertjm on 2010-03-01
Thanks!

I tried /dev/sr0 and /dev/scd0

Both return the error msg

mount /dev/sr0: unknown device

---

### Post by mc4man on 2010-03-01
Well I'd leave the fstab as posted above, not that important other than you should have a proper entry.

In your report it indicated media was detected in the drive without a filesystem.

 > configuration: ansiversion=5 status=[COLOR="Blue"]ready[/COLOR]

This would be expected if you had an audio or blank cd/dvd in the drive, do you remember?

If posible insert a disk with a filesystem - a dvd movie, data cd, data dvd, ubuntu live cd ect.

Then after the drive settles run in a terminal
```
sudo lshw -C disk 
```and post ( only care about the *-cdrom: entry

---

### Post by Robertjm on 2010-03-01
Looks like the problem was probably not a problem at all, but really an issue with bad media.

I was trying to mount the drive using a CD someone had burnt for me at my church. I had put it in my drive without really looking at it. After getting annoyed with the problems I pulled it out of the drive and took a look to make sure it was actually written to! There was all sorts of "oily" looking stuff on the bottom. Perhaps he was eating a donut?

I cleaned the CD off and tried mounting it again, but to no avail. Then I tried a different CD. This one mounted just fine (using /dev/sr0 in the fstab BTW) and I was able to read the disk just fine. I've had a problem before where whoever was running our soundboard didn't finalize the audio CD so I'm guessing that's what happened here (besides being covered with jelly!)

Wasted several hours on this idiotic problem. Only reason I admit the most simplest of things I should have tried immediately is to save someone else the grief should they read this thread in trying to solve their problem. ;)

Robert

---

### Post by VMC on 2010-03-01
> **Robertjm said:**
> Thanks!

I tried /dev/sr0 and /dev/scd0

Both return the error msg

mount /dev/sr0: unknown device

What's the output of this:

```
wodim -checkdrive
```

---

### Post by cariboo on 2010-03-01
I was going to add to this earlier, but work got in the way. :) I don't have an entry for a cd-rom at all in /etc/fstab, cds and dvds still mount.

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=b2b062ff-c687-4306-a9ce-89ed8b2bddd8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=386d0109-5af3-45a1-a049-7d76a277fece /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=53c80ab9-9fd1-412b-a4aa-5b2163e9e9b7 none            swap    sw              0       0
```

---

### Post by mc4man on 2010-03-01
> I don't have an entry for a cd-rom at all in /etc/fstab, cds and dvds still mount.
I don't think it's that important anymore, though having an incorrect entry may be an issue vs. none at all.

I guess if an app was looking only for an expected mount point (media/cdrom0, /media/cdrom1), that would be a problem but more typically they look to /dev/*

Have also noticed that in lucid only the boot cd/dvd drive ends up in fstab in multi-drive systems anyway.

---

