---
title: "EXT4 on top of RAID0 / RAID5... is it safe?"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by swagner74 on 2012-03-16
Hi,

_Quick question_
Is it safe to setup an EXT4 filesystem directly on top of software RAID0 or RAID5?

_Long story_
In the past, I had EXT4 on top of LVM on top of software RAID0 and RAID5, and it worked like a charm. I also had EXT3 and EXT4 on top of RAID1, and everything was smooth.

A few days ago, I installed new hardware (RAM), changed my HDs, and decided to change my RAID/LVM setup to better suit my needs. As I do not have the need for volume management anymore, I decided to setup EXT4 directly on top of RAID0/RAID5. Since then, the system has become highly unstable, keeps on crashing/rebooting randomly... Tried 12.04 beta 1 as well as 11.10 fully updated... same symptoms...

At first I suspected a memory issue, but memtest86+ tests are fine. Then I suspected a faulty HD but It's kind of hard to determine for sure, I can't find anything in logs.... I double checked my SATA cables... They seem good to me... Now, I have come to suspect EXT4 on top of an md without LVM in between... Even though reboots occur randomly, they seem to happen on disk writes to the RAID[0|5]/EXT4 filesystems...

I will revert to my initial setup RAID[0|5]/LVM/EXT4 to see if it makes a different, but I was wondering if anyone had heard of issues or warnings in this area?

Your feedback is very welcome!

---

### Post by swagner74 on 2012-03-18
Well, I am replying to myself :)

After several hours of investigation, it turned out that my problems were hardware-related (the fan on my video card was broken). I installed a new one, and sudden reboots are now gone.

So I partitioned my disks as intended originally, that is EXT4 on RAID0/5 and it works very well.

---

