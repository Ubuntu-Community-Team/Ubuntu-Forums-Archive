---
title: "Installing w/multiple SCSI drives?"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by lwalker on 2006-03-28
Being a total *nix newbie, before attempting an install, I did a fair amount of homework on partitioning.  I have three SCSI drives each of 4.5 or so GB, and am doing a completely new install (that is, no dual-boot, no holdovers at all).  I had decided on this scheme:

First Drive:
--------------
/boot    = 80 MB (ext3, Primary, bootable)
/           = 100 MB (ext3, Logical)
swap   = 384 MB (swap)  [system RAM = 128 MB, this is 3x]
/var     = 1 GB (Resier, Logical)
/tmp    = 776 MB (Reiser, Logical)  [just comfortably over the 650 MB of a CD]
/home = 2 GB (Reiser, Logical)  [actually, balance of space, c. 2.2 GB]

Second Drive:
-------------------
/usr     = all (Reiser, primary)

Third Drive:
---------------
/usr/local = all (Reiser, primary)

OK, I get to the partition step in the install.  The installer sees all three drives just fine.  I erase all my existing partitions.  I set up the partitions exactly as specified above (I say "exactly" but the installer tweaks the exact sizes to suit its eccentric tastes, but they're pretty close).

Install proceeds, gets to the remove-CD-and-reboot stage.  Goes on from there, and halts mid-stream with a "no disk space left" error.  Force it to continue, get to a terminal session, and see almost nothing on /usr or /usr/local, but root filled to 100%.  That *looks* like the installer puts everything under root no matter what other filesystems exist; can that possibly be so?

OK, I try this again a couple of times (I have a hard head).  Same basic issue.  Finally, I give up and decide to let the installer do the job itself.  But no sooner do I click on "Erase first drive" (or whatever the exact wording is) than off it goes, apparently paying no attention to the other two drives.

I do end up with a working system; that's nice.  But I have 9 GB of fast SCSI drives that I might as well be using for doorstops.  Here is what the system shows me:

/dev/sda1  ext3    /          4.04 GB, c. 51% used
/dev/sda5  swap  swap  212 MB

/dev/sdb1  Reiser  unused  4.24 GB

/dev/sdc1  Reiser  unused  4.24 GB

Swell: the kindergarten everything-in-root system.

Surely there is a way to do this correctly.  I do not want to start customizing the system in any way till it's set the way it's going to stay; but I *need* to be able to use it asap.

Please, someone, what should I be doing here?  (I don't mind doing a whole reinstall, but not numerous whole reinstalls if that can be avoided.)

Thank you.

---

### Post by Swab on 2006-03-30
You have 100MB for your root partition.  That's just not enough... even with your /usr partition.  My /lib folder takes up over 200MB.

---

### Post by hw-tph on 2006-03-30
I second Swab in that a 100MB root partition is too small. Also, I suggest using LVM so you can reallocate space as needed. 2GB for /home might not be ideal in the long run - then grab some space from /usr/local, or whatever.


Håkan

---

