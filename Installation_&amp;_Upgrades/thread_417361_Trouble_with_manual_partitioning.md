---
title: "Trouble with manual partitioning"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mjpatey on 2007-04-21
Hi, group-

I'm doing a fresh install of Feisty using the Live CD.  I've gotten to the partitioning section, and have run into some trouble...

In the "prepare partitions" step (doing manual partitioning), here are the partitions it's discovered...

hda1=ntfs
hdb1=ext3
hdb3=fat32
hdb5=swap

It's an accurate report of what's there.  The ntfs partition is where my Windows install lives, and I've chosen to keep it.  hdb1 is my ext3 partition that I wish to reformat, blowing out my prevous Feisty testing install and starting over with final Feisty.  hdb3 has always been my "shared partition" between Ubuntu and Windows, I'll be leaving it alone, and hdb5 is the Swap partition, and I just want to leave it alone, too.

When I click "Next" (or "Continue", whatever it says), I get:

> 
ERROR:

No root file system is defined.

Please correct this from the partitioning menu.


I don't know what that means, and I don't at any point see a "partitioning menu".

Anybody know what I should do?  It has brought the install process to a halt, of course.  Thanks for any help you may have!

-Mark

---

### Post by hal8000 on 2007-04-21
When the partitions are displayed highlight hdb1 and click edit. Choose this partition as the / (root) partition and tick the square box to format it. That should allow you to install.

It will install with a single partition but it is better to create a separte /home partition as well.
If you lose / you will lose your own work in /home , hence 2 partitions are preferable
HTH

---

### Post by mjpatey on 2007-04-21
I will try that!  Thank you.  It hadn't occurred to me to create a separate /home partition... that would come in handy if I want to do a clean install later without losing my stuff!

When I get home in about 8 hours, I'll try selecting sdb1 as my /root partition.  Thanks!

-Mark

---

