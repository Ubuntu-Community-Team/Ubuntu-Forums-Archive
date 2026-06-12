---
title: "&quot;unable to satisfy all constraints on the partition&quot; on 10.04 final"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by oblivious on 2010-05-09
Hello guys,
I'm having a problem while trying to install Lucid Linx final.

When I get to the stage where I manually set the partitions, the installer says "unable to satisfy all constraints on the partition" for every new partition I create. Trying to continue the process beyond this point just brings up more errors.

I have tried using the gparted from another livecd to create free space, and selecting the option "install using available free space" but the results are the same.

I read on the release notes that the alpha/release candidate could bring such an error, and that it should be fixed in the final release.

I double checked the md5 checksum of the download, checked the cd for defects, and everything seems to be ok....
What can I do?
Thanks in advance

---

### Post by srs5694 on 2010-05-09
I've run into this error occasionally with GParted. IMHO, it's a GParted bug. I recommend you partition using fdisk (or gdisk for GPT disks) instead. You can do this from an emergency disc, such as [System Rescue CD](http://www.sysresccd.org/Main_Page) or [PartedMagic.](http://partedmagic.com/) Once you create your partitions, you'll need to create filesystems on them. In theory, you should be able to do this with the installer, but I don't know how persistent the bug will be. If you want to be sure you don't run into the bug at that time, you should be able to use mkfs on the partition(s) you create.

---

### Post by the_Ben on 2010-05-09
I'm having the same issue with Windows 7 and Ubuntu 10.4 final.  I shrunk the Windows partition using Windows, but I still get the "unable to satisfy all constraints on the partition" error when I tell Ubuntu to install into the largest contiguous free space.  Anyone know of a work-around for this?

---

### Post by oblivious on 2010-05-10
Hi srs5694, thanks for your response.
I would like to try your suggestion, however there is something still unclear: If I create and format the partitions with another CD, I will end up with someting like this (example values):
swap partition: 1024 MB
/ partition: 50.000 MB
/home partition: 70.000 MB

Will the Ubuntu installer understand/assume these empty partitions will be used for installation?

---

### Post by ratcheer on 2010-05-10
I believe it has to do with a change to the acceptable partition boundaries since Lucid Beta came out. Try changing your partitions with a **Karmic** Live CD. I am guessing that will work.

Tim

---

### Post by oblivious on 2010-05-10
> **ratcheer said:**
> I believe it has to do with a change to the acceptable partition boundaries since Lucid Beta came out. Try changing your partitions with a **Karmic** Live CD. I am guessing that will work.

Tim

My previous comment still remains... will the Lucid installer assume these empty partitions created with Karmic will be used for installation?

---

### Post by srs5694 on 2010-05-10
> **oblivious said:**
> Hi srs5694, thanks for your response.
I would like to try your suggestion, however there is something still unclear: If I create and format the partitions with another CD, I will end up with someting like this (example values):
swap partition: 1024 MB
/ partition: 50.000 MB
/home partition: 70.000 MB

Will the Ubuntu installer understand/assume these empty partitions will be used for installation?

You'll need to select the "manual partition" or "advanced partitioning" option (I don't recall precisely what it's called) and then select the partition(s) you want to use and manually set their mount points.

BTW, 50GB (I'm assuming you meant GB, not MB, for your / and /home partition sizes) is a bit on the high side for a root (/) partition when you've got a separate /home partition. I generally recommend 5-20GB for root (/). My own desktop system (running Gentoo, not Ubuntu; and Gentoo is more disk-space intensive than Ubuntu) uses about 18GB on root (/) at the moment, with a lot of software installed. I've got about 5GB in use on my Ubuntu-based MythTV system.

---

### Post by oblivious on 2010-05-10
Hello from Lucid! :)
I took ratcheer's suggestion and used an old Jaunty liveCD to create the partitions, then rebooted with the Lucid liveCD and played around with the install options until I found out how to set the mounting points for each one (as srs5694 suggested)
Big thanks to both of you!
BTW, the actual partition values were 15GB for the root partition and 50GB for the home partition ;)

---

### Post by ratcheer on 2010-05-10
Great! I'm glad I could help.

Tim

---

### Post by the_Ben on 2010-05-11
> **ratcheer said:**
> I believe it has to do with a change to the acceptable partition boundaries since Lucid Beta came out. Try changing your partitions with a **Karmic** Live CD. I am guessing that will work.

Tim

So, just to make sure I have this right; the problem lies with Lucid's partition creation?  So if I create the partition with an older version of Ubuntu, then load 10.4 into the newly created partition, everything should be gravy?

---

### Post by ratcheer on 2010-05-11
> **the_Ben said:**
> So, just to make sure I have this right; the problem lies with Lucid's partition creation?  So if I create the partition with an older version of Ubuntu, then load 10.4 into the newly created partition, everything should be gravy?

Yes, that is what worked for me and the OP of this thread. If you started with a clean system, Lucid would create and use the new partitions without problems, but the boundaries of the partitions of an older installation will not necessarily work for a repartitioning for Lucid. It is described in the Lucid release notes.

This is not a bug, it is just a change that is incompatible with older partitions. To the best of my knowledge, the change was made for compatibility with Windows 7 (and, maybe, Vista).

Tim

---

### Post by paalz on 2010-09-30
Somehow "unable to satisfy all constraints on the partition" problem disappeared after a left 1Mb of free space before the first partition
although i came across this error not during 10.04 installation

---

### Post by topet2k12001 on 2010-11-29
> **paalz said:**
> Somehow "unable to satisfy all constraints on the partition" problem disappeared after a left 1Mb of free space before the first partition
although i came across this error not during 10.04 installation

Same here; I have been observing that there's always 1MB before the whole partition whenever I install Ubuntu (started using Ubuntu in 10.04). I somehow ran across the same error today and your message reminded me of that 1MB observation. Thanks!

---

### Post by TheCat on 2011-02-13
> **ratcheer said:**
> I believe it has to do with a change to the acceptable partition boundaries since Lucid Beta came out. Try changing your partitions with a **Karmic** Live CD. I am guessing that will work.

This worked for me.  Thanks.

---

