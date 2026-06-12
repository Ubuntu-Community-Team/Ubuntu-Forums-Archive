---
title: "Karmic on the Dell A2010"
date: 2009-10-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rondackcpu on 2009-10-29
A few weeks ago I reported that one of the Karmic Alphas was the first Ubuntu to show signs of working on my Dell A2010 "All-In-One".  At that time there were some small problems that kept it from being a complete success.  I can report, now, that those have been fixed and the Karmic RC is running beautifully on my A2010.

So here's a big "Thank You" to the developers. Karmic brings the end of Windows on that machine, and it refutes the idea expressed here by some that say there is little or no progress between releases of Ubuntu, and that Karmic is trash.

Here are some observations and tips for installers:

	Older releases of GParted are known to have some difficulty handling the NTFS file system.  My copy of GParted is 0.3.4-8 and way out of date.  It would not even scan the disk.  I chose to scrap Windows completely, and the partition editor in the Karmic installer was able to cope with complete removal of 'Vista' and its NTFS file system and replace it with new 'ext4' partitions (root 45GB, swap 5GB, and home 200GB).  Installation was very fast and without complications.

	The display came on at max brightness and needed to be dimmed.  The default value can be changed in <System> <Preferences> <Power Management>.  The minimum value is more than bright enough for me.

	The sound came on a bit too loud.  Using the volume applet on the top panel will reduce the volume, and the new value will be remembered.  Exaile plays my ogg files with good stereo imaging.  I assume it uses Pulse-Audio which works on this machine.

	My first impression is that "suspend" is unreliable, but the boot process is short enough that lack of "suspend" is not a big deal.  "Hiberbate" seems to work but does not save any time.

	There are several modules inserted into the kernel relating to the video card, but the video never gets to the display screen.  There must be some intermediate software that is missing, but I have not been able to determine what needs to be done.  Tvtime sees only the still camera on the display frame.  There is a "real" TV across the room, and TV on this computer has always been a low priority.

	Before I did the wipe and install thing, I tried WUBI to install Ubuntu "inside Windows".  That was satisfying enough to go ahead with the wipe, but would not have been an adequate operating mode.  Grub2 blew out several times during the experimentation, usually after a software update.

	Sorry to hear that others are so disappointed over a FREE operating system.

CRS

---

