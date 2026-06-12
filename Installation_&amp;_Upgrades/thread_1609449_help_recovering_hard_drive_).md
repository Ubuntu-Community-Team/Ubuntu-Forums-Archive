---
title: "help recovering hard drive :)"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by nthali on 2010-10-30
Hello ubunters,
Alright, so i couldn't install ubuntu on my laptop's internal pointsec encrypted hard drive, so i decided i would use my 250G external free agent seagate drive for a full install - it has (had?) my entire data on it as a windows NTFS drive - i decided i would do a "New Partition Table", and thought i would leave the beginning 180 G untouched (do not use this partition), assuming it would stay as a windows NTFS, and use the other 70G to install (60G ext4 and 10g swap).
ubuntu pretends to install everything and is all done and asks me to restart - i do, and i don't see any dual boot screen - should have known that i probably can't dual boot off of an external hard drive. windows starts up fine - that's a relief - but then the external hard drive is no longer recognized by windows. it just doesn't show up as a lettered drive, although the "remove" item in the system tray calls it a "Mass storage device".
i try to boot from the CD again, and notice that ubuntu calls this external drive as the "250G hard disk: 60G filesystem" as i had partitioned it.

So long story short: 1 burning question
is my data hosed in the 180G unknown partition? or is there a way to salvage it?
i'm pretty sure i didn't check the "format" option, so should it somehow still be there and somehow reachable?

Thanks,
Nilesh

---

### Post by q999 on 2010-10-30
the tool I use for fixing inspect and copy  partions is [http://partedmagic.com/](http://partedmagic.com/) and or [http://clonezilla.org/](http://clonezilla.org/)
  free linux live cd or 
almost any other live cd to
 view windows and or linux partions and data.
now any encrypted partion will not be readable
 and booting to them will take the proper disk order.it must match the encrypted drive.
..good luck

---

### Post by Mark Phelps on 2010-10-30
Messing around with partitioning tools is a sure-fire way of making your situation worse!!

When you attach your drive, and you go into Places, can you see the 180GB partition? If so, can you open it and see any of the files?

When you attach your drive and boot into MS Windows, which OS version are you running? If it's Win7. open the Disk Management utility, scroll down to the bottom of the list and see if the space is listed as Offline.  If it is, you can switch that to Online and it will assign it a drive letter.

---

### Post by nthali on 2010-11-05
Thanks folks for the replies.
However, the 180G partition was completely invisible to both Windows (it's XP, unfortunately, not Windows 7), and PartedMagic which i tried as well. 
I even tried my luck at having PartedMagic change the partition type to NTFS (whereupon it did give me the warning that this had the "potential for loss of data", which i accepted), but it failed with some error.
 
I was left with no choice but to look for partition/disk recovery software - i found and tried the free EASEUS Partition Recovery utility which didn't help so i tried the free EASEUS Data Recovery Wizard - it's free to recover 1G only, but it was a proof of concept to see if it could find my files - indeed it did, whereupon i had to bite the bullet and buy the full version ($69.95), and yet another external hard drive to recover all the data onto. very expensive mistake for me.
 
worst part is that i can't imagine that i'll be using the data recovery wizard very much - such stupid mistakes (should) happen only once in a blue moon :)
 
but if anyone knows of any other free software or any other tips on how to recover data like this, i'd love to hear about it.
after all, the data and the NTFS should have been perfectly intact - all i should have ideally needed to do is tell the computer somehow that this is an NTFS, so treat it as such, and read the data. but maybe not.
 
thanks again,
Nilesh

---

### Post by dino99 on 2010-11-05
this might help:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

