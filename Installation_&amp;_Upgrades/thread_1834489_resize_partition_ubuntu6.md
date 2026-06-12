---
title: "resize partition ubuntu6"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by waderedsox on 2011-08-27
hi guys I'm trying to install ubiuntu alongside windows 7 and I am running into a snag the option to resize my hard drive partition is not showing up I have tried 10.4, 11.4, and bt5 including 64 and 32 bit versions I am sure there is an explanation any ideas would be appreciated I have checked all through the manual mode and can not do anything other than format or delete I suspecting it must be detecting something wrong with my drive or something any ideas?

---

### Post by saltmarshlamb on 2011-08-27
How many partitions do you already have? 

From the livecd, open a terminal and run 

```
sudo fdisk -l
```

if you're not sure.

---

### Post by waderedsox on 2011-08-27
just 1 plus the w7 100mb odd partition forget what its called

---

### Post by dino99 on 2011-08-27
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by saltmarshlamb on 2011-08-27
Most of the W7 systems I've seen on here have had 4 partitions. Perhaps you post a screenshot of the partitions shown in the W7 disk management tool or from gparted in the livecd. 

Don't use the livecd partition editor to do any disk management in w7 though, use the w7 disk tools.

---

### Post by waderedsox on 2011-08-27
ok I'll get a ss the reason I was trying to use the ubuntu partition manager was because it makes it really east to set up exactly the right partitions easily

---

### Post by waderedsox on 2011-08-27
here are the screen shots

---

### Post by waderedsox on 2011-08-27
gparted

---

### Post by Hakunka-Matata on 2011-08-27
right, you need to boot into win 7 and use it's Disk Management tool to shrink sda2, and create unallocated space to be used for the Ubuntu installation.
Defragment the drive first, and reboot into windows after defragging at least once before shrinking.
Win7 recovery disk(s) - have?  Win7 - important data backed up?

---

### Post by saltmarshlamb on 2011-08-27
you also need to deal with whatever errors are on the ntfs drive - the reason it's causing an issue is the ! flag on the sda2 drive

---

### Post by Hakunka-Matata on 2011-08-27
[http://ubuntuforums.org/showthread.php?t=1683627&highlight=shrink+windows+7](http://ubuntuforums.org/showthread.php?t=1683627&highlight=shrink+windows+7)
The above thread talks about how - why - dangers - etc. in relation to shrinking win7 partition.

@[saltmarshlamb]("http://ubuntuforums.org/member.php?u=1418432");  sorry for jumping in, it seemed pretty obvious where he had to go at this point.

---

### Post by saltmarshlamb on 2011-08-27
> **Hakunka-Matata said:**
> [@[URL="http://ubuntuforums.org/member.php?u=1418432"]saltmarshlamb](@[URL="http://ubuntuforums.org/member.php?u=1418432"]saltmarshlamb);  sorry for jumping in, it seemed pretty obvious where he had to go at this point. :)

The OP still has some errors of some sort to deal with on the ntfs drive - but as far as I can see we all wander about helping where and when we can so no apology is needed.

---

