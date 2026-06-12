---
title: "System Recovery, Data Retrieval?"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by qwert231 on 2005-11-14
After a failed 5.04 to 5.10 upgrade (see [http://www.ubuntuforums.org/showthread.php?t=88919](http://www.ubuntuforums.org/showthread.php?t=88919)) I get:
exec: 428 chroot: not found
Kernel Panic - Not Syncing: Attempted to kill init!

My website is on there. Any way I could save this? Maybe install again without wiping the drive? If I need to put a second drive in the system I could, but I was hoping to avoid that work.

---

### Post by yesplease on 2005-11-14
When you have a windows partition you can backup your data from windows with explore2fs (I use version 1.07), it can read ext3 (and ext2).

I read that /home wont be overwritten, when you have a separate root and home partition (perhaps you can check that information by searching the forum).

---

### Post by qwert231 on 2005-11-14
Don't have a windows drive or partition on that system, but I do have another windows system. I put explore2fs on it, and am backing up stuff off my linux drive now. (I'm on my work from home system. It's nice to have 3 :) )

When I'm done I will do a fresh install of 5.10. Thanks man!

---

### Post by dbott67 on 2005-11-14
For future reference (and for those that may be just reading through the forums looking for how to recover data from a single OS system), you could also use a "Live CD" (such as the Ubuntu or Knoppix Live CDs) to recover data without having to put the hard drive into another system.

You will need to have a device/location that you can write your data to (as well as run the LIve CD):
- a 2nd CD/DVD burner
- USB hard drive
- USB thumb drive
- FTP site
- or compress & upload your zipped data to [www.yousendit.com](www.yousendit.com)
- or lots and lots of floppy disks and lots of time! :)

-Dave

---

### Post by qwert231 on 2005-11-14
You can check out my progress and activity here:
[http://mkenyon2.blogspot.com/2005/11/current-activity.html](http://mkenyon2.blogspot.com/2005/11/current-activity.html)

---

