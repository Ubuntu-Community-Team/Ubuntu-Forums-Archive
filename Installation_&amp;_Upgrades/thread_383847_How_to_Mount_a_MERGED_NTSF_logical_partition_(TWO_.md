---
title: "How to Mount a MERGED NTSF logical partition (TWO DRIVES-ONE DRIVE LETTER)"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by komputes on 2007-03-13
I'm back to Ubuntu after 4 months of being completely discouraged with 6.06 on x64. I am now using a good old 32-bit processor on what used to be a M$XP 	](*,) computer. Once I saw Ubuntu  Ultimate I was pulled back into the Ubuntuness. I just had to get rid of that crap. But I digress... I have, as many n00bs before me have and after me shall, run into my first problem which requires your assistance. I've searched for this and could not find a forum that delt with this issue. I guess you would say I'm a particular case.

**_*I do not feel like F'ing up my drives, so please no guessing, only reply if you are sure that you can solve this*_**

I have 2 360gb **Serial ATA** drives which (in windows) used to mount to one drive letter (D:, although that doesn't mean jack s - ) . What I would like to do is **mount those who disks in linux (still merged) and display the drive on my desktop** (I know that's not how you linux harcores roll, but I can't bother with dev this and dev that, i just need icons that work. I'm only a step above a monkey you know...

Advanced thanks to the genius who figured this out.
:guitar:

---

### Post by TheeMahn2003 on 2007-03-13
> **komputes said:**
> I'm back to Ubuntu after 4 months of being completely discouraged with 6.06 on x64. I am now using a good old 32-bit processor on what used to be a M$XP 	](*,) computer. Once I saw Ubuntu  Ultimate I was pulled back into the Ubuntuness. I just had to get rid of that crap. But I digress... I have, as many n00bs before me have and after me shall, run into my first problem which requires your assistance. I've searched for this and could not find a forum that delt with this issue. I guess you would say I'm a particular case.

**_*I do not feel like F'ing up my drives, so please no guessing, only reply if you are sure that you can solve this*_**

I have 2 360gb **Serial ATA** drives which (in windows) used to mount to one drive letter (D:, although that doesn't mean jack s - ) . What I would like to do is **mount those who disks in linux (still merged) and display the drive on my desktop** (I know that's not how you linux harcores roll, but I can't bother with dev this and dev that, i just need icons that work. I'm only a step above a monkey you know...

Advanced thanks to the genius who figured this out.
:guitar:

Well, I made Ubuntu Ultimate it will work no better then Ubuntu in your case as the drive(s) you have are in a "raid" configuration, the file system you use is irrelevant as it won't be picked up w/o a hefty amount of work, installing dmraid may hook you up but requires you to do editing to your fstab but if you boot from that drive you are still in the same situation, there is no easy way as of current ie one click have it all fixed now.

I also have 2 sata 320's (not 360) however not raided as well as a 250 sata I boot from, I understand the speed gain you get from raided drives in windows, I'm certain faster in linux however alot of work I don't want to do currently.  Perhaps down the road I may integrate raid support in my distro, however don't look for it anytime soon.

Incase you would like to try  with all repos enabled, in a terminal:
```
sudo apt-get install -y dmraid
```

---

### Post by komputes on 2007-03-14
Is it a RAID configuration when you just add a hard drive? Doesn't the R stand in RAID stand for redundant, meaning one HDD would have to back itself up onto the other HDD to avoid failure. Which one of these are we talking about?

    * RAID 0: Striped Set
    * RAID 1: Mirrored Set
    * RAID 0+1: Striped Set + Mirrored Set (4 disk minimum)
    * RAID 3/4: Striped with Dedicated Parity
    * RAID 5: Striped Set with Distributed Parity
    * RAID 6: Striped Set with Dual Distributed Parity
(from wikipedia)

Well anyhow I don't know what happened, I tried ntsf-config straight of the distro and it worked once but gave me an error  and then never gave me the configuration window. Then after a few updates, a few reboots and of course assing the ubuntusoftware repository in the list, all of a sudden my drive (as it was labeled in windows) showed up on my desktop. I was like:)  until I opened it to find absolutely nothing inside.:(  Trying to find out what had happened, I went into ntsf config and, it looked different (prolly cuz it updeeted duuuh) and I got this error (which I can understand - i'm not THAT dumb). 

Mounting /media/BIG DRIVE failed.

Failed to read last sector (1250274563): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?



I need to know how do I configure the tables so that they can be merged as one disk. I think you're right they might be 320GB SATA drives. My goal is to build a 620GB partition table (NTSF) which spans across two physical 320GB disks. Can you show me how to do that? In otherwords how to setup the "RAID" which had been previously taken care of by Windows Drivers which came with the motherboard (I think).

I followed your instructions and setup dmraid. anything else I have to do?if you tell me to fstab someone I wouldn't know where to start. Can you give me a knife, arum I mean... a hand... a hint.

---

### Post by komputes on 2008-02-22
TheeMahn2003 I recognize your name from the usplash script. By the way, I was wondering, what amount of work would need to be done and is there a guide available for this? I don't know if there's such a thing as a software RAID, but I think that is the case here. The data is spread across two drives which I think you can accomplish with any 2 HDD's in windows (maybe I'm wrong). Any help is appreciated!

---

### Post by frootloop on 2008-04-23
I'm looking for a solution to a similar problem myself. I have 4 drives setup in windows as one bigger drive with a single drive letter. In windows this is accomoplished by creating a dynamic disk and spanning it across multiple physical drives. I have yet to finad out how to mount the seperate drives as one linux logical drive

---

### Post by frootloop on 2008-04-23
Finally figured it out!! Going to try later tonight, will post back if successful

---

### Post by komputes on 2008-04-29
fl, i'd be impressed if you found a solution which to this day i still have an issue with. If you do figure it out please share.

---

### Post by komputes on 2008-06-15
Posting screenshot of Hardy trying to access this merged disk. I was able to search and list some files, but no use because they cannot be read.

---

