---
title: "disk space reported wrong"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by MrKimi on 2012-02-28
My disk size is reported wrong. I'm seeing 79GB but I know it is 250GB.  I've read a lot of pages about changing partition sizes, but this is the  disk size, not the partition size. I can create a partition of size  79GB, but nothing larger.

Here's the history. I have two 250GB  SATA disks. I use one as my laptop internal hard drive, and the other I  attach externally with a USB cable. When I want to I can swap them  around. But what I usually do is use clonezilla to clone my internal  drive to the external one and keep the external one in a safe place.  Let's call the internal one A and the external one B or this will get  confusing.

Drive A suddenly gave me problems, my machine would  only boot to GRUB and no further. This coincided with my swapping the  internal drive with yet another drive and swapping it back, so I must  have screwed up something there. Anyway, drive A was bad.

So I  put drive B into my internal slot, booted and restored my backups. All  this worked fine. Now I want to clone drive B (which is my good system  disk now) to drive A which is the one that went bad. I don't need to  recover stuff from that drive, but I'd like to use it again if I can.

Clonezilla  told me the disk was only 79GB. Huh? All the other tools I've used say  the same. The most recent one I've used was GParted which allows me to  create a 79GB partition on the disk, but no larger.
I'm assuming there is some corruption in the disk geometry or similar. But I don't know what tools do that.

Drive  B (the one that works fine) has an msdos partition table. heads 255,  sectors/track 63, cylinders 30402, total sectors 488397168, sector size  512

Drive A (the bad one) has an msdos partition 255,  sectors/track 63, cylinders 9546, total sectors 153356490, sector size  512. Creating a new one with gparted gives me the same thing. cfdisk,  when given different geometry information, tells me I'm trying to use  more space than there is.

So, maybe this disk is just toast and I need another one, but is there something else I should try?
Thanks

(Ubuntu 11.10,  Dell 9400)

---

### Post by darkod on 2012-02-28
I have never needed to use fixparts, but try to see if it helps you in some way to correct the cylinders count:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It helps with some partition issues with success, not sure about cylinders issues.

Also, I have no idea if testdisk can do what you need, since it is usually used to bring back deleted or lost partitions. However I think it reports if it finds strange cylinder value, not sure if it can repair it though.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Can this be because of clonezilla use? It clones sector by sector, so if the partition cloned was 79GB can it somehow "lock" the disk at that value?

---

### Post by MrKimi on 2012-02-29
Thanks for the reply.

Fixparts did not seem to help. It reports the disk size:
[B]Disk size is 153356490 sectors (73.1 GiB)
[/B]which is a little less than the 79GB but I'll assume it is taking something off for overhead somewhere.
I could not see a way to mess with the cylinders. It looks a lot like another utility I tried (whose name I now forget) which did seem to allow me to mess with cylinders, but it gave me an error when I tried to do that.

I had already tried testdisk. That got me some files off the disk that I wanted. But it did not let me adjust the size (if there is a way to do that I overlooked it and I'm happy to hear more).

Clonezilla is unlikely to be the problem here. The disk A was working, then it stopped working. After that I popped it out and replaced it with the clone (disk B), and the clone worked fine. I cloned disk A about a month ago and I do this regularly so I don't see any way clonzilla could have messed with disk A in the last couple of days.

---

### Post by varunendra on 2012-03-03
When drive A (the bad one) is connected internally, go into BIOS and note down its name as seen by the BIOS. Post it here. If it is same as the one on its sticker label (which says, along with other things, that it is 250GB), you have a fair chance of fixing it back to normal. If it seems something strange and different from what its label says, then most probably its BIOS (the drive's own BIOS program on its EEPROM chip) has gone corrupt, and there is nothing you can do about it (except, if you are extremely lucky, to get a replacement card of same model and batch). Although the possibility of the BIOS being corrupt is just next to zero, because then you wouldn't have been able to use it at all!

Also, are you sure someone, without your knowledge, didn't actually 'change' the drive with a similar looking 80GB one? Maybe someone from CIA or KGB (or maybe even some naughty creature from mars..!!) ;)

Because similar problems may occur if a partition is copied using 'dd' command, but that is very easy to fix, and in case of any file system corruption, no matter how serious, I believe the fixing is just a matter of (at-most) deleting and re-creating partitions _if the BIOS sees the disk correctly_.

Another possibility is the corruption of the part of disk-BIOS that resides on the disk itself (and defines its geometry), which again is beyond your control and thus is non-repairable (any software tool can't repair something that it can't 'see'). Although this one is just a guess based on some (weak, poor, almost useless) theoretical knowledge about modern hard drives.

---

### Post by MrKimi on 2012-03-09
I've been away (offline) or I would have replied earlier.

Thanks for the reply. I went into the BIOS and it told me it was seeing a 79GB disk (ie the shortened size, it didn't give me any other information). The label on the disk (still) says 250GB. So I conclude the disk's EEPROM believes the size is 79GB and I'll take your advice that 'there's nothing you can do about it'.

Possibly Martians switched the disk, we don't have CIA or KGB in this part of the world. But I didn't think we had Martians either so what do I know? If anyone did switch the disk they would have had to break into my house and put a disk with an incorrect label as a substitute for the one I had. And leave the other disks alone. I guess Martians might do anything.

I'll mark this as solved now because I'm convinced this isn't going any further. Disk space is too cheap to spend more time on it esp when more time is unlikely to solve it.

---

### Post by varunendra on 2012-03-11
Well, if the label says 250, and you are 'able to use' the visible 79GBs, then it suggests there is something beyond my current knowledge, and there may be other (possibly easier) ways to make it recognize all the 250GB space.

But with present amount of knowledge I have about it, digging more would almost certainly be a thing for only those who like digging just for the kick of it. For someone like you who seems to care about time and reasonable outcome, I think you are absolutely right about:
> **MrKimi said:**
> ....Disk space is too cheap to spend more time on it esp when more time is unlikely to solve it.

I wish someone with more knowledge about this kind of problem and possibly its solution comes across this thread and enlighten us with his/her valuable input.

---

