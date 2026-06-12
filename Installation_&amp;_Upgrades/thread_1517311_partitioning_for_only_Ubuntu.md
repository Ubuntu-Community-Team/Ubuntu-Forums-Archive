---
title: "partitioning for only Ubuntu"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by mblanco2000 on 2010-06-24
I know there are alot of tips and hints out there for partitioning, but it seems most of the ones I am finding are for dual boot systems.

I am setting up a single boot ubuntu 10.04 machine.  This is my first install w/ ubuntu and just need a bit of guidance on the situation.  I read from a previous post most people use a third party partitioning tool like parted magic.  So I downloaded it but need advice on how to set up the disk partitions.

I understand swap should be approx. twice my ram amount, which is 4 gigs.  The hd I have is 750 gigs.

---

### Post by psusi on 2010-06-24
Plop in the desktop install cd, boot up, guided - use whole disk, done.

---

### Post by oldfred on 2010-06-25
Swap only needs to be slightly larger than RAM if you  want to hibernate. With 4GB you should not use swap much if at all. You would have to do video editing or run every application at once to use swap.

With that size hard drive I like to have several partitions, but it totally depends on what you are planning on doing. At the minimum I would make a 25GB / (root) 4+GB swap and make the rest /home. 

If you are planning on extra partitions for additional system installs then you may want to leave space unallocated for future use, or add addtional 25GB for additional roots. Possibly a partition for data to share if using multiple installs. Would you ever go back and want windows. Then be sure to leave a primary partition available. You have 4 primary or 3 primary and a extended that can hold a lot of logical partitions.

---

