---
title: "Need help uninstalling Ubuntu"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by obserspy on 2024-08-06
So I've recently been wanting to get rid of Ubuntu because it is taking up too much space and I don't need the OS anymore. Tried to delete it from Disk Management in Windows 11, but my 2nd SSD which is a 2 TB drive that I allocated everything for Ubuntu specifically is not anywhere in Disk Management. Yes, some partitions with no file systems appear and the rule of thumb is that they are usually Linux partitions, but they are not anywhere close to the 1 TB+ of storage I allocated to Ubuntu. At this point, I'm so confused as to what to do because my 16 GB flash drive that I have tried to format, so I can run a live session of Ubuntu on it, has been uncooperative and is now not even appearing in File Explorer anymore. I'm so confused and overwhelmed and need help. If anyone knows of an easy solution and an easy way to get rid of Ubuntu without using Disk Management, I would be very interested because I need my 1 TB+ of storage back.

By the way, I hope this is a good channel to post this, but if it isn't, I apologize. I just didn't know another place to post this.

---

### Post by currentshaft on 2024-08-06
.

---

### Post by TheFu on 2024-08-07
Any disk partitioner from any OS can be used.  Just delete the partitions with Ubuntu file systems.  If the OS you normally uses doesn't show which file systems are used, nothing I can do about that.  Linux doesn't have that limitation.

It should be obvious, that deleting the wrong partitions would be bad.  Really bad.  Measure 3 times, cut once.  You should backup any data you want to keep across any connected storage as well.  People not used to doing these things often make mistakes and delete the wrong partitions.  Happens all the time.

If I had a GUI, I'd use **gparted**.  If I don't have a GUI, I'd use **parted** on Linux.  Both of those tools should be on any Ubuntu Live Boot ISO (the same ISO used to install the OS).  Gparted works as a "tell it what you want to do, as many things as you like", then "Apply" which actually does it. Don't forget to press the "Apply" button, or nothing will happen.

So, I guess that would not be using "Disk Management", whatever that is.

---

### Post by yancek on 2024-08-07
How about posting an image or a link to an image online of your Disk Management output.  Some members here might be familiar enough with windows to give you suggestions.
The standard method is to simply format the partition not 'uninstall' it as it is an operating system not an application

Since you want to use windows to remove a non-windows system partition, don't you think it would make sense to go to the microsoft sit or a windows forum?

---

### Post by obserspy on 2024-08-09
Sorry about the silence, yes I can upload an image when I get home.

---

### Post by obserspy on 2024-08-09
The problem is that my 16 gb flash drive isn’t appearing on Windows anymore. No matter what I do, my USB isn’t anywhere to be found.

---

### Post by ajgreeny on 2024-08-09
What is currently on,  or what do you think should be on that USB drive?

If you still have ubuntu installed on the computer and can boot to it you could use that to run  gparted (you may have to install it first) and using gparted create a new partition table on the USB drive, then add a new partition which you can use either for a new instalation or simply as a live Ubuntu system using an ISO of your chosen version.

You haven't give us much information so far so I think we are just guessing at the moment and many of us including me don't know very much about Windows or the reason why it can't detect that USB drive.

---

