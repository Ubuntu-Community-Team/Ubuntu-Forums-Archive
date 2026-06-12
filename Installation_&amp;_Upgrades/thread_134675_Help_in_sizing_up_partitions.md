---
title: "Help in sizing up partitions"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by Duneatreides on 2006-02-22
Hello all,

I am going to give Ubuntu Linux a test run, and I am interested in creating a dual-boot setup,  but am unsure of what size each partition should be.

I guess it would be helpful to know what system I am using to dual boot.
Model: Dell Dimension 4100
CPU: Pentium III 800 Mhz
RAM: 512 Mb
Storage: 30.0 Gb
Current OS: Win98SE

I am currently in the planning stages and this will be a weekend project.  I came across this from the Linux Documentation Project  [http://www.tldp.org/HOWTO/partition/requirements.html](http://www.tldp.org/HOWTO/partition/requirements.html) , and based on that I came up with this tentative scheme.

Windows 98SE: 10.0 GB
Swap: 1.0 GB

Now I am unsure of the rest.

/(root): What size should I make the root?
/usr : What size should I make /usr?
/boot: What size should I make /boot? Do I need a /boot partition?
/tmp: What size should I make /tmp? Do I need a /tmp partiton?
/home: What size should I make /home? 

And the last questions of all? What exactly are these partitions for? I know that the /(root) partition is the *required* partition, but what about the others?  What are some good, security conscious recomendations for sizing up the partition?

Any advise would be very helpful.
Chris

---

### Post by heimo on 2006-02-22
I'd create just two partitions for Ubuntu + swap.  ~6GB for /, 768MB or 1GB swap and rest for /home. For explanations what these partitions / parts of file system are for, see:
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by cotcot on 2006-02-22
I only have / (root), swap (2xram) and a vfat partition for data share between ubuntu and xp. In case of repartitioning i would make ext2 instead of vfat.

---

