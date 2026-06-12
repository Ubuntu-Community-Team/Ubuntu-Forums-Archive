---
title: "Need help in my Ubuntu install + partition."
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by taikuodo on 2007-08-14
Ok, I've installed Ubuntu, but it seems weird to me. Here are my ailments.

First of all, I used a pre sp1 XP Pro CD to install windows on my 250gb HD, so it only detected 130gb, so I should have 120 or so GB left for Ubuntu.

Now, I go to Ubuntu Live CD, install -> Manual Partition -> I make one new partition (ex3, 112 gb, mount point = "/") 

And I make a swap partition (693 mb, should probably be more anyways).

When all is said and done, i go into linux, and my sd1 drive is my WINDOWS DRIVE! Its the 130gb drive! Where did my supposed 112 gb drive go? I go to filesystems (or whatever its called) and it says it is 95gb free, but it is read only.


Am I supposed to be making different partitions?

---

### Post by merlinus on 2007-08-14
Did you navigate to /home/username?  The filesystem is ubuntu, and is read-only except for root.  You home directory is available to you for read-write.

-merlin

---

### Post by taikuodo on 2007-08-14
I see, so how do i get to /home/username?


Thanks.

---

