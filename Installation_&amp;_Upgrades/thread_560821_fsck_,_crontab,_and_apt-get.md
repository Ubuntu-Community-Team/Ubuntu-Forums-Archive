---
title: "fsck , crontab, and apt-get"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by iconicmoronic on 2007-09-26
I'm hoping someone in the forum can assist.
I have a few questions; I'm new to Linux and reading the LPI Linux Cert book by O'Reilly, and supplementing with a web page here and there but a few things are not clear to me as of yet.

**_apt-get:_**

I've loaded two seperate Ubuntu versions, and am now fully up-to-date with 7.04   I wasn't having any issues running apt-get commands until today, but all of a sudden I keep getting a message: [B]cannot execute binary file; are you root?, and yes I've used sudo with apt-get.
For example, apt-get autoremove which just now completed, was not running two seconds ago.[/B]
Can someone perhaps shed some light on why the binary file might not execute? Could it be that somehow my package manager is occupied, the swap partition overloaded, or something of this nature? 
**_fsck & crontab:_**

I haven't tried a regular maintenance scheduling uptaking with Linux, ever, when I ran Windows XP I was obsessed with not seeing a single red line on the fragmentation graph or having any excess files; etc. This is because I'm on a legacy PC and I don't want to hinder it any.

I had attempted running fsck on a few Ubuntu distribution and I had begun to think it erroneous that fsck was a Linux command because the message bash: fsck is not a command always returned.

Last night, I took apart my PC to clean it free of dust and what not, and remove excess parts that might be eating up some resources. Putting it back together, upon boot fsck was forced!  And I was glad because like I said, I like a clean filesystem and whatnot; but the fsck utility ended abruptly stating:

**fsck (exited abnormally) with exit status 3. **What the heck is exit status 3? I found a few statuses for exit on fsck like 1,2,4, and some higher numbers, but the about Debian page I checked had no positive answer.

It also said something about the next fsck being scheduled at a future time, as if to say it was prescheduled and I assume this is because fsck forces a check of the filesystem from time to time.

A hint though is that originally fsck stated that it **had not been run in 39,800 days, and upon running it again (from a terminal -- which prompted me to reload the OS in case any filesystem damaged occurred because my mouse wasn't functioning right and as it turns out the battery was just dead!!) it stated it hadn't been checked in 10,000 some-odd days.**

*To me this suggests something is wrong with the system clock.* Can anyone offer an explanation? (oh and I apologize for dragging on).

The second half of this question is how can I use **crontab** (or for that matter another tool) to schedule fsck at boot time, similar to Windows XP? 

And, finally, for now those are my three questions. Thankyou, any reliable explanation is much appreciated.

---

