---
title: "Filing Lucid bug"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Eric M. on 2010-03-25
This is a newbie question, but I'd like to help out the lucid release.  I am testing Lucid beta 1 and want to report a bug.  But I can't identify the problem area nor know where to look for any crumbs of the failure.  So I can't tie it to a specific package to submit a bug report.  Since I've been running 9.4 without problems, I'm pretty sure it is related to the new installation on a separate partition of 10.04 beta 1.

I having a system crash/hang for unknown reasons.  After a random period of time, the X windows goes away and I'm left with a flashing cursor and a hung machine (no activity, hard reboot required to restart).  This has occurred on Live CD, native install with all latest updates applied.  The crash does not appear related to any specific activity nor time.  It has crashed from everything from the install program running (in Live CD and not) to the update program running.

The only potential clue I have is running tightvncserver from another system for a half a day did not have a system crash (just lots of tightvncserver crashes).  When going back to the direct console, the problem occurred.  So maybe this is X/video card related, but not sure.

How do I track down the package causing the problem so I can submit a report?  

Where would I look to see if the system caught the failure to a log file before hanging.  I'm hoping this helps determine the package.

Thanks,
Eric M.
--------------
MB GIGABYTE GA-MA709GP-UD4H, Phantom II X4 940 Black, 8GB, 1.5TB HDD

---

### Post by quixote on 2010-03-26
Sending crash reports in Lucid should be an automated process.  The orange starbrst-y thing shows up in the panel, you click on it, and it asks whether to send a report.  It collects all the data the devs need.  I think you may need a launchpad account for it to file the report, but maybe not.

I wouldn't worry too much about sending this crash report.  Lucid has been amazingly stable at least since the alpha2, and then with the next to last kernel upgrade, it suddenly started crashing spectacularly on any and all occasions.  They have hundreds of bug reports about it.  The last time I tried to send a report a little message flashed up saying, in effect, "Yes.  We know." :D

---

### Post by kansasnoob on 2010-03-26
> **Eric M. said:**
> This is a newbie question, but I'd like to help out the lucid release.  I am testing Lucid beta 1 and want to report a bug.  But I can't identify the problem area nor know where to look for any crumbs of the failure.  So I can't tie it to a specific package to submit a bug report.  Since I've been running 9.4 without problems, I'm pretty sure it is related to the new installation on a separate partition of 10.04 beta 1.

I having a system crash/hang for unknown reasons.  After a random period of time, the X windows goes away and I'm left with a flashing cursor and a hung machine (no activity, hard reboot required to restart).  This has occurred on Live CD, native install with all latest updates applied.  The crash does not appear related to any specific activity nor time.  It has crashed from everything from the install program running (in Live CD and not) to the update program running.

The only potential clue I have is running tightvncserver from another system for a half a day did not have a system crash (just lots of tightvncserver crashes).  When going back to the direct console, the problem occurred.  So maybe this is X/video card related, but not sure.

How do I track down the package causing the problem so I can submit a report?  

Where would I look to see if the system caught the failure to a log file before hanging.  I'm hoping this helps determine the package.

Thanks,
Eric M.
--------------
MB GIGABYTE GA-MA709GP-UD4H, Phantom II X4 940 Black, 8GB, 1.5TB HDD

Sounds like an Xorg issue. One of the hardest bugs to file.

What graphics card to you have?

The ouput of the following command might help:

```
lspci | grep VGA
```

Maybe even:

```
cat /proc/cpuinfo
```

---

