---
title: "Theoretical question on dual installs and data loss!"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2010-02-28
Hi.
[I]Example Scenario:
Someone has a laptop running Windows Vista on an 80GB hard drive.
They have 50GB used up.
They want to install Ubuntu as a dual boot. They allocate 30GB to the Ubuntu install.[/I]
Would all of the data on the Vista side be 100% safe? This may seem like a silly question but I'd just like it confirmed.
Thank you.

---

### Post by codemaniac on 2010-02-28
No problem with that go ahead and install ubuntu..your vista partition will not be affected..with ubuntu installed you can also access your ntfs partitions from ubuntu with full read write access..

---

### Post by oldfred on 2010-02-28
NO.

Your 80GB drive is not 80GiB, probably about 76GiB. The drives use 1000 and systems use 1024 bytes math. 
System requires space for journaling which consumes some of the available space.
Windows needs 10-20% free space just to keep working or 5 to 10GBjust to keep working.

---

### Post by Rytron on 2010-02-28
> **oldfred said:**
> NO.

Your 80GB drive is not 80GiB, probably about 76GiB. The drives use 1000 and systems use 1024 bytes math. 
System requires space for journaling which consumes some of the available space.
Windows needs 10-20% free space just to keep working or 5 to 10GBjust to keep working.

Ah yes. I now remember hearing that about Windows and the percentage of free space. I was told 20% is reccomended.

On that matter. Does Ubuntu require x% of space to function at its best?

---

### Post by oldfred on 2010-02-28
I think ubuntu hide some extra space. Some tools report different sizes than others. It maybe the space reserved for journaling.

As far as my estimate of your drive size, it was swag, but there has been some discussion before where users were complaining about "missing" space. Someone else commented wait till you buy a 2TB drive and see how much you lose.

My est was not too far off. 80/[FONT=Verdana][SIZE=2]**1.073.741.824 = **[/SIZE][/FONT]74.5

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
Conversions for KB, MB, GB
[FONT=Verdana][SIZE=2]one **gibibyte**      1 GiB = 2**30 B = **1.073.741.824 B**[/SIZE][/FONT]
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

---

### Post by Rytron on 2010-02-28
Thank you oldfred. ;)

---

