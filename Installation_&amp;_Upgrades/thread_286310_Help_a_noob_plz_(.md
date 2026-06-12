---
title: "Help a noob plz :("
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by tehjord on 2006-10-27
Yoyo Wassup

First time trying unbutu out, here is my problem
I got 2 hd, one for windows and an other one I wanna use for Linux + a storage partition for music and stuff that both linux and windows can read in.

First Is that possible ? 
If so than how must i partition my hd, (primary extended ?) im kinda lost. Also what kind of partition do I need for linux, im not sure because there are different kind (swap boot root) anyone could help me plz

---

### Post by DaveBorealis on 2006-10-27
It's possible.

For the Linux make a root ('/') partition of at least 3 Gigs, and the kind can be ext3, although it can be one of the other Linux filesystems.  Then make a swap partition.  (The usual advice is 2X the size of your RAM...it's an outdated piece of advice, but if you don't know what size swap I'd use that as a guide.)  Make a third partition to be one of the Microsoft formates, probably best to go with fat32.  The fat32 partition can then be mounted by both Linux and Windows.  You can put this partition on either disk.  And then you'll dual boot between the two.  Unfortunately you'll have to run the operating systems one at a time.

Best regards,
Dave

---

### Post by tehjord on 2006-10-27
I forgot, I already have a primary partion that use all the disk space for storage, must I format it and change it to extended partition ?

---

### Post by DaveBorealis on 2006-10-27
> **tehjord said:**
> I forgot, I already have a primary partion that use all the disk space for storage, must I format it and change it to extended partition ?

If that's the hard drive that you want to put Ubuntu on, then you'll have to reformat (losing ALL the data on it!), and your partitions for the ext3 and fat32 will be primary partitions.  I usually make swap a primary partition, but the Ubuntu installer automatically made mine extended.

You'll want to take a look at [https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

Dave

---

