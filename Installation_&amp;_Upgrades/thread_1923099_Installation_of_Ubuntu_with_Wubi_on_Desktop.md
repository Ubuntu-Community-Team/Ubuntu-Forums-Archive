---
title: "Installation of Ubuntu with Wubi on Desktop"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by spidey89 on 2012-02-09
Hey guys,

This is my first post and I've tried to find answers, but I still can't get it to work, I tried to install Wubi Ubuntu on my desktop with multiple drives, 5 to be exact, but I can't get it to work, even after copying the boot mgr or something to all my drives, any ideas?

---

### Post by Mark Phelps on 2012-02-10
First of all, Wubi installs such that you don't NEED a boot manager.  It uses the existing Windows boot manager to provide OS selection capability.

Second, if you really did install GRUB to ALL of your drives, that was a serious mistake.  Thrashing around like that only makes things works.  If any of those drives booted Windows, you most probably broke Windows boot capability in the process.

Third, the proper way to install Wubi is to download the ISO and the Wubi.exe program, put them in the same directory, right-click on the Wubi.exe program, select Run as administrator -- and run in.

This ALL has to be done from inside Windows.

---

### Post by spidey89 on 2012-02-10
Maybe I put it wrongly, I have installed and run successfully Ubuntu using Wubi on my laptop before, my Windows 7 on my desktop is fine. I can't remember what was the error, I've found some answers saying copy the files over to the hard drives and it'll work, which unfortunately didn't work for me

---

### Post by oldfred on 2012-02-10
If you have 5 drives and have already tried wubi on your laptop, so you seem to like Ubuntu enough that you want it, why are you installing wubi? It may be time for a full partitioned install.

Even the creator of wubi expects you to move to a full install.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

With multiple drives, you can keep Windows on one drive & Ubuntu on another. You can share data in NTFS partitions from all drives easily (ok, relatively easily).

---

### Post by spidey89 on 2012-02-11
I didn't try on my desktop which I want to. My system is already up and running and I'm not sure if dual boot with separate partition will work, and 4 of the 5 hard drives are used to store photos and videos

---

### Post by oldfred on 2012-02-11
Some food for thought on large data drives.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by spidey89 on 2012-02-11
That is confusing

---

