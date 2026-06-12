---
title: "How to use the second HDD in ubuntu?"
date: 2017-05-24
forum: Installation &amp; Upgrades
---

### Post by enjel3 on 2017-05-24
Hi!
First I want to apologize for my bad English

I have installed Ubuntu Server 16.04 with 6TB of HDD.

[img]http://i.imgur.com/2rB5NgS.png[/img]

But when I install ubuntu only one disk appears and very partitioned.

[img]http://i.imgur.com/Cbx9LUd.png[/img]

I need the 6TB in /home , how can I do it?


Thank you very much.

---

### Post by TheFu on 2017-05-24
Please copy/paste text, not images.  Images are a waste of bandwidth for people paying by the bit to access these forums. It also makes it hard for me to provide exact lines back to you.

Appears you are using software RAID.  There are 3 different RAID devices - md2, md1, and md3.
If you will run the **boot-info** script that my signature links to, maybe we can see what is happening. As it is now, cannot see enough details to know what is  happening.

If it really is RAID1, then I think we've found the storage:
md2 - 1TB
md3 - 1.7TB
md1 - 500MB

So, that means 2.8TB is being used. Thanks to the difference between 1024b and 1000b that storage people use and formatting overhead, the numbers add up to about 3TB of mirrored storage.  A quick look at
```
$ more /proc/mdstat
```
should confirm the RAID being used. Please copy/paste and use "code tags" like I did for the command so things line up and are readable.

---

