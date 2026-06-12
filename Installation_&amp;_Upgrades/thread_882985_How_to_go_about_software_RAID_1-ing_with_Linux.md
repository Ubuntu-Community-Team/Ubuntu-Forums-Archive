---
title: "How to go about software RAID 1-ing with Linux?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Totakeke on 2008-08-07
I just wiped my hard drives (accidentally of course :-P) and I figured it would be good to try a clean install of Ubuntu. Unfortunately, I'm lost when it comes to partitioning, and I can't even find where to RAID 1 my hard drives. So my questions are:

A lot of guides on the internet say to set the drives are RAID instead of ext3 journaling or something. I, however, don't get the RAID option at all, I can't find it. In fact, my installation never even gets me to Linux, all I get is a command prompt after booting. (Which tells me I probably didn't partition correctly.)

Also, what directories should I create partitions for and generally what size should they be? I have two 250 GiB hard drives (mirrored, eventually) so space isn't an issue. I plan to do some gaming (Linux permitting :-P) and programming, so I need a lot of place to put stuff.

Thanks.

---

### Post by tamoneya on 2008-08-07
do you plan on just running linux on this system or do you plan on dual booting?

---

### Post by NickZA on 2008-08-09
Hi Totakeke

This is a superb guide I have used a couple of times now (under 7.10 and 8.04): [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

However that's for RAID-5 but the process is almost identical, just follow his steps BUT replace these commands in his tut with mine, below:

```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdx1 /dev/sdy1
```
...substitute your volume names in for sdx1/sdy1.
and also where he says to edit your fstab use this line instead (for a 2 disk array)
```
/dev/md0 /media/yourdiskname auto defaults 0 2
```

Note his guide doesn't tell you how to remove the RAID if it ever needs to be (eg. you decide to change your setup). I have *just* posted a new thread in this regard, here:

[http://ubuntuforums.org/showthread.php?p=5553360#post5553360](http://ubuntuforums.org/showthread.php?p=5553360#post5553360)

(can be useful if you duff something and need to clear up your RAID settings to start anew)

Have fun! :popcorn:

-Nick

---

