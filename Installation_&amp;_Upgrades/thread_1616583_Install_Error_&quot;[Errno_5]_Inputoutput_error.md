---
title: "Install Error &quot;[Errno 5] Input/output error"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by breNTx22 on 2010-11-08
"
The **installer** **encountered** an **error** **copying** **files** to the **hard** **disk**:
 [Errno 5] Input/output **error**
 This is often due to a faulty CD/DVD **disk** or drive, or a faulty **hard** **disk**.  It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed,  to clean the CD/DVD drive lens (cleaning kits are often available from  electronics suppliers), to check whether the **hard** **disk** is old and in need of replacement, or to move the system to a cooler environment."


I'm getting this when I try to install Ubuntu 10.10 64 bit on my desktop.


I've tried it 4 times. It seems to be installing now.


What i did differently:


Selected for it to use the entire hard drive instead of partitioning it myself.


Took the front of my case off and turned a fan on pointing at the CD drive. 



Why I did that:


Other people were saying the error meant there was a problem with the partition(s) and/or the CD drive overheating.






This could just be luck of the draw. Has anyone else gotten this error on Ubuntu 10?

---

### Post by cozmicharlie on 2010-11-08
I am having the same problem

---

### Post by breNTx22 on 2010-11-08
> **cozmicharlie said:**
> I am having the same problem

I suggest trying what I did.

I got it installed okay.



If I were you I would...

1) Try to keep the computer (mainly the CD drive) as cool as possible. Whether it's by having a fan blow on it or keeping it on a cold (but dry) surface.

2) If that doesn't work, try letting it use the entire hard drive (instead of manually making partitions)

---

### Post by sikander3786 on 2010-11-08
It could actually be the problem the installer itself is mentioning to

> This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.

Check if you system is not overheating. If it isn't, check the disc for defects. If you burnt the disc yourself, check the integrity of the downloaded image as well.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Try to burn a new disc at the lowest possible speeds.

Sometimes, it has been reported that changing the HDD or CD/DVD drive data cables helped.

If neither of the above works for you, you definitely need to scan your HDD for bad sectors to make sure it is in proper condition.

---

### Post by breNTx22 on 2010-11-08
> **sikander3786 said:**
> It could actually be the problem the installer itself is mentioning to



Check if you system is not overheating. If it isn't, check the disc for defects. If you burnt the disc yourself, check the integrity of the downloaded image as well.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Try to burn a new disc at the lowest possible speeds.

Sometimes, it has been reported that changing the HDD or CD/DVD drive data cables helped.

If neither of the above works for you, you definitely need to scan your HDD for bad sectors to make sure it is in proper condition.

If you're referring to me (The OP), I did none of that and it worked. I don't think it was heat related because I touched the CD drive it didn't feel warm and the OS HD has a 120mm fan blowing on it.

---

### Post by psusi on 2010-11-08
Fire up the disk utility and take a look at the SMART statistics on the drive for errors and have it run the long self test.

---

### Post by sikander3786 on 2010-11-08
> **breNTx22 said:**
> If you're referring to me (The OP), I did none of that and it worked. I don't think it was heat related because I touched the CD drive it didn't feel warm and the OS HD has a 120mm fan blowing on it.
Then you were too lucky :-) But note, every one doesn't have that much luck. Lets see what **cozmiecharlie** comes up with.

---

