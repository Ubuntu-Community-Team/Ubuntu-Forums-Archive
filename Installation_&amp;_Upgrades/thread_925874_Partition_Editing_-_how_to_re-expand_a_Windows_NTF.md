---
title: "Partition Editing - how to re-expand a Windows NTFS partition?"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by jvin248 on 2008-09-21
I have one machine that I've used for a while (Ubuntu 6.10 through 8.10 on it)... I minimized the Windows XP NTFS partition to expand the space for Ubuntu.  Now I have a need to re-expand the NTFS partition (putting Ubuntu on a different machine), so I imaged/"ghosted" the drive over to a spare one, then used GParted (on 8.04.1 liveCD) to minimize the Ubuntu partition and expand the Windows XP NTFS to fill the extents of the drive. 

GParted shows the NTFS partition as 70GB and the used space as 14GB, as intended.  When I boot Windows XP and launch Windows Explorer within this partition, it shows only 14GB drive size that it had before the 'expansion'.

Any suggestions for fixing?  I've tried "chkdsk /F" and defragmenting from Windows, a Windows based partitioner to nudge the size a slight amount to see if that would fix, and nothing so far.  Been too long away from Windows so I've exhausted the ideas I've come up with.

Thanks!

---

### Post by Pumalite on 2008-09-21
Try Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by caljohnsmith on 2008-09-21
Boot your Windows Install CD, go into the recovery console by pressing "r" at the first menu, and try the following commands:
```
fixboot
chkdsk /r
```
If I remember correctly, you need to make sure you use the "/r" option (which implies also the /f option) with chkdsk or it won't actually fix any errors. If after doing those commands Windows still doesn't recognize its larger partition size, you can use "testdisk" from the Ubuntu Live CD to help fix it, but try the above first and let me know how it goes.

---

### Post by jvin248 on 2008-09-22
Thanks for the suggestions! 

I don't have the Windows install or repair CD's (I repaired a scrap machine).  I'd used the liveCD and Gparted to resize the drive first before trying the other methods.

In between trying things last night I remembered I had a backup drive image - which I had from before the Ubuntu install and 'ghosted' that over the problem drive.  That finally worked, and even resized the partition correctly during the copy phase.

Again, thanks! : )

---

