---
title: "Kernel Updates?"
date: 2008-09-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-09
Anyone know whats happening with intrepid and kernel updates?

Seems intrepids git hasnt changed in sometime now.

We may see RC6 get released by Linux before we get RC5??

---

### Post by beartard on 2008-09-09
Take a look at the current buglist for the kernel team and you might have some idea why the releases are slow-in-coming.

---

### Post by Nullack on 2008-09-09
> **beartard said:**
> Take a look at the current buglist for the kernel team and you might have some idea why the releases are slow-in-coming.

Understand, but new RC's fix bugs from upstream so by being behind upstream they are working on revisions with known bugs that arent fixed.

---

### Post by ronacc on 2008-09-09
I checked launchpad and while there are a bunch of bugs against "kernel" in general I only saw 5 against 2.6.27-2 and they all seem to involve specific hardware .

---

### Post by jerrylamos on 2008-09-09
> **ronacc said:**
> I checked launchpad and while there are a bunch of bugs against "kernel" in general I only saw 5 against 2.6.27-2 and they all seem to involve specific hardware .

My kernel problem is on an ordinary Compaq Presario 3.3 gHz Celeron, ATI graphics.  There's got to be tons of them out there.  Bug #265049 both Alpha 5 CD Live and installed 2.6.27-2 fail so quickly they don't have a chance to update any logs or messages.

Booting in recovery mode and on CD Live, the last line on the screen is:

pci 0000:00:00.0: MSI quirk detected; MSI disabled

then the system freezes.  BTW, the same Alpha 5 CD installs and runs on an IBM Thinkpad R31.  

The bug is a kernel problem because the same Alpha 5 install boots O.K (for an Alpha) with kernel 2.6.26-5 from Alpha 4.

Jerry

---

### Post by ronacc on 2008-09-09
I did not mean to imply that bugs involving specific hardware are not serious , the are infact "show stoppers" for those with that hardware .however I dont see them as precluding kernal updates which may in some cases remove those bugs .also how much effort should be invested in debugging what almost certaily wont be the kernel actualy released .

---

