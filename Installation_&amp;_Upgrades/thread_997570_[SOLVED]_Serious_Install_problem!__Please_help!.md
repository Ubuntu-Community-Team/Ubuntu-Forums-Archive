---
title: "[SOLVED] Serious Install problem!  Please help!"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Eric Qel-Droma on 2008-11-29
Okay, so I asked this whole question HERE:  [http://ubuntuforums.org/showthread.php?t=981536](http://ubuntuforums.org/showthread.php?t=981536)  And I thought I got an answer.  However, I have done exactly what was suggested:

1) Boot w/install CD
2) Run GParted
3) Delete 8.04 partition (after backing up, of course)
4) Re-run install CD to put 8.10 where 8.04 was

AND HERE's THE PROBLEM: the "select largest continuous free space" option selects the whole ****** HDD!  WTF?

I have no idea how to do this manually, and I need to keep my NTFS/XP to keep the wife happy.  The only "guided" options offered are to resize the NTFS partition or to use the whole disk.

Please help.  I'd hoped to go to bed tonight, but now...

Eric

---

### Post by It_Was_Luck on 2008-11-30
Try manually doing it...

Once you delete the 8.04 partition you just need to make that same space a Ext3 filesystem and apply the mountpoint "/" in the install. Now I don't know how much hard drive space you are working with, but you might want to possibly add in a /home partition, inside your extended partition of course. But if you're working with less than 10GB I wouldn't bother.

Cheers.

---

### Post by Eric Qel-Droma on 2008-11-30
Does it matter that the previous partition was an Ext2 filesystem and did not have a mount point listed in the partitioner?

---

### Post by Eric Qel-Droma on 2008-11-30
Apparently not.  I'm installed and everything (so far) is workable and peachy.  I have my boot menu back and everything.  The wife will hardly notice.

Thanks!

---

