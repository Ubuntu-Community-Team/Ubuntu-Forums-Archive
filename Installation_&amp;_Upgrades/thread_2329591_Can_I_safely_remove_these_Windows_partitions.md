---
title: "Can I safely remove these Windows partitions?"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by coldraven on 2016-07-03
I have just bought a second Lenovo B590 laptop with Win 8 and I plan to make it dual boot with Ubuntu 16.04.
I do not plan to use Windows very much but I suppose that it would be handy now and again.
I have not used Windows  since XP so finding my way around Win8 has been very tedious.

What I've done so far....
Determined that there was no restore image
Created one using recimg /createimage c:/image_folder 
Copied this image to an external drive. It's called "CustomRefresh.wim" and is 6.5 GB. Well I hope that a wim file is a restore image :)

Now using Windows Disk Management I want to shrink the Windows partition.
Can I also delete the three empty partitions on the right of the picture?
Or should I first do  a fresh install of the Windows image to clear out all the Lenovo, Norton etc bloatware? All ideas welcome!

---

### Post by yancek on 2016-07-03
It would seem so since if you look at the top section of the window, Disk Management shows them as windows filesystems with "100%" free which would indicate there is no data on them.  Surprising for a partition labelled windows recovery?

---

### Post by coldraven on 2016-07-05
> **yancek said:**
> It would seem so since if you look at the top section of the window, Disk Management shows them as windows filesystems with "100%" free which would indicate there is no data on them.  Surprising for a partition labelled windows recovery?
Yes, I thought it was odd but I guessed that the seller on eBay had done some sort of restore. The only username is lenovo1. 
I have not had the time to do anything so far, maybe have a go in the next few days.

---

### Post by Mark Phelps on 2016-07-05
My guess is that the previous owner did an upgrade to Win10 -- as that is known to create new partitions in the process.

Looks like they simply rolled back to Win8.1 and left the crud there from the Upgrade.

---

