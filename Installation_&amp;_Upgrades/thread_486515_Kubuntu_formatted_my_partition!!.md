---
title: "Kubuntu formatted my partition!!"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by yigals on 2007-06-28
In the installation process, after trying to resize one of the partitions, Kubuntu reported error, and now I can't access my partition any more! (has a lot of important data, I know i'm dumb for not doing backup, but I didn't think it'll actually erase my partition!)
Windows says that the partition is not formatted, and I can't do chkdsk because the partition type is RAW (according to cmd).

Is my data all gone??

---

### Post by kaltv on 2007-06-28
Ouch.

You are talking about the Windows partition right? If so, have you tried starting Ubuntu on just LiveCD (no install), to see if you can access the windows partition from there? With any luck it will automount the Windows partition anyway. Otherwise you might have to use the console to try a forced mount of the Windows partition.

If you can, then you can do a back-up of the data through Ubuntu LiveCD before trying to fix the rest of the problems. At least your data would be safe! :( Good luck!

---

### Post by yigals on 2007-06-28
QTParted is letting me know that the filesystem of the partition is unknown, and I can't mount it since I need to report what filesystem it is using, I tried several options, none have worked.
Any other ideas?

---

### Post by louieb on 2007-06-28
All kinds of data recovery tools  here. Good Luck. [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by ububaba on 2007-06-28
Please check again it may not be a re-partitioning but renaming of the drives. It happened 
to me once. No harm in trying.

---

