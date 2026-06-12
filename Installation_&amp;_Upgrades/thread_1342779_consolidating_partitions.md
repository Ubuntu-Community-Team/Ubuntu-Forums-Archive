---
title: "consolidating partitions"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by lostinxlation on 2009-12-01
hi,
My laptop PC has a lot of paritions that are remainings from Suse8.2 which has been there. Since Suse8.2 became flakey lately, I decided  to replace Suse with Xubuntu9.10. I want to take this opportunity to consolidate some small partitions and make the structure a little bit cleaner.  I saw the options to split the partition in Xubuntu installer, but I couldn't find the option to consolidate multiple partitions.
 
Not sure if I missed anything in the menu, but could anyone tell me if I could consolidate the partitions on Ubuntu installer ?
 
thanks

---

### Post by howefield on 2009-12-01
Boot up with the live cd and use gparted to consolidate your partitions.

But you don't want to get it wrong and end up with a machine that won't boot, if you post a screenshot of what you currently have, (from gparted) it might make it easier to give you advice.

Sorry, just re read your post, have you installed xubuntu yet ?

---

### Post by darkod on 2009-12-01
Just to add, you probably didn't see option to expand/consolidate partitions if you never deleted any.
Existing partition can be expanded into free unpartitioned space in front or behind it. Use Gparted and look at your current situation very carefully. Then sit down and if you need to even draw on paper how you like to change it, what you want to end up with. Which partition to delete, that will create unpartitioned space, and how to expand others. But the free space has to be immediately next to the partition you want to expand, watch out for that.
After you finish your planning you can use Gparted again and do the operations.

---

### Post by lostinxlation on 2009-12-01
Thanks !!
 
I have already started Xubuntu installation with preliminary partition  structure.  Will repartition with GParted once  installtion is completed.

---

