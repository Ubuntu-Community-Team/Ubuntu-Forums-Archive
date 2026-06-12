---
title: "Cannot partition"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by corblimey on 2008-09-09
I don't think I'm destined to get Ubuntu installed on my main machine.  Every time I get as far as partitioning, but it doesn't let me resize the XP partition.  I then gParted and it gives me a warning to run chkdisk and then reboot twice.  I've run chkdsk about 5 sodding times, defragged numerous times (in safe mode) and rebooted probably a dozen times.  Every time, the error comes back up in gParted.  I'm assuming this is why the Ubuntu installer partition editor isn't let me in either.

Right now, gParted is showing:```
Partition	Filesystem		Label			Size		Used		Unused		Flags
/dev/sda1	fat32						4.97GiB		3.78GiB		1.19GiB
/dev/sda2	!ntfs			HP_PAVILION		181.33GiB	---		---			boot
unallocated	unallocated					7.38MiB
```Clicking on the ! gives me > * Warning: The disk has bad sector. This means physical damage on the Disk *
* surface caused by deterioration, manufacturing faults or other reason. *
* The reliability of the disk may stay stable or degrade fast. We Suggest *
* making a full backup urgently by running ‘ntfsclone –rescue –‘then *
* run ‘chkdsk /f /r’  on Windows and reboot it TWICE! Then you can resize *
* NTFS safely by additionally using the –bad-sectors option of ntfsresize*How would I use this -bad-sectors option in  gParted?  How does gParted know about my bad sector so quickly?  This comes up almost immediately upon starting up.  It takes chkdsk many hours - I don't know the results of the chkdsk, by the time I come back it's rebooted - if there were errors, would I know about it?

Any sort of help would be appreciated.

---

### Post by manishtech on 2008-09-09
Try checking the ntfs filesystem with this command

```
sudo fsck.ntfs /dev/sda2
```

---

### Post by corblimey on 2008-09-09
I went into 'try Ubuntu without installing' as this is the only way I can get to terminal.  ```
sudo fsck.ntfs /dev/sda2
sudo: fsck.ntfs command not found
```

---

### Post by dushkal on 2008-09-10
I'm also getting similar error. I am running chkdsk right now, but its taking lot of time. Theoretically I could reinstall Windows as its a new installation with no data on it, but just want to avoid that....
(yes, I need a dual boot machine for work related windows specific stuff....)

---

