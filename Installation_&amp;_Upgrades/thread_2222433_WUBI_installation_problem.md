---
title: "WUBI installation problem"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by musahossein on 2014-05-06
> **Mark Phelps said:**
> While that statement is true, using WUBI is NOT "running inside Windows".  The "inside Windows" part is the installation, and while it does create a single file (root.disk) inside a Windows filesystem partition, when you run Ubuntu via Wubi, your are running Ubuntu by itself, NOT "inside Windows".

And, BTW, while I'm not personally a fan of WUBI, it was a useful way to allow people to experience Ubuntu first-hand without the risk of trashing their systems due to partitioning mistakes.

I have a question. I downloaded and installed Ubuntu 13.10 using Wubi. I am running windows 7. Then yesterday while using Ubuntu 13.10 inside of windows, a pop up informed me that I could upgrade to Ubuntu 14.04. So I clicked on the install and all went well until restart. Now after I restarted nothing happens the screen hangs. So I don't have Ubuntu any more. So then in the hope of recovering files I re-installed 13.10 using Wubi as before. But the installation stopped before it was complete. I can now use 13.10 inside windows as before but none of the files or folders are there. Can any one tell me what is going on and whether I can ever hope to recover any of the files?
Thanks
Musa

---

### Post by slickymaster on 2014-05-06
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by musahossein on 2014-05-06
Sorry about that. Still trying to figure my way thru this forum.

---

### Post by Mark Phelps on 2014-05-06
WUBI has been discontinued.  Would be best if you removed the installation and looked into installing into its own partition.  Even if you get it fixed, you will not be able to upgrade since it's not being supported anymore.

---

### Post by oldfred on 2014-05-06
Wubi is just one file root.disk inside the NTFS partition.
So if you reinstalled without saving the old root.disk, your data is gone. And since it is a Linux formatted partition inside a NTFS partition it would be very difficult to find old data. 
If you saved the old root.disk it can be mounted and data recovered.

Backups are one the most important things to learn with computers. If you data has any value at all you have multiple backups.

---

