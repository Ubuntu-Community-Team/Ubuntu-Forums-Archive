---
title: "NTFS partition"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by ngms27 on 2005-11-08
If I have a 160GB disk with a single NTFS partition can I install Ubuntu straight from the CD?

i.e. Do the partition tools on the install CD shrink NTFS partitions?

If not are there any Linux freebies that will do the job?

Thanks

JonnyT

---

### Post by earobinson on 2005-11-08
the partitition tools should be able to shirnk ntfs, if they can not you could always dl a demo of partition magic to do it.

always backup your important data before you partition

---

### Post by Cufishing on 2005-11-08
It would not work for me. I had to follow the guide. That did not work either, so I had a pretty clean, fresh HDD to work with.
Here is the guide:
[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29)

Do not trust anything, and heed the warning. Back up all your important data to off drive source.

I read and followed an example, I cannot find the link at the moment.

Anyhow, a new large drive could look like this.
Part 1: Win=NTFS
Part 2: Music=Fat32
Part 3: Photo's, movies whatever,=FAT32
Part 4: Linux
Part 5: Swap

Or whatever fits your ideals.

This way, you can store all of your foavorite stuff, and be able to access it from either OS.

Good Luck.

---

### Post by earobinson on 2005-11-08
did you try my second idea using a demo of partition magic? Im sure I used to do this all the time when i ran windows

---

### Post by corruption on 2005-11-08
I'm gonna have to agree with earobenson on this one... I've never found anything that can reliably resize an NTFS without corrupting some data on the drive other than partition magic... a few months back, when I finally gave up on windows altogether, I used partition magic in conjunction with gparted to convert a 120gb ntfs partition, half full of data, over to an ext3 partition, 60gb at a time.. (reduce 60.. convert to ext3.. move remaining data.. convert 2nd portion.. gparted to recombine as a single partition)

My only recommendation is that before you run this, you run a defragging tool under windows, especially if theres anything mission-critical on the drive.

---

### Post by earobinson on 2005-11-08
Im sure there are other just as good tools out there, but since my switch (3 ish years ago) Im out of touch on the latest and greatest windows apps

---

### Post by LuxoDave on 2005-11-08
Disclaimer- I have only used Ubuntu for a few days.

But, when I installed Ubuntu, I was able to change the size of my 80 gig NTFS drive (with Windows XP) to 40 gig, and a new primary for Ubuntu and a swap drive as well. I can boot into both OS's now. 

Maybe I misunderstood the question?

---

### Post by earobinson on 2005-11-08
[QUOTE=LuxoDave]Disclaimer- I have only used Ubuntu for a few days.

But, when I installed Ubuntu, I was able to change the size of my 80 gig NTFS drive (with Windows XP) to 40 gig, and a new primary for Ubuntu and a swap drive as well. I can boot into both OS's now. 

Maybe I misunderstood the question?[/QUOTE]
no i think you are right, in my first post i said that the partition tool should be able to do it, but if not use partition magic.

---

### Post by jdong on 2005-11-08
Most of the times, the Ubuntu installer's resizer should be able to shrink NTFS volumes. However, this is a **very conservative** tool, and will refuse if there is even the slightest hint of something abnormal. As a result, there are some drives that it probably could shrink but refuses to do so. Note that this is a reverse-engineered NTFS tool, that is, MS refused to give any insight as to how NTFS works, and all of this work is a culmination of guess-and-check efforts.

Partition Magic works better at resizing these troublesome partitions.


As far as installing Linux directly onto NTFS or FAT32, there are indeed exotic ways to do so (googling will turn up Topologi Linux and other cool gadgets), but it's not a practical solution.

---

### Post by earobinson on 2005-11-09
out of intrest jdong do you know if partition magic was reverse-engineered?

---

### Post by jdong on 2005-11-09
[QUOTE=earobinson]out of intrest jdong do you know if partition magic was reverse-engineered?[/QUOTE]

No; the inner details for NTFS were licensed to the team for the sake of making PM. I 'm sure a nice legal document was involved governing the details of the partnership :)

For some strange reason, MS is cooperative when the product requires an MS product to be useful, but coldly unwelcoming when the end utility is used to switch people away from MS products ;)

---

### Post by aum11 on 2005-11-09
Does anyone know where a functional demo of partition magic can be found and downloaded?  I have googled and found only crippled versions.

Ta.

---

