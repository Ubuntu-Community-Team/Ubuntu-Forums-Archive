---
title: "What's best way to copy entire /home directory to 11.04?"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2011-06-08
I installed a new 11.04 on my Thinkpad in place of the old 10.10 system, so it replaced the old /home with a new empty one. But I had previously done a partition copy of the original 10.10, complete with /home to a spare HDD so now I can copy that /home in place of the new empty /home. What's the best way to do that?

Should I use 'dd'? Should I use Nautilus?

Or should I partition-copy that copy of the 10.10 onto available space on the thinkpad 11.04, then manipulate the partitions to consolidate? Maybe create a separate /home partition?

---

### Post by Mr. Shannon on 2011-06-08
I have always used Nautilus.  I have done this twice and so far my files seem to be OK.

---

### Post by dFlyer on 2011-06-08
> **bliffle said:**
> I installed a new 11.04 on my Thinkpad in place of the old 10.10 system, so it replaced the old /home with a new empty one. But I had previously done a partition copy of the original 10.10, complete with /home to a spare HDD so now I can copy that /home in place of the new empty /home. What's the best way to do that?

Should I use 'dd'? Should I use Nautilus?

Or should I partition-copy that copy of the 10.10 onto available space on the thinkpad 11.04, then manipulate the partitions to consolidate? Maybe create a separate /home partition?

I just mount the drive and drag the folders/files that I want to my home folder. I usually don't bring any of the config file over.

---

### Post by bliffle on 2011-06-10
> **dFlyer said:**
> I just mount the drive and drag the folders/files that I want to my home folder. I usually don't bring any of the config file over.

I've got 240,000 items(files and symbolic links, I guess) in the old /home, which seemslike a lot to copy if it goes one item at a time with nautilus. I worry about date stamps changing , and permissions, etc. Big data copies just worry me, especially when copying with a little program that's to copy little ordinary files.

---

### Post by Mr. Shannon on 2011-06-18
If you want to preserve the file properties then you could use
```
cp -a /path/to/backup/ /path/to/home/
```

Note: I have never done this so I am not sure that you actually want to preserve ownership of files.

---

