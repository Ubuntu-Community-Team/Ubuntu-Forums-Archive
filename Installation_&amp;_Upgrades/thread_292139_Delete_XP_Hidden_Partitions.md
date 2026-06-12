---
title: "Delete XP Hidden Partitions?"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by brotherajnin on 2006-11-03
I recently bought a new Dell (XP) and tried to install Ubunutu, however I couldn't because all four primary partitions were being used.  In addition to the usual C: and D: drives, there were:

1) 47MB FAT16 EISA Configuration

2) 3.50 GB FAT32 (Unknown Partition)

Apparently the first contains drivers and diagnostic software, the latter is for restoring the system.  

Some websites say it's safe to delete them, others say it's not.  What are my options here? I want a dual boot system so I'd rather not just overwrite the entire drive.

---

### Post by Dr. Nick on 2006-11-03
I am betting that if you delete them you could possible void the warranty, and if anything went wrong you would have a problem resintalling windows xp.

You can resize a partition to make room for ubuntu by looking here

---

### Post by yosef on 2006-11-11
I was in a similar boat not so long ago.  I had a new laptop from dell and was considering putting fedora on it at the time. There were these hidden partitions and Iwasn't sure what to do.  One partition was a restore point which, when I used it, set my system back to how it was when I got it from the stare... Dell's bundled spyware, adware, trashware etc included.  The other was for running diagnostics. I resized the partition, splitting it up and putting on fedora, I tried getting the restore point to go on the other partition after getting hit by a virus, I could not get the restore point to go on to the newly resized partition and xp was really ubuseable at that point due to both the virus which norton didn't catch and then also due to difficulties uninstalling norton. I could not get xp installation disks from the store nor would dell send me new ones... at that point to hidden partitions were useless.  I eventually reformatted the whole thing and put on kubuntu.  I hope something from what I went through can be helpfull to you.

---

### Post by d3v1ant_0n3 on 2006-11-11
I would be dubious of touching the partitioning if you ever wanted to restore windows XP. 

I had issues with reinstalling XP on this machine when I had repartitioned the harddrive. I tried the restore disks but it wouldn't work, presumably saw it as a new machine. If you have a basic (non restore type) disk of Windows Xp, and the product key, you should be ok. But you'll lose all of dells handy malware if you need to reinstall. I hate these 'built in' restore partitions.

---

### Post by yosef on 2006-11-11
I agree with you, I think its a big rip off, I paid for my computer and windows as well, but with no installation disks if something goes really wrong, as it did.  I believe there is a way of burning the restore point to a cd... If I remember correctly it was not a difficult process, and then one could delete that partitionand still keep dells malware! Yay!

---

### Post by Dr. Nick on 2006-11-11
Ugh, compaq used to put their "BIOS" (not the actual bios, just the gui to modify it) on a hidden partition, sort of a pain when someone gives you a computer but keeps the hard drive to protect the security of its contents.

Took me quite awhile to find the stupid floppy images on their site and  recreate it on a new hd.

I wish companies would just give you a Windows disk, or let you just get a computer without windows and save money.

I think they have hidden partitions since most users would never notice them until tech support showed them how to use them to reinstall, and in that case the customer would probably be thrilled for their foresight.

---

### Post by yosef on 2006-11-12
> **Dr. Nick said:**
> 
I think they have hidden partitions since most users would never notice them until tech support showed them how to use them to reinstall, and in that case the customer would probably be thrilled for their foresight.

Dr. Nick, I award you with (fanfare please) :KS A GOLD STAR!!! I believe you have hit it on the nose! I just wish that I had had the option of getting this same computer without windows and saved a chunk of cash... ridiculous[-(

---

### Post by Dr. Nick on 2006-11-12
> **yosef said:**
> Dr. Nick, I award you with (fanfare please) :KS A GOLD STAR!!! I believe you have hit it on the nose! I just wish that I had had the option of getting this same computer without windows and saved a chunk of cash... ridiculous[-(

Thanks for the :KS lol

I would even be kind enough to tell them I would never use their tech support for software issues :) 
(You can get much better advice here:KS)

I wouldnt give up the warranty though lol, saved my parents once, our 2.4ghz p4 started smoking since the fan died, smelled like burnt plastic, tech support asked "have you tried restarting it?" we then reiterated the fact that it is smoking and melting plastic to which they said they would send another one to us ASAP. 



Got lucky and got a 2.53 one lol

---

### Post by yosef on 2006-11-12
LOL!!
What country was the tech support in?  Maybe they didn't understand english?

---

### Post by Dr. Nick on 2006-11-12
> **yosef said:**
> LOL!!
What country was the tech support in?  Maybe they didn't understand english?

Heh, I forget exactly, IIRC they were here in the US since the call was made about 10pm CST; think that is early morning over in Asia.

I think they understood english, they were just following their sheet of generic responses lol

---

### Post by emdeem on 2006-11-12
If you don't want to mess with the hidden recovery partitions, do you really need both C: and D:?  Maybe you can move anything useful from D to C and then delete the D partition.

---

### Post by awhowart on 2007-05-18
I purchased a Dell 1501 in November and was having trouble with XP (big surprise), so I decided to reinstall it. For some reason the default keys for booting from the hidden partitions didn't work, so I downloaded a trial imaging software and burned a copy of the hidden drive containing the default image of xp that was shipped with Dell. I was able to reinstall xp from the burned image, no problem. You should write down your default partition sizes though, because the burned image will only burn to a partition of the same size as the default.

I plan on clearing my partitions and installing Ubuntu 7.04 this weekend! YAY! :-)

---

