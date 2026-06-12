---
title: "Strange message during booting"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by cRoMo on 2005-06-05
Although my Ubuntu is not a fresh install (actually, I've successfully upgraded from SID), I'm writing because I got spare time now, and the problem didn't cause any seriuos inconviniences.

During booting, just after partitions are beeing mounted, such a warning appears three or four times (don't remember at the moment):

"find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments."

Don't know actually what is this warning related to, hopefully someone ever had similar problem. 

BTW, found some related posts on newsgroups, although I'm still confused about the reason for showing those warnings during booting. [link](http://groups.google.pl/groups?hl=pl&lr=&q=find%3A+warning%3A+specified+maxdepth+&btnG=Szukaj)

---

### Post by mingus on 2005-06-05
You can see more clearly what the kernel is trying to do when this error is encountered, by:

changing the boot kernel option "quiet" to "verbose"

and immediately after logging in to gdm, going into a terminal with
#dmesg | more

or consulting the system log
#tail -300 /var/log/messages    (where 300 is an estimate of where in the log that last boot started, just scroll down to the start point or repeat the command if you didn't get far enough up in the file)

look in particular for a filesystem related task as the kernel is mounting from fstab

---

