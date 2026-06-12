---
title: "Try to install Linux Mint but can't shrink windows partition to make spac"
date: 2015-08-28
forum: MINT
---

### Post by philg6akk2 on 2015-08-28
Hi 

I have a new I3 pc 8gb ram and system disc is 114gb ssd. running windows 7

The live runs ok but when i go to install it can't see windows and wants to reformat SSD.

When I go to Windows the C drive has 68gb unused but the partition won't resize under windows.

C drive is GB NTFS

Any Ideas how to move ahead.

By the way have been a happy osx user on an Imac Mini since 2009 but now Apple are really mucking up things and the replacement for Iphoto is useless. I was thinking that window 10 would be the answer but that was worse than w7

I'm nearly 70 and don't want to be a command line Guru especially after my stroke hence the interest in Mint what I want is a simple interface for emails, web browsing, photo editting (already used Gimp) playing music and videos (already got music and video out of Itunes. I have an Android phone coming soon so want to link Google contacts, mail and calendar.

All suggest much appreciated

Regards

Phil

---

### Post by PaulW2U on 2015-08-28
*Thread moved to **MINT**.*

---

### Post by yancek on 2015-08-28
How did you try to resize the windows partition and what was the result.  With windows 7, the standard method is to go to Control Panel, Selecti Administrative Tools, Computer Management, Storage, Disk Management, More Actions and on the far right then click the arrow to get All Tasks Shrink Volume and select the volume here.  You mention windows 10 but your post seems to indicate you are using windows 7?

You should have the partitioning tool GParted on the Mint install medium which you can also use to do this.  You would be better off using windows tools however.

> The live runs ok but when i go to install it can't see windows and wants to reformat SSD. 

Which Installation Type option are you using?  Best bet is to use the manual method which is called 'Something Else' and will give you some control.  If you don't see any partitions when you come to the install section, I would advise stopping before you overwrite everything.  Did you check the download to verify its integrity?  I would also suggest you back up any personal data before trying to install if you have not done so.

---

### Post by philg6akk2 on 2015-08-28
when I went to the shrink option it had a zero for the amount that it thought could be safely shrunk to.

I checked another  a partition on a  different disc and it gave the amount that could be safely shrunk as a non zero amount, several gb in fact

---

### Post by yancek on 2015-08-28
> when I went to the shrink option it had a zero for the amount that it thought could be safely shrunk to.


Was that using windows Disk Management tool?  Usually, windows won't shrink to less than half the size it is.  I don't really use windows so don't know what the problem is.   Can you boot the Linux Mint DVD and get a terminal open?  Then type the following command to get drive/partition information to post here so someone can suggest something:

```
sudo fdisk -l
```That's a Lower Case Letter L in the command.  

You could probably resize with GParted.  No guarantees with that and I would back up and important data before messing with the partitions.

---

