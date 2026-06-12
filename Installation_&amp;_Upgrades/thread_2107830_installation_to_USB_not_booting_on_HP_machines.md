---
title: "installation to USB not booting on HP machines"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by jeliocranch on 2013-01-22
Wondering if anyone has any insight.
I'm teaching an intro to Linux class, and thought I had come up with a cool idea to allow students to use the same environment no matter where they were working:
  I installed 32 bit 12.04 to a 32 GB flashdrive.  Not a liveUSB mind you, a full install.  I've been testing it for the last 4 weeks during the break in semesters, and its been working extremely well on all machines, until a few days ago.   
  It still works perfectly on almost all machines, but now it interrupts the post/late BIOS startup on the HP workstations we have in the classroom.  Instead of even getting boot options, I get a blank screen with a flashing cursur in the upper left corner as long as the drive is inserted.  It does recognize a new drive inserted and asks for confirmation prior to preceding with post.
  Trying the drive in any non-hp machine I have access to works perfectly, still.  I was thinking it was perhaps a flash drive issue, as the machines will boot liveUSB's, but no.
I was also thinking file-system, since the in the BIOS-new-hardware-warning there's a message about reconfiguring for UNIX file systems, but inserting the removable classroom HDD's with the same Linux OS configuration works fine without changes.

So, I'm left with culprits of either a new HP BIOS, or some difference in the way the system sees a liveUSB vs a standard install, or something else.  Anyone system-admin experience with HP machines know anything about this (or anyone else, for that matter?)
Thanks!

---

