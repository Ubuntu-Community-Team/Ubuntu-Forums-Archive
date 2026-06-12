---
title: "Karmic telling me my disk has bad sectors"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Findarato on 2009-10-15
Hello,

I recently upgraded to ubuntu karmic and now my system is telling me it has bad sectors and that I should replace my hard disk. This couldn't possibly be related to the installation itself right ?
Ubuntu 9.04 never told me such a thing and I find it pretty weird.

Thank you very much for your help,
Findarato

---

### Post by andied on 2009-10-15
google search will bring up numerous posts about this - consensus is this is a bug in the disk utility

---

### Post by QIII on 2009-10-15
When did you upgrade?  Are you using the Beta?

Alpha 6 was reporting bad sectors and disk failure on one of my data drives on a 64 bit test machine.  That has cleared up since I've been using the Beta.

And yes... As above, it is a bug.

---

### Post by Jimmyfj on 2009-10-15
:guitar: Ta-da :guitar:

I've been on Karmic since the Alpha1 and **only** in Alpha6 did I get those reports about bad sectors and possible future disk crash. I took it for a bug since the fsck did not report anything at either boot up or in the log files. Now in Beta the error has completely disappeared.

---

### Post by andied on 2009-10-15
I am using the latest beta and I received this ominous warning that my disk was failing and I needed to replace it. I re-installed and got the same message...quite disturbing, to say the least.

---

### Post by donniezazen on 2009-10-15
I am having same error. Is there a third party application that i can run to check if i have bad sectors?

---

### Post by cariboo on 2009-10-15
Go to System-->Administration-->Disk Utility highlight the drive in question and click the More information link. The problem are will be highlighted in red.

The disk utility will give you the Manufacturers name and the model # of your hard drive. Go to the manufacturers web site and download their diagnostic tools and run them on your hard drive.

See the screenshot.

---

### Post by george1984 on 2009-10-25
I have karmic beta64 on a laptop, no problem with hard drive reported.

Just installed karmic rc64 on to desktop drive sdb. It warns that drive sda (which has hardy installed) has many bad sectors. In fire engine red. Very dramatic.

Just obtained GSmartControl from Synaptic. Short test appears to show no errors (never used it before).

Are these disk failure warnings widespread? Is it the way that I use the two hard drives on this box? - I am presuming that the error message is a false alarm.

---

### Post by autocrosser on 2009-10-25
Do extended tests to make sure---but, yes--you are most likely "bit" by the bug...search for the report & add to it IF you are sure your disks do not have problems.

---

### Post by nanog on 2009-10-25
Your bad sectors are real -- but having bad sectors is not uncommon.  Palimpset the new gnome disk utility is just overly sensitive.

---

### Post by george1984 on 2009-10-25
Thanks for the responses.

Will do extended test - find out how many bad sectors there are, and if they are significant.

---

### Post by george1984 on 2009-10-25
Thanks for the responses.

Will do extended test to determine how many bad sectors, and if they are  significant.

---

### Post by JillSwift on 2009-10-25
The utility does have a check-box to tell it not to tell you about a failing drive. (In the more information window)

Just check to make sure it's not really failing first. :)

My laptop hard drive has has 12 bad sectors on it from the moment I got it (used and abused thing). Palimpsest told me it was failing, too. I just peek at it now and again to make sure it stays at 12 bad sectors. If it starts forming new bad spots, *then* I know the drive needs replacing.

---

### Post by Polygon on 2009-10-25
what about pending sector count? Is this part of the bug or is this for real?

---

### Post by george1984 on 2009-10-26
hello again.

I ran GSmartControl, but it stopped at 60% completion reporting a read error.

Is there a command line instruction that will force it to 100% completion and report all errors?

---

### Post by seeker5528 on 2009-10-28
> **Polygon said:**
> what about pending sector count? Is this part of the bug or is this for real?

If you have another drive available that is the same size or larger to use, I would use ddrescue to clone the one with the errors, then use it again to write the stuff from the clone back to the original:

ddrescue input output

: if the disks were sda and sdb:

ddrescue /dev/sda /dev/sdb
ddrescue /dev/sdb /dev/sda

: if it still says there are sectors waiting to be remapped after that, then I would replace the disk.

If you don't have another disk to do the above type of operation with, your screenshot shows that you have a Western Digital, if you go to their website they should have an ISO you can download for their utility that does the testing, which might provide an option to try to fix the errors. 

Any way you do it there might be some lost data in the sectors that are waiting to be remapped and possibly higher risk of losing additional stuff you you use a disk utility than if you copy the stuff first.

Later, Seeker

---

### Post by seeker5528 on 2009-10-28
Oops, got a diplicate post somehow.

---

### Post by bluesscream on 2009-10-28
I was too lazy to pluck off an old, broken drive with an no more booting xp and karmic shows me exactly the bad status of this drive. But I'm still able to mount it and clone it's files... ;)

---

