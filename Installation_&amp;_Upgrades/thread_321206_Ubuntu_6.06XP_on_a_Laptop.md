---
title: "Ubuntu 6.06/XP on a Laptop"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by FFfanatic on 2006-12-18
I have a laptop I want to install ubuntu on it. In order to put ubuntu on it, should I install xp on one hard drive and ubuntu on the other or should I split my first hard drive and install both on that one? If I do it all on one, is there any way I could use my 2nd HD so I could install/put both XP and ubuntu programs and files on it and use them from either OS?

---

### Post by ajgreeny on 2006-12-18
Probably simplest to install ubuntu on one drive and windows on the other.  Just make sure you install windows first (on the first drive) and ubuntu second, but again for simplicity put grub on the windows MBR.

An alternative would be to put both OS on one disk, again windows first followed by ubuntu, and then format the second drive fat32 and use it as a shared disk for all your personal files for both systems.  It will mean setting up a separate /home partition for ubuntu but there is plenty of information around telling you how to do that if it is your choice.

---

### Post by FFfanatic on 2006-12-19
With putting one on each drive, would I be able to reach into the other if say, I was in ubuntu but needed to get at something from xp? Or would the files be inaccesible since they are on different drives?

---

### Post by aysiu on 2006-12-19
> **FFfanatic said:**
> With putting one on each drive, would I be able to reach into the other if say, I was in ubuntu but needed to get at something from xp? Or would the files be inaccesible since they are on different drives?
Read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by FFfanatic on 2006-12-20
Awesome, that's what I was getting at. I'll split my 1st 50GB HD for XP and Ubuntu and I'll use my 2nd 50GB HD for virtually everything else. Thanks Aysiu. And once again, XP bows down to Ubuntu!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!111one!!!!!!!!!!!!!!!!!!

---

