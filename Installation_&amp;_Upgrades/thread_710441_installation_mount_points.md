---
title: "installation mount points"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by spoolboyy on 2008-02-28
Hey guys.

I bought an older laptop (1.0ghz, 512mb, ram, 40gb hdd)  for the express purpose of running Linux and becoming more familiar with it.  I have installed openSuse and kUbuntu and tried them out deciding that I prefer kUbuntu.  kUbuntu will be the only OS on the computer.

I would like to do a fresh re-install of kubuntu (which is on the machine right now) with the following partitions:

* Swap - obviously.  
       I'm thinking about 1 gig?  any other suggestions based on my hdd size?

* OS / kernel on another partition.  
       10ish gigs for this?  maybe?

* user docs and applications in another partition (if that's possible with the programs)
       using the remainder of the drive.

My question is what are the mount points I would need to set.  I am a Windows migrant and am not very familiar with the file system of Linux.

any help would be appreciated.  I've read a few of the similar posts, but none of them (that i read) really directly answer my question.

-Adam

---

### Post by dstew on 2008-02-28
Swap is a partition type. It doesn't have a file system on it, and doesn't have a mount point. 1 Gb is fine. You just create a partition, don't bother formatting it, and designate it for swap during the installation.

Your root partition should be formatted as ext3, and given the mount point '/' (without the single quotes). I don't know about the size, but 10 Gb is probably OK unless you are going to install a ton of applications. That assumes you are going to also create a /home partition.

For your /home partition, make it as big as possible, if you are going to store a lot of data. It should be formatted ext3 and given the mount point /home

---

### Post by spoolboyy on 2008-02-28
Thanks stew.

That's what I thought the mount points should be, but every post i read either they had 8 drives in RAID 0 or they were just doing the "Guided Partitioning" like I had done before.

I ended up boosting my root ( / ) partition to around 15 gigs.  That oughta hold me in case i go application crazy.  swap at just barely over I gig.  Just in case anyone else has issues like i did, here's what i learned.

so '/'  == root file system, holds kernel, OS and apps.  leave yourself enough room here for all the programs you want, including the OS.

/home == your user space.  for your docs, music, files etc.  leave yourself enough room for all your documents etc.

SWAP - is not a storage partition, it works in conjunction with your virtual memory / memory system as a temporary storage area.

thanks.

-Adam

---

### Post by dstew on 2008-02-28
Yes, you have understood correctly. Best wishes.

---

