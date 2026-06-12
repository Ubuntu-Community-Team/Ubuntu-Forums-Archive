---
title: "Another case of &quot;/bin/sh: can't access tty ; job control turned off&quot;"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by sizzam on 2006-10-31
I've seen a few threads referencing this error, I wanted to give my account of what happened to me.   I can duplicate the problem consistently.  This is my only machine, but if anyone from the Ubuntu team needs information from my machine or needs me to try something, I will assist in any way I can.

Machine:
AMD64 3700+
2 Gigs of RAM (512, 512, 1024)
250 GB SATA hard drive
CDRW - IDE Primary Master
DVD-RW - IDE Primary Slave

Using the x86 install CD.

I installed Edgy successfully using the DVD-RW.   I then messed something up and decided I wanted to start over with a fresh installation.

I put the Edgy CD into the CDRW and rebooted.  I was presented with the Live CD menu.  It started to load, and then stopped on a black screen with an error like this:

BusyBox v1.00-pre10 (Debian......
/bin/sh: can't access tty; job control turned off
#

The error was more verbose, but I don't have a copy of it.

I rebooted, and this time put the CD in the DVD-RW.   This lets me boot all the way in and start the installation, although very slowly.   The installation freezes at 78%.  I've tried it 5+ times, always freezes at 77/78%.

I got out an old Windows 98 CD and booted up with it.  I deleted all partitions and FDISKed the Master Boot Record.  I then tried both drives again, same issue.   I get the 'job control turned off' error with CDROM1 and 78% freeze with CDROM2.

I thought maybe I had a RAM issue.  I cycled through the install again using each of my three pieces of RAM alone separately and got the same results with each stick of RAM in the machine.

I ended up downloading the alternative install CD and doing a text based install.  This got me up and running and everything is fine at this point.

---

