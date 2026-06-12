---
title: "Recommendation for installing when there are already 4 partitions"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by dugh on 2011-03-15
I got a laptop that I'd like to install Ubuntu on (I've done this numerous times before).  But this one already has 4 partitions on it, and the Ubuntu installer complained that you can't have more than four.  I know you can make a logical or whatever partition that holds others sub-partitions, but I'm not sure the best way to do it without destroying data from the other partitions.

The existing partitions include: a recovery partition, the primary windows partition (large size), a small boot partition, and a special partition for hp software that can run without booting windows.

Can I convert the windows partition into a logical partition or something like that which can be divided up, without wiping out the windows files and data there?

And yes I know I can use the wubi installer, but I prefer a more permanent solution (Ubuntu is my primary OS, but I don't want to wipe out Windows at this point).

Thanks for your help

---

### Post by Skaperen on 2011-03-15
Unless there are appropriate gaps in just the right places and sizes, you cannot create logical partitions without first backing up data to another storage device (or 2, as usually recommended).  But in all cases when changing stuff on a disk, making backups (plural) is always a very good idea.  In your case, after making at least 2 backups, you can change one of the partitions to the extended type, and proceed to slice it up into 2 or more logical partitions.

Well, OK, there is one case where backups are not needed ... when you just installed the OS to an empty drive and are looking for an excuse to do it all over again :)

---

### Post by oldfred on 2011-03-15
You should leave the hidden in windows 100MB boot partition and the windows main install. You then have a vendor recovery & a vendor utilities partition that may or may not be useful.

The vendor recovery should let you write the files to a set of DVDs to allow you to recovery your system. Make two if it lets you and a repair CD. But then it has little use and can be deleted. Realize that the recovery just erases drive and writes the image back to the way it was when you purchased system. (not to useful in my mind anyway).
If you have spent a lot of time updating windows I would back up an image and use that as a real recovery.

They other partition is usually vendor utilities. This is usually a small partition which you can backup and restore (if you want). 

Only if you have some sort of non-standard system that boots special files would you not be able to do above.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by dugh on 2011-03-15
Thanks, yeah, I'm going to backup the recovery partition and use that to install ubuntu (after shrinking the windows partition and expanding the recovery partition using the partition editor)

Appreciate your help

---

### Post by srs5694 on 2011-03-15
> **dugh said:**
> Thanks, yeah, I'm going to backup the recovery partition and use that to install ubuntu (after shrinking the windows partition and expanding the recovery partition using the partition editor)

That's what I'd recommend (if by "recovery partition" you mean the ~15GB partition that HP provides instead of physical recovery media). One caveat: Windows is very picky about its boot partition. In particular, if its start sector changes, Windows will probably refuse to boot. Depending on the version you use and what options you set, GParted will sometimes move the start sector of a partition even if you don't ask it to do so. Thus, if you resize your Windows boot [noparse](C:)[/noparse] partition, I recommend doing so using the Windows partitioning tool, which is more likely to do this safely. If even that messes it up, you'll just have to use those recovery DVDs!

---

### Post by gordintoronto on 2011-03-15
See also, Issue 41 of Full Circle Magazine, page 36.

---

