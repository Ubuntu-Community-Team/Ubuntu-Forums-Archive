---
title: "create a recovery partition with image of fresh install    grub???"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by tatt on 2008-01-22
Hi,

I have searched throughout and cannot find anything to assist me with this.


I install Ubuntu to many identical machines....

Is it possible to make an image of a fresh ((Updated)) install onto a recovery partition with an entry in grub which, if the worst happens, the user can use grub to reinstate the system to "as new".

Also to assist me with the installs, is there an Ubuntu version of "drive image" or one of the many other similar application so to speed up the install of these systems.


Thanks in advance

Chris

---

### Post by ugm6hr on 2008-01-22
This should do it for you:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by tatt on 2008-01-22
Thanks......

This is great for multiple installs.

How about the recovery partition....


How I would expect to see this work is...........ISH!

1..The user requires, for whatever reason, he wants his system restored to as it was new. He has no cd's or memory sticks. and no internet connection.

2. The user chooses to enter the grub boot menu on boot up where he is granted with 2 options, 1st to boot into ubuntu and 2nd to fully recover the system to factory defaults.

3. The user selects option 2, the system asks him if he is absolutely sure he wants this to happen and explains that all his data and configuration will be lost.

4. The system automatically formats the active partion and restores the ubuntu image back to the active partition.

Also the recovery partition must be invisible and locked.


Thanks again

Chris

---

### Post by ugm6hr on 2008-01-22
I have never done this, but in theory Partimage should allow something similar....

If you created a minimal Linux installation (maybe with Debian) on a partition which auto-logged in as root and ran partimage at startup, that would act as a "restore" partition.

I don't know the command-line for partimage, but it probably has a man page (or try* partimage --help* after installing it).  The startup would just run to restore a pre-allocated image (that you have put maybe on the same partition) on to a pre-allocated partition.

A small script would give you the "warning" presumably....

As for how to make the partition "invisible" - I have no idea.  Even my current Vista restore partition is not invisible (I just don't auto-mount it at startup).

---

