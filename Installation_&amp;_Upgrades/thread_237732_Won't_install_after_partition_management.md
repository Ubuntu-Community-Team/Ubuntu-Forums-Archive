---
title: "Won't install after partition management"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by hAvAAck on 2006-08-16
Okay, I've been trying for 2 days now to try to get past all the problems I've been having in just attempting to install Ubuntu. At this point I can finally get the CD to boot up, get to the partition management, and click "install"
It hits 15% of "installing system" and it just drops right off the screen. Nowhere to be found. It's like I just booted up the live cd.
I think it might be having trouble with the way I'm trying to partition it because I get errors stating "unrecoverable errors in XXXX FAT16 partition. Go back? Ignore and continue?"
I'm set up like this

**Maxtor 40G HD**
part1= 36MB (something Dell put in)FAT16 
part2=nearly 40G has Windows XP on it NTFS
**WD 120G HD**
part1= 36MB (dell) FAT16
part 2= 36G root (linux) partition (ntfs is the only option it gives)
part 3= 2.5G Swap (linux)
part 4= nearly 80G of data (ntfs)

It apparently finds errors in the FAT16 partitions, I've thought about just deleting them but I have no idea what they're doing.
I also thought I needed to mount the linux root on a FAT32 partition, but the linux installer partition thing wants to format it to NTFS

I'm confused as to what the problem is. My aim is to dual boot XP and Ubuntu. I don't want to touch my 80G data-only HD

Yours 100% Newbly,
hAvAAck

---

### Post by zxee on 2006-08-16
It sounds like you haven't actually chosen a partition for ubuntu to format and install to. There's a lot to read in the dapper how to but you might want to look at how to create a partition; [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
I usually do manual partitioning-you can always open a shell (Alt+F2) and type cfdisk hdb and see if you can use that. It's not really hard it just takes getting use to. I'm presuming you have IDE drives. It looks like your WD 120 is the drive that you want to create a partition for linux on.
Linux won't install to NTFS. So try cfdisk and if you have problems let us know what they are.

---

### Post by hAvAAck on 2006-08-16
I just actually figured it out. What I had to do was set up my 2nd HD like this
part 1: 38g linux root (ext3)
part 2: 2g linux swap 
part 3: 80g data (ntfs)

It was having a real problem with the FAT16 partition, so I just completely deleted all of the partitions and started new with that configuration. Once I did that it allowed me to install linux on the etx3 partition, which was different than before when it would only format it as ntfs.
Thanks for the help!

---

