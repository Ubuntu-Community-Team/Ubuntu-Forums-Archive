---
title: "Not offering side by side option"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by rodericke on 2010-09-07
For some reason, I have 164 GB of free unused space that Ubuntu is not recognizing on install.

---

### Post by howefield on 2010-09-07
> **rodericke said:**
> For some reason, I have 164 GB of free unused space that Ubuntu is not recognizing on install.

What do you mean by unused, unallocated or simply spare in another partition, and what else is on the disk ?

You could boot to the desktop with the Live CD and create the partitions you need, eg one for / one for /home and one for /swap.

Then select the manual option during the install, and mount your partitions as required.

---

### Post by rodericke on 2010-09-07
There are only two partitions. One takes up 1.6GB and is Windows Recovery(loader) and the other is simply248.5GB of which 164 is available for use. Ubuntu isn't recognizing this. As far as manual partitioning, I am pretty much a noob so this is unnerving as hell. Is the side by side option no longer available. can I create my partitions using a partitioning software and then install ubuntu?

---

### Post by Hobgoblin on 2010-09-07
> **rodericke said:**
> There are only two partitions. One takes up 1.6GB and is Windows Recovery(loader) and the other is simply248.5GB of which 164 is available for use.

Sounds like that space is already partitioned.

The installer should give you the option to resize it and then install alongside Windows.

Try defragmenting the drive from within Windows a couple of times then try the Ubuntu installer again.

The other thing is, are you booting from the Ubuntu CD or running the installer from Windows?  If you've been running it from within Windows I would suggest booting from the CD and installing from there.

---

### Post by rodericke on 2010-09-07
It does not offer a resizing option or the option to install side by side. That's the issue. I'm about ready to either give up or replace windows altogether. On the other hand, if that fails then i am screwed as I have no back up discs for Vista. Oh well. I'm tired of giving the Windows guys my money.

---

### Post by andrewthomas on 2010-09-07
resize the vista partition from within windows, then try to install.

---

### Post by Mark Phelps on 2010-09-08
> **Hobgoblin said:**
>  ...Try defragmenting the drive from within Windows a couple of times then try the Ubuntu installer again.

Do NOT do this!  

Never use the Ubuntu installer to shrink MS Windows OS partitions if they are either Vista or Win7.  Doing so runs the risk of corrupting those partitions and rendering MS Windows unbootable.

With Vista or Winy, ALWAYS use the Disk Management utility to shrink the OS partition first, then allow the Ubuntu installer to use the new unallocated space.

---

