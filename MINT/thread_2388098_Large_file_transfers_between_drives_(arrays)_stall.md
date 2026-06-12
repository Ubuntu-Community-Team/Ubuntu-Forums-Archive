---
title: "Large file transfers between drives (arrays) stall out - then receiving drive locks"
date: 2018-03-28
forum: MINT
---

### Post by marcerickson on 2018-03-28
Running Mint 18 Sarah on a Dell Poweredge 1800 server.  There are three RAID 1 arrays, each is two 1 terabyte drives.  They show as 3 separate drives to the OS.  The RAID card is a Dell 6 - Channel CERC SATA Dell Part #342-0056.  I include this info if needed.  I don't think it's a factor in the problem, as the file transfer worked normally when I have Ubuntu 13 or 14 on it.  But hey - maybe I'm wrong.

When trying to transfer large files between two of the drives (arrays), the transfer keeps dropping speed at a slow rate until it's moving at 3 to 4 MB per second.  Speed then starts increasing until speeds of 45 - 50 MB per second are attained.  This repeats until all of the files are transferred.  Files are between ~200MB and ~1.2 GB in size.  The filesystem is ext4.

If too large a quantity of files is transferred (more than 10 GB? It's hard to say - there doesn't seem to be a hard limit), this surging continues until, for some reason, the transfer stops. "Error splicing file.  Input/output error."  Then all files on the receiving drive (array) are locked.  If I reboot, the locks are erased.

Maybe it's related to this issue?  [https://ubuntuforums.org/showthread.php?t=2387876](https://ubuntuforums.org/showthread.php?t=2387876)

---

### Post by TheFu on 2018-03-28
How are the transfers performed?  Exactly what program is used?
I use rsync all the time for stuff like this.  Whenever things get slow, it is because of issues:
* bad cable
* bad power
* failing controller
* failing disk(s)
* bad RAM

So, if you see this on all three sets of disks, it isn't a single bad cable.  Look at the logs for hints on the exact issue.
I don't know what "locked" means. I've never seen that, but if it means remounted read-only, then I have seen that on a disk which was about to fail.  It was an SSD and eventually, it failed completely and became useless.

With anything related to storage, be certain you have automatic, daily, versioned, backups. We don't get to choose when failures happen. All disks fail.  That is their goal in life, to fail.

---

