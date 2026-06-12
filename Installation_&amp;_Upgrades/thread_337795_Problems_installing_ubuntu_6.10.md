---
title: "Problems installing ubuntu 6.10"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by bear102 on 2007-01-13
Hello all,

I'm new to all things linux and was told ubuntu was one of the best (and easiest versions to install) therefore I decided to give it a go.  After watching a video tutorial on google video of how to install it i felt confident enough.

Im running windows XP pro and have 2 hard drives, both running fine.  I decided to install ubuntu to the drive only containing data that if was lost wasnt too much of a loss. (this doesnt have an OS running just data held on it).  The drive has 200GB capacity and when first attempting to install had 25gb of free space.

These are the steps I took to install it and the problems I have occured!

1. Rebooting the system and loading from CD as normal. 
2. Doing CD Check, no problems found.
3. Start ubuntu
4. Wait for it to load then click install
5. Go through the options till the partition options appear (now is where the problems start coming!)

6.  I choose the first option which automatically partitions the drive using the free space available (or at least this is what I have understood this to mean!) I leave the slide bar so that it is on the default "50%" value.
7. Click Next

Now when I click next, the computer works for a little bit then stops and stays on the same screen. So I click next again and the screen just hangs (however I can still click around and use the OS from the CD as its working.  I thought the install had crashed so I clicked cancel.  After rebooting back to windows I checked the drive and found it only had 9GB of space left on it!

Can anyone give me some idea why this happened!? And how I can sort it out?

Thanks alot!

---

### Post by Lord Landis on 2007-01-13
Well, you may wish to free up some more space on the drive you're installing to.  *EDIT - I just remembered what you said about 50%.  If you have a 200 gig drive, but only have 25 gigs free, you can't use the 50% option.  It just won't work.  You need to tell the partition editor to either use a lower percentage (like 10%) or free up at least another 80 gigs on that drive.  END EDIT*  

Normally the installer works just fine, but every so often it gets strange and you may need to set up a few things by hand.  If 6.10 (edgy) isn't working very well and you're not comfortable manually editing partition tables, I'd advise you to download 6.06 (breezy LTS) and try working from that.

If you are comfortable configuring partitions yourself, then load the live CD and do the following:

Under 'System' -> 'Administration' is an application called **Gparted** - that's the Gnome partition editor.  Use that to resize the existing windows (FAT32 or NTFS) partition on HDB (make very sure you're on HDB!).  Note that you may already see other partitions on that drive.  If that's the case, delete all non-NTFS (or FAT32) partitions before moving forward.

Next create two new partiitions in the free space.  You'll need one partition (at least 20 gb, and you should choose EXT3 as the file system) for the OS install and another (approximately twice the size of your RAM, with the Linux-Swap filesystem) for a swap partition.  Once the partitions are created, close Gparted and double-click the install icon.  When it asks you what to put where, it should default to putting / on the EXT3 partition and swap on the Linux-Swap partition.  These partitions should be named /HDB2 and /HDB3.

Hopefully this will work for you.

---

