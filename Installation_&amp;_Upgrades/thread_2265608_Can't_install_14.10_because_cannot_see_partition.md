---
title: "Can't install 14.10 because cannot see partition?"
date: 2015-02-16
forum: Installation &amp; Upgrades
---

### Post by frank0478 on 2015-02-16
So here is my partition. I intend on using the unallocated space for ubuntu 14.10 [ATTACH=CONFIG]260024[/ATTACH]
but when I use boot through usb to install within ubuntu, I don't see ANY of the partition. It just comes out as one single 500 gig disk. 
I am not entirely sure how to proceed. I have read some procedures but it has been confusing. 

I obviously want to leave the C drive (windows 7) and the G drive alone. If anything, I will want to access the G drive from within Ubuntu. But that's later on. 

First, I need to figure out how to do this dual boot thing and have it set up into the unallocated space.
Any assistance would be appreciated.

---

### Post by Mark Phelps on 2015-02-16
BEFORE you charge into dual-boot setup, I strongly advise that you use the Win7 Backup feature to create and burn a Win7 Repair CD.  You may need that later to restore a working Windows boot loader if the dual-boot install corrupts it.

---

### Post by Bucky Ball on 2015-02-16
... and backup any valuable data. Are you choosing 'Something Else' when you get to the options for install?

---

### Post by coldraven on 2015-02-16
> I don't see ANY of the partition. It just comes out as one single 500 gig disk.
When you boot Ubuntu from USB did you try running gparted?
It may give you some more info. You may need to create a partition in the unallocated space but whether that best done in Windows I will leave to  other people give perhaps better advice.

---

### Post by frank0478 on 2015-02-16
@Mark, windows back up disc, done.
@Bucky, Much of my stuff is on cloud. And yes, I chose the "something else" feature.

---

### Post by frank0478 on 2015-02-16
I think I might have come across "gparted"
but I am not entirely sure what it means and how to do it...

---

### Post by Bucky Ball on 2015-02-16
Boot from the installer, 'Try Ubuntu', once at the desktop search for Gparted (may be called partition manager in your version, I'm not using a standard Ubuntu). ;)

Don't create Linux partitions with Windows. You can't. Do that during install with the unallocated space as you'd planned.

---

### Post by frank0478 on 2015-02-16
K I just did what you said.
Try Ubuntu -> run Gparted
It told me that I got overlapping partition. I am not too sure what this means and how to resolve it. 
In essence, Gparted showed my partitions IN ADDITION to a unallocated 500 gig, which should should not be happening and hence the "overlap" I am assuming.

---

