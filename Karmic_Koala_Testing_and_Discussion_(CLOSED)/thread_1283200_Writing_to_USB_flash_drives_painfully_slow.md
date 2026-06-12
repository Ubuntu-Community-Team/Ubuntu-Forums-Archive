---
title: "Writing to USB flash drives painfully slow"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-10-05
Hi guys. 
I've been experiencing this problem since installing Karmic back in A4.  Anyway, whenever I try to write a file to a USB flash drive, it copies at around 16-20mb/s, which I can deal with, and quickly reaches the end of the copy.  However, right at the end, the copy bar hangs for a few minutes.  It is proportional to the size of the file and I *think* that the file has been successfully copied, however I am not certain.
Writing to an external hard disk via USB does not do this and this has happened with multiple drives.  
What is the problem?

---

### Post by The Fiddler on 2009-10-05
On my Jaunty installation, I get pretty similar behavior: the bar moves quickly, then stops before finishing. If I copy more than one sufficiently large file (e.g. parts 1 and 2 of a movie), I see this start-stop routine a few times before the copy finishes.

I'm pretty sure this is not a bug: the system is caching the file in memory (causing the bar to move quickly) but the USB stick cannot keep up. At some point, the system has to wait until the USB stick has finished writing data before moving on.

Check the light on your stick: if it is flashing when the bar stops moving, it means it is still writing data - the copy is not yet complete.

---

### Post by JCoster on 2009-10-05
Yeah the light on the stick still flashes.

I understand the reasons for why it takes so long but surely the bar stopping right at the end is incredibly misleading?

---

