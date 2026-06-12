---
title: "installation stops at 15%, finding filesystems"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Eumenidesdk on 2008-01-25
When I try to install 7,10 Ubuntu from the live session it allways stops at 15%, Finding filesystems

I have waited for hours but it doesnt move on

The only harddisk in my pc is a 200 GB with about 190 GB partiton 10GB free space unpartitioned. I am trying to install it on the 10 GB unpartitioned space.

I have unplugged my XP harddisk. So no dual boot

---

### Post by overdrank on 2008-01-25
> **Eumenidesdk said:**
> When I try to install 7,10 Ubuntu from the live session it allways stops at 15%, Finding filesystems

I have waited for hours but it doesnt move on

The only harddisk in my pc is a 200 GB with about 190 GB partiton 10GB free space unpartitioned. I am trying to install it on the 10 GB unpartitioned space.

I have unplugged my XP harddisk. So no dual boot

HI and have you checked the live cd for errors and you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Eumenidesdk on 2008-01-25
I'll swap back to XP and burn a new CD after which I'll do a checksum on both CD's.

It'll take an hour or so. I'll be back.

Just to clarify, When I use XP on the other HDD I have no problems so it should not be hardware malfunction

---

### Post by Eumenidesdk on 2008-01-25
I checked the live CD for errors and also did a MD5checksum nothing wrong. Burned a new one and checked.

but it only get to 15%

---

### Post by overdrank on 2008-01-25
> **Eumenidesdk said:**
> I checked the live CD for errors and also did a MD5checksum nothing wrong. Burned a new one and checked.

but it only get to 15%

HI and what is on that drive, a OS or data? Has the drive run defrag or scandisc?

---

### Post by Eumenidesdk on 2008-01-25
I don't remember the name of the manufacturer.

But it's a 200 GB with a 190 GB data partition and 10 GB unpartitioned free space.

---

### Post by tordenalf on 2008-03-24
Hi,
Same problem here. - stops at 15%, "finding filesystems"
I choose manual partitioning
partition 1: ntfs, 17Gb, contains XP
partition 2: ext2, 19Gb, mounted as "/"
partition 3: swap, 600 Mb

---

### Post by forumjanus on 2008-05-26
Hi
My xubuntu installation also stops at 15%, Finding file systems. Nothing is wrong with the Installation CD and I have tried installing in "Safe Graphics Mode" but it always stops at 15%. 

I had Win Me on the PC before but now I can't load that either. 

Problem solved: I installed Ubuntu server edition and then wrote "sudo apt-get install xubuntu" That worked. So now I have Xubuntu.

---

