---
title: "Failing Hard Drive, best way to copy to new Hard Drive"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by wingrider78 on 2010-12-14
Hello, I have a hard drive that is failing (ran the SMART test and have a "current pending sector count" and when I ran the short test, it came back okay, but running the long test the test showed "Failed, Read"  The overall assessment show a green dot but that the disk has a few bad sectors.  About a week ago my tower started making a periodic humming noise, I am only assuming that it is the hard drive.  My question is, how do I copy my entire drive to a spare drive I have that I can just put in and be good to go??  I am pretty sure there is some fancy little terminal command that can accomplish this since everything else can be done in the terminal :) I just don't know what it is.  Let me know if you need any specific data from my computer and I'll get it for you.  Thanks.

---

### Post by CharlesA on 2010-12-14
You can use dd to do a bit-for-bit copy.

I would suggest using clonezilla to copy the data to the other drive.

---

### Post by dino99 on 2010-12-14
Dont worry too much about the "marketing failures" reported by SMART ( tool made by seagate, ibm, wd & co to sell you new hardware)

noise can be made by some installed package(s) like hddtemp, can be removed anyway, dont need it.

run a fsck on next boot:

sudo shutdown now -R

to copy/duplicate, you can use clonezilla or follow this:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by CharlesA on 2010-12-14
> **dino99 said:**
> Dont worry too much about the "marketing failures" reported by SMART ( tool made by seagate, ibm, wd & co to sell you new hardware)

SMART is there to monitor the health of the drivel that's it's job.

Each drive has a number of spare sectors that it can use to remap to should sectors go bad. As time goes on, and a drive develops more, and more bad sectors, you run out of spares and then start getting read errors.

If the OP is getting read errors, then the drive is having problems.

---

### Post by dino99 on 2010-12-14
This "great" SMART report errors on all my hdds for age now, and you know what, they continue working like a charm. As said previously, dont trust this tool, period.

---

### Post by CharlesA on 2010-12-14
> **dino99 said:**
> This "great" SMART report errors on all my hdds for age now, and you know what, they continue working like a charm. As said previously, dont trust this tool, period.
That's your choice. :)

The thing to keep in mind is to look for changes.

I've got a drive with 8 bad sectors, but it's not having any problems (yet). I'm not all that worried about it since I keep backups of everything.

---

### Post by Herman on 2010-12-14
> sudo badblocks -sv /dev/sda# >> badblocks.reportWhere: '#' is replaced with a partition number.

The badblocks command can give you a pretty reliable second opinion.

---

### Post by CharlesA on 2010-12-14
> **Herman said:**
> The badblocks command can give you a pretty reliable second opinion.

+1. It may take a while to run, depending on the size of the drive.

---

### Post by presence1960 on 2010-12-14
Disregarding SMART or outright dismissing SMART is not "SMART"

It is a tool used to monitor your disk(s), it is not a crystal ball but it will alert you to changes you may want to be concerned about so you don't lose your data.

To subscribe to the "conspiracy" theory is foolish, SMART does not exist to sell more hardware, just as expiration dates on food & drugs are not there to sell more of the same.

---

### Post by presence1960 on 2010-12-14
> **Herman said:**
> Where: '#' is replaced with a partition number.

The badblocks command can give you a pretty reliable second opinion.

Thanks for restoring sanity Herman.

---

### Post by wingrider78 on 2010-12-14
Thank you for all the replies, I just finished running SeaTools from seagate (maker of my hard drive) it found several bad sectors and in the end, repaired all the bad sectors.  All seems well for the hard drive, but the computer is still making that intermittent humming noise.  Off to find the culprit...

---

