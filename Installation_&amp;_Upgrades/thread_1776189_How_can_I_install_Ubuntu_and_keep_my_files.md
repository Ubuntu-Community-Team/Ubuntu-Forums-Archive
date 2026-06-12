---
title: "How can I install Ubuntu and keep my files?"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by acidincense27 on 2011-06-05
Okay, so, I showed Ubuntu 11.4 natty Narwhal to my fiance, and she thought it was awesome. She loved how simple it was, and she loved the interface. She wants me to install it for her on her computer. It's currently loaded with Windows Vista, but she has a ton of important files on it. She's an artist and her work is very important. Now, my question is, how can I install it for her and keep all of her files. She doesn't have enough space on her hard drive for a backup. Her drive is about 250 GB, and 200 of those are used. Is there a way that I can like install it but keep her files? Perhaps I can install it on the remaining 50 GB and move the files over to the Ubuntu partition?

---

### Post by BlueDon on 2011-06-05
I don't think it is possible I'm afraid. I'm sure someone who knows a lot more than I do will tell you, but your best bet is to buy an external drive and backup the files (which if she has a lot of her own work on her comp it's probably worth doing anyway) and then putting them back on. 

I don't think you can copy over files because the formatting is different. A windows install runs on an NTFS format whereas Ubuntu runs on EXT4 and so they don't cross over.

---

### Post by oldos2er on 2011-06-05
Ubuntu can read and write to NTFS just fine; however Windows, as far as I know, can't read or write to ext4.

I suggest you backup any sensitive files before any OS installation though. Hard disks or USB drives are relatively inexpensive.

---

### Post by kjuergen on 2011-06-05
If these files are that important I would say it's criminal to have them on one drive only...... Especially if it's on a winDOS machine (I just had my work laptop corrupt everything on it's own, winDOS 7 pro!).
Get one of these cheap 500GB USB drives and transfer all files. Later use the drive to make regular backups.

Modern HDDs are no longer what they were years ago. Only the professional variant (expensive)have good lifetimes. The consumer grade el-cheapo stuff sometimes fails after weeks but they all have one thing in common: they fail, you just don't know when.

As to your question: you could use a partition manager to split the HDD into 2 logical partitions. Copy the files you want to keep over to the new partition and install ubuntu in the one you had winDOS. Then mount the second partition.
However, I would never attempt to do that w/o having a backup of the files (see above)!!!! And then it's easier to just copy them to the USB drive, install whatever you want and then copy them back.

Juergen

---

### Post by Mark Phelps on 2011-06-06
> **acidincense27 said:**
> ...It's currently loaded with Windows Vista, but she has a ton of important files on it. She's an artist and her work is very important...Perhaps I can install it on the remaining 50 GB and move the files over to the Ubuntu partition?

First thing you should do is back off ALL the "important" files.
If you're not able to do that, then leave it alone.  

Seriously. 

Do NOT attempt to use ANY Linux utilities to shrink (or split) the Vista partition.  It has a nasty reputation for being easily corrupted.  And if that happens, you can say goodbye to all the "important" files. 

Once you have backed off your important files, you can TRY using the Vista Disk Management utility to shrink the OS partition -- but don't be surprised if it doesn't allow much shrinkage.  It's famous for that.

And, once again, do NOT resort to using Linux utilities to try to FORCE the shrinkage down to a level you want.  That's very likely to corrupt the Vista filesystem and render it unbootable.  And then, how are you going to retrieve your important files if you can't even boot the PC?

---

### Post by gylti on 2011-06-06
> **acidincense27 said:**
> Okay, so, I showed Ubuntu 11.4 natty Narwhal to my fiance, and she thought it was awesome. She loved how simple it was, and she loved the interface. She wants me to install it for her on her computer. It's currently loaded with Windows Vista, but she has a ton of important files on it. She's an artist and her work is very important. Now, my question is, how can I install it for her and keep all of her files. She doesn't have enough space on her hard drive for a backup. Her drive is about 250 GB, and 200 of those are used. Is there a way that I can like install it but keep her files? Perhaps I can install it on the remaining 50 GB and move the files over to the Ubuntu partition?
external hard drive, online backup or cds dvds is essential - best thing is for her to have a spare hd or even another comp and use that to mess around with before she tries anything drastic

---

### Post by awam66 on 2011-06-06
I have just done an install of 11.04 on a friends machine and one of the options in the installer is to copy the files from the windows partition. It did this and all the files showed up in Documents on the Ubuntu installed filing system. Go for it buty as has been said above back up all important files first.

---

### Post by kev77 on 2011-06-06
I would echo users above, buy an external drive, i would not risk trusting important files to a partition manager, 500gb would be ideal size!

---

