---
title: "LVM - how do I not use the whole disk?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by whit on 2008-01-24
Doing a fresh install of Ubuntu Server (latest) I'd like to have a number of LVMs. The installation routine wants to give me just one. It is less than obvious how to get this to work right - it seems like this menu is kludged together badly. It shows entries for "LVM VG ..., LV root" and "LVM VT ..., swap_1" that persist even if I deleted the partitions under them. On the other hand the option to "Configure the Logical Volume Manager" tells me I can't do that until I write the partition table to disk. Why is this the first option on the screen, when it can't be used? 

Okay, so I ignore that and go the "Configure the Logical Volume Manager" again. This time I tell it to go ahead and save my new partitions. It gives me "Error informing the kernel about modifications... -- Device or resource busy...." WTF? And it won't let me use the "Ignore" option - that just keep cycling back to this Error page. Yet if I "Cancel" I've gotten nowhere. Likewise if I just "<Go Back>".

Oh, now "<Go Back>" cycles back to the same idiotic Error page on first iteration. Then it gives me "Warning! The kernel was unable to re-read the partition table...." What's the way to use this thing to straightforwardly set up a server using multiple LVMs? 

Further into it now - the screen are coming up in very confused order, anyway I have one that shows "Current LVM confguration" that shows that the error is that it's been trying to read a "physical volume" which is one of the ones I deleted because I didn't want to have a single LVM swallow the drive. Obviously I should never have chosen the "Guided" partitioning - but when I tried to back up from that to do otherwise, the choice was gone.

If you're gonna have an installer that's this broken, you need to document it better. If it's been documented better somewhere, I haven't found it in either the official or user-generated docs. Have I missed something? I'm sure I'll get it to do what I want eventually. But nobody should have to spend hours just getting a fairly-straightforward install to use a non-default partitioning scheme.

---

### Post by whit on 2008-01-24
I've found this, which seems pertinent:

[http://www.mail-archive.com/ubuntu-server@lists.ubuntu.com/msg00264.html](http://www.mail-archive.com/ubuntu-server@lists.ubuntu.com/msg00264.html)

Note that it's a filed Debian bug with a proven fix, which Ubuntu hasn't gotten around to dealing with yet.

(I'd note though that the system I'm trying to install on has hardware RAID, not software as with this bug report.)

---

### Post by whit on 2008-01-24
Okay, after restarting the system I get to the partitioning menu on manual setup mode, and I can set up lvm partitions. But there's no obvious option to set up and format filesystems within them. Selecting one does not present any such option with its menu either. Is this just the wrong tool for the job, pretending to capabilities it does't have. Or are the capabilities hiding somewhere?

There's no way beyond this stage without having a boot partition set up, of course.

LATER: Found it. Got an option off the LVM submenu to create logical volumes, after once again saving the groups. Not sure that showed up the first time around that way.

---

