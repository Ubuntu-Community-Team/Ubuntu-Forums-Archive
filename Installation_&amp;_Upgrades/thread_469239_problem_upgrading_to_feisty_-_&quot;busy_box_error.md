---
title: "problem upgrading to feisty - &quot;busy box error&quot;"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by ncumming on 2007-06-09
Tried this post in the beginner forum and didn't have much luck...maybe this is the better place...

I've been running dapper for a couple of months now on an older dell laptop (approx 500 mhz PII and 384MB of RAM).  I recently upgraded to edgy with very few issues, and got a little ahead of myself and tried to upgrade to fiesty. During the upgrade process, something seemed to go wrong - after a couple of hours, the process just stopped. I tried rebooting my system to see if perhaps the process had finished and got the apparanently infamous "***can't access tty job control***" error.  I've tried following the advice in this forum and don't get very far.  Does anyone have the patience to walk me through troubleshooting this? I realize I can always go back to edgy, which would be fine, i'd just hate to have to wipe my system to do it, which is the only thing i can think of to do know - basically start from scratch...

---

### Post by Beaucephus on 2007-07-02
The great thing about Ubuntu is starting from scratch is not that much of a hassle.  Trying to troubleshoot a borked install is a waste of time when you can be back up again in a trustworthy fresh install in a half hour. 

Backup any data and hand configured files (ndiswrapper?).  Boot from a fresh Feisty CD and your off.  Don't forget to check the MD5 sums.

---

### Post by Herman on 2007-07-02
Hello Beaucephus,

Is your '*/bin/sh: can't access tty; job control turned off*' error like this one,[busybox or tty error]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#busybox") ? 

Or is it more like this one [Target filesystem doesn't have /sbin/init]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Target_filesystem_doesnt_have_") ?

If you can identify which one it is and then follow the sub links from those links you should find something there that will help you.

I agree with ncumming too, if you can't fix it easily, one of the great things about Ubuntu is that it's extremely quick and easy to make back up from and restore again after a re-install. Here's a link to my [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm") page in case that will be any help to you. I prefer to try to fix mine first though, but you can do whichever seems easier.

Regards, Herman :D

---

### Post by ellannjohnson on 2007-07-25
After all the t:guitar::guitar::guitar:rouble shooting I did on this problem, nothng worked. I finally tried live acpi=off @ boot:  line. Worked like a charm.

---

