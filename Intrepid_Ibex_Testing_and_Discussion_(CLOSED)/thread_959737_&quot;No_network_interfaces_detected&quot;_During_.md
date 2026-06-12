---
title: "&quot;No network interfaces detected&quot; During Clean Install of 8.10"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Rexcellent on 2008-10-26
Hello,

Although relatively new to Ubuntu, I believe I encountered a problem with the following combination:

Ubuntu Server 8.10 Intrepidd Ibex 64-bit edition.
Asus ASUS P5KPL-CM board updated BIOS rev. 0514.
Atheros L1E ethernet NIC by Attansic Technology Corp.

So, I was excicted when I read [**Linux 2.6.27 was released**]("http://news.softpedia.com/news/Linux-kernel-2-6-27-Is-Out-95350.shtml").  It even specifically mentioned the atl1e network controller.  I was even more excited when, shortly thereafter the relase date of Ubuntu 8.10 was publicized.

Having worked with 8.04 Hardy Heron, and having worked around the earlier compatibility issues with the Atheros nic, I decided to give 8.10 beta a try.  Unfortunately, early into the fresh install, I received a red screen indicating: "No network interfaces detected".  Afterwards, installation ran to completion.

Curiously, I was able to start networking manually, but the connection was highly unreliable and would frequently disconnect.

Since [**this procedure worked for me**]("http://jan.ucc.nau.edu/~wal2/atheros_attansic.html") with 8.04, I tried the same using 8.10 RC Intrepid, and guess what, It worked!

It appears that the procdure mentioned above uses atl1e driver 1.0.1.0 whereas the release candidate uses 1.0.0.7, as I hypothesized in [**this thread**]("http://ubuntuforums.org/showthread.php?t=770173&page=6").

Can anyone confirm that this is either fixed in the final version of 8.10 or if it will continue to be an issue as it was in 8.04?

Cheers,
Rex

---

### Post by Rexcellent on 2008-10-29
So, I'm guessing this was the wrong place to ask about this combination of hardware and software.  Can anyone point me in the right direction?

Thanks

---

