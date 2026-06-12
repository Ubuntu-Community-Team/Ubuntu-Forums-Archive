---
title: "Can't Access tty; Job Control Turned Off"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by sirskeleton on 2007-09-06
Long Story

Was working on getting a new install on a two hard disc system. I went to the windows disk manager and deleted the ubuntu partition thinking to reinstall on the window partition and use the other one for backup. Now when I try to boot from 7.04 disc to reinstall everything it says "Can't Access tty; Job Control Turned Off" Is there a way to wipe both discs clean and install ubuntu?

---

### Post by merlinus on 2007-09-06
You can use dban to completely wipe the disks of everything, and then gparted live cd to create partitions before installing ubuntu.

dban: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

gparted: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by sirskeleton on 2007-09-06
I wiped the disks of everything, but I am still getting the same error message. I'm not sure how to use gparted correctly. Could that be the problem?

---

### Post by mxg01 on 2007-09-06
Is one of the drives a slave drive?

If so then you could try making it a master. There could be an issue with installing to a slave drive.

---

### Post by sirskeleton on 2007-09-06
Tried that still no luck.  

I'm planning on trying the 6.06 version of Ubuntu later tonight, perhaps that will work.

This is really starting to bug me.:mad:

---

### Post by Pumalite on 2007-09-06
Post your specs. Let's see if we can help you.

---

### Post by sirskeleton on 2007-09-06
2x Intel Xeon 2.7, 2 gigs RAM, GeForce QuatroFx 3000, a 74 gig Seagate along with HP 34 gig. I had installed 7.04 on the Seagate with no problems before. I think the problem has something to do with wiping that drive in windows manager.

Steps I've Taken

1. Erased Drive With dban

2. Tried unpluging combinations of hard drives and master/slave configs

3. Tried booting with a floppy in the drive. (other post said it fixed it)

Nothing has worked. This is a matter of some ugency, because my father is returning from the hospital this friday and I would like to have the box up and running as a media streamer to a PS3 so he doesnt have to get up and down to change movies and such. I will be trying version 6.06 to see if it makes a difference.

---

### Post by Pumalite on 2007-09-06
The only possible problem that I can see is your video card. Have you tried the Alternate CD?. Have you been able to get a command line at all?. By the bit about the floppy I gather you have read the big thread on the subject, so there is nothing I can add to that. Have you tried all the possible fixes?.

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by sirskeleton on 2007-09-06
It seems that putting in the 6.06 disc solved the problem. I was able to install it onto the disk. Thanks for all the help Pumalite and merlinus. :) This whole error seems like one of those everything works for everyone kinda problems.

---

### Post by Pumalite on 2007-09-06
Magic! Ain't life great!!

---

### Post by merlinus on 2007-09-06
Amen, bro!

Hopefully gutsy will solve many of these feisty problems.

-merlin

---

### Post by Pumalite on 2007-09-06
Hey Merlin, I thought you had your Tribe 5 already installed.

---

### Post by merlinus on 2007-09-06
I have run it from the live cd, but most of my income is derived from computer-related work.  So alpha and beta remain greek letters, for me.

Of course years of DOS and windows were never more than beta-testing.

:)

-merlin

---

### Post by Pumalite on 2007-09-06
Fortunately I just have fun, so I have Tribe 4 in one and Tribe 5 in another. They are great. I've had not one problem up to now. I do video and sound encoding mostly. Updates have ran flawlessly. Give it a try.

---

### Post by frychiko on 2007-09-07
Tribe 5 doesn't solve the problem. 

I had this "can't access tty" problem as soon as I  upgraded my motherboard and now waiting for a fix..! Damn you MSI motherboard.

---

### Post by Zenham on 2007-09-16
I can suggest, from my experience this evening installing on a machine with a new P5K WS motherboard, that you can indeed install Ubuntu from the standard i386 CD on this motehrboard.

Two things you should try: 

1.  Only use a sata CD/DVD drive, unless you have SATA entirely disabled and are running in IDE mode.

2. In your BIOS, turn on AHCI, and set the SATA mode to "compatible".

You can just boot off the standard install CD and proceed normally.

This worked fine for me, posting on the box while it updates. Even came up with a working network, no hands required.

---

