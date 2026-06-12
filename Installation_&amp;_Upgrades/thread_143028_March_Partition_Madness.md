---
title: "March Partition Madness"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by Steverini on 2006-03-11
Greetings all, 

I apologize in advance if this has already been covered, however I haven't been able to find anything that directly addresses my question, so I'm relying on you guys.

Scenario:

I have a single 80 gig HDD with Windows 2000 currently installed in a single 80 gig FAT32 partition.  Yes, I know NTFS is better, but I'm a dinosaur and I absoutely refuse to change this ;) 

I have Partition Magic 7.0

I do not have my Ubuntu CDs yet.  I would like to get the baselline partition(s) set up for a future Ubuntu install using Partition Magic.

I want to scale my W2K partition back to about 40 gig, but also want to leave about 15 gig for a separate FAT32 partition (accessible by both Linux and Windows.

Questions:

Partition Magic asks me how I would like my primary partition divided.  I answer 40 gig.

Partition Magic asks me if I intend on installing an operating system in the remaining space.  Here's where I'm not sure what to answer.

If yes, it will make the new partition a primary partition.
If no, it will make it a logical one.

Which should I choose?

Abstract:

Based on how I partition the drive as described above:

Once my Ubuntu CDs arrive, I'll most likely end up allowing the installation procedure to further partition the secondary partition I just partitioned (confused yet?  yea, me too)  and set up the linux ext3 and swap partitions as it sees fit.

Question:

Once I launch the Ubuntu installer, Will it allow me to retain a portion of my second (newly partitioned partition) FAT32 partition?

I have tried to explain this as intelligently as I can, however, I am suffering from partition insanity as you can probably tell.

As an aside, I run regular backups to my External USB drive using Acronis TrueImage 8.0, so If i completely screw this up, I can recover nicely with no fallout at all.   This does not mean I won't be chewing my fingernails when I decide to hit the 'commit' button in Partition Magic, it simply means I can get my original system (partions and all) back if I need to restore from my Acronis Image.  BTW, I highly recommend Acronis TrueImage.   But that's a whole other post for another day.

Any advice will be most welcome!

Regards to all, 

Steverini

---

### Post by KansasJoe on 2006-03-11
The ubuntu partitioner will ask you where to put the operating system which will be where you created the ext3 and the swap in partition magic(or you don't have to make swap in partition magic and ubuntu will make swap for you).  It's not really gonna save you any time by partitioning with partition magic now vs using ubuntu partitioner when you dl the iso file or receive the cd's.  It won't touch your fat32 as long as you tell it not to.  Personally, I think it would be best if you just created your seperate fat32 now with partition magic for whatever reason you want to do this may be.  Then when you get the cd use the partitioner which comes with the installer.

---

### Post by NatvAmer on 2006-03-11
I used Partition Magic 8.0 with Windows XP to re-partition my 40G drive. (I don't think it cares if it is FAT32 or NTFS) I just told it to resize the existing partition to 15G and leave the rest blank.

When I rebooted into XP that is when I went to the control panel and in computer management I partioned a FAT32 partion for sharing. 

When that was done I booted to the Ubuntu installation disc and let the partitioner use all unused free space and used GRUB to Dual Boot.

---

### Post by thoffland on 2006-03-11
I just did something similar... I had a 40g hard drive with Windows 2K server on it, but wanted to load Edubuntu on it as well... so I used GParted and partitioned the hard drive for Edubuntu. Be sure to defrag Windows first... then partition it. 

I think that either way you do it, Ubuntu will format the partition for you anyhow, so I dont think you need to worry about ext3 right away. Just be sure that when you install it that you create a swap partition as well, it might do it automatically for you depending on the options you choose.

I hope this helps... I'm sure someone more knowledgable will chime in with a better answer.

---

### Post by aysiu on 2006-03-11
If your Windows partition is already FAT32, you don't need another FAT partition for sharing files.

And the Ubuntu partitioner may actually be better than Partition Magic, believe it or not.

When you get your CDs, print out this webpage:
[http://users.bigpont.net.au/hermanzone](http://users.bigpont.net.au/hermanzone)

---

### Post by Steverini on 2006-03-11
Thanks to everyone.  

I have heard that gparted is a pretty stout partitioning tool.  I'll probably just turn it loose and see what happens, gambler that I am.  If you don't hear from me for a while, It didn't work!   But I don't expect that to happen.  Anyhow, thanks for all the feedback!   

Now go drink some green beer.  Why wait for Friday?

---

