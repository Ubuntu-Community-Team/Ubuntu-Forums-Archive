---
title: "recovery"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by zuza on 2009-11-16
I had installed ubuntu 9.10 using wubi. When I tried to resize partitions with PartedMagic I got an error message and after reboot I could start neither windows nor ubuntu. I managed to rescue the root.disk and swap.disk files. How can I access data in that files?
(when I try to mount root.disk under linux, I get a message that the file is corrupt)

---

### Post by TheHimself on 2009-11-16
It depends how much your file system has been screwed up. After turning on the computer, at which point does it stop?

Boot up using the live CD and then see if you can find your partitions and files on the hard drive. Do not change anything. Then in a terminal run

```

sudo fdisk -l

```

and post the result here.

---

### Post by Mark Phelps on 2009-11-16
> **zuza said:**
> I had installed ubuntu 9.10 using wubi. When I tried to resize partitions with PartedMagic I got an error message and after reboot I could start neither windows nor ubuntu. 

You didn't mention which MS Windows OS you used.  IF it was Vista or Seven, you might have corrupted the OS partition by using GParted to resize it.  If that's what happened, you will have to boot from a Vista or Seven installation or recovery CD and run Startup Repair a few times to get Windows boot capability back.

---

### Post by zuza on 2009-11-16
GParted failed while copying files to a shrunk partition. I did reboot the system and entered recovery mode (I have a recovery partition, which wasn't damaged). In the recovery mode the main partition and all the files were detected, so I copied the files to an external disc. I have cleared the partition and installed ubuntu on it. And now I can't get data out of the backuped root.disk file ( fsck says "the superblock is corrupt").

I used Windows Vista, but there wasn't anything like Startup Recovery in the recovery mode, I backuped files and used full recovery option (it cleared the whole partition).

---

### Post by Mark Phelps on 2009-11-16
> **zuza said:**
> I used Windows Vista, but there wasn't anything like Startup Recovery in the recovery mode, I backuped files and used full recovery option (it cleared the whole partition).

It's not Startup Recovery, it's Startup Repair -- and it's an option on the standard Vista DVD and certain recovery CDs.  It doesn't erase or wipe anything, instead, it rewrites the Vista boot loader files, restoring boot capability.

But if you used an OEM-provided CD, or an OEM-provided recovery menu, that option might not be there.  Sounds like that's what you did and it rewrote the partition instead of the boot loader files.

---

### Post by zuza on 2009-11-19
I managed to solve the problem. I recovered my data using R-Linux ( [http://www.r-tt.com/](http://www.r-tt.com/) ).

---

