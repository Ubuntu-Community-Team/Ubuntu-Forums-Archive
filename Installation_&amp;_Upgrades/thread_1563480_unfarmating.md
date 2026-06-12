---
title: "unfarmating"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by sukumarreddy on 2010-08-29
Hi friends,

              Today my friend has instaaled ubuntu 10.04 by replacing 9.10 vertion. By doing this, he lost his entire HDD data and all the drives are combined.

Is there any way to help him. (UBUNTU 10.04 is working)

---

### Post by Rubi1200 on 2010-08-29
What exactly do you want to do?

If he installed 10.04 over 9.10 (replacing it), the data is lost.

Perhaps, you could ask him to run this command in the terminal:
```
sudo fdisk-l
```
Lowercase L not 1
so we can see how the drive is partitioned.

Thanks.

---

### Post by sukumarreddy on 2010-08-29
It shows 1 single drive(File System) of 250GB

---

### Post by Rubi1200 on 2010-08-29
I think it is almost certain any data from the previous version is gone.

You could take a look at the options here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
but the chances are quite slim.

In the future, your friend should make regular backups of important files before doing things like this.

:)

---

### Post by srs5694 on 2010-08-29
It's conceivable that [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) could recover some files from the old installation; however, I wouldn't hold out much hope for getting more than a handful of files -- and most of those would probably be uninteresting system files rather than user data files.

In addition to maintaining separate backups, I recommend creating a separate /home partition. This practice won't completely eliminate the possibility of data loss (nothing is 100% certain to do so), but it does make it less likely that a re-installation will trash user data.

---

### Post by varunendra on 2010-08-30
> **srs5694 said:**
> In addition to maintaining separate backups, I recommend creating a separate /home partition. This practice won't completely eliminate the possibility of data loss (nothing is 100% certain to do so), but it does make it less likely that a re-installation will trash user data.
+1
Or even better, as oldfred (one of my favorites :)) suggested [here]("http://ubuntuforums.org/showpost.php?p=9766755&postcount=9"), create a separate /data partition instead.

For recovery of files (if there are some really important ones he wants to recover) try Testdisk or PhotoRec (basically test disk, just enhanced for recovery of photos/images). I believe they may have a good chance of recovery if they were not fragmented (rare in linux) and were located in a partition other than where 9.10 was installed.


**_EDIT_:**
One more thing if you are concerned about the recovery thing. **DO NOT USE UBUNTU that is installed on your harddisk!** The more you use it, the less would be chances of recovery. Boot from a live CD like [SystemRescueCD]("http://www.sysresccd.org/Main_Page") and store recovered files in an external media like a USB flash drive or a USB harddisk.

Bottomline is: Do not use the harddisk until all the recoverable data is recovered on some external media.

---

