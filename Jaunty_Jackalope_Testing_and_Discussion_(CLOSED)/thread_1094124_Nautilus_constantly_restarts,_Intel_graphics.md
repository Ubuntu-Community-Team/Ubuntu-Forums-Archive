---
title: "Nautilus constantly restarts, Intel graphics"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rondackcpu on 2009-03-12
I am trying to run the Alpha version of Jaunty on two Dell machines with Intel graphics.  On one computer, Jaunty Alpha 4 was installed and it has been updated with all the updates to today, March 12, 10:00 AM, EDT.  It has a problem with Nautilus restarting over and over whenever a CD is put in the optical drive.  

Jaunty Alpha 5 Desktop install disk will not boot to the desktop on either of the machines.  Again Nautilus restarts over and over again until the CD is manually ejected or the computer freezes.  This action first appeared about Feb 20.  Log files on the computer indicate a "segfault" in libbrasero-media.  More details and log files can be provided.

That Alpha 5 CD boots normally on a laptop with a Nvidia graphic card and seems to work normally on simple testing.

Does anyone else notice this problem with Intel graphic machines?

CRS

---

### Post by Nullack on 2009-03-12
I believe that Intel are in release candidate for their latest driver revision - might be worth a short to try it on a test machine.

---

### Post by yanns on 2009-03-12
I noticed a similar problem in general:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/339993](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/339993)

---

