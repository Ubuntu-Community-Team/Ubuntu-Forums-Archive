---
title: "Ubuntu upgrade causes slow internet connection"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by mixtri on 2010-05-19
Hi guys.
I upgraded to ubuntu 10.04 lts yesterday. the upgrade went smoothly. but now I have a very slow internet connection. It is as if i am on a dial up when i have a broadband speed of 20 MB. is anyone else experiencing this? What can i do to fix or perhaps roll-back the installation to the previous proper working state.
Thanks

---

### Post by mixtri on 2010-05-19
Anyone? please!

---

### Post by wkulecz on 2010-05-19
How are you judging speed?

Web browsing? or file transfers?

give the following command in a terminal:

date && nslookup msdn.com && date

If its several seconds elapsed between the date/time printout you may be up against this issue:

[http://ubuntuforums.org/showthread.php?t=1476688](http://ubuntuforums.org/showthread.php?t=1476688)


If the DNS is fast, but downloads are slow, if you are using WiFi take a look at:

[http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3)  and [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)


Your complaint is too generic for anyone to really know what the issue might be.  The above are two problems I'm aware of.


I see the very slow (5 second DNS lookups which kills web browsing since modern pages usually do many lookups) web browsing issue depending on what network I'm on.

The Ubuntu powers that be say its "broken routers" and while there may be truth to it, getting the local network powers that be to spend money to fix network problems Windows and Mac users on the same subnet don't have, will be a very tough sell!

HTH,
--wally.

---

### Post by wata on 2010-06-11
I ran into exactly the same problem, Ubuntu 10.04.  

Download speeds were extremely variable 200kbps ~ 3.3Mbps, most of the time in the 200kbps range.  Tested using [http://mire.sfr.fr/](http://mire.sfr.fr/) (I live in France using SFR as an IP provider).  Ping times to [www.sfr.fr](www.sfr.fr) were 1000 to 3000-ms.  This affected all three machines on my network (Ubuntu 10.04, Ubuntu 9.10, and Windows XP).

While running ping on my 9.10 PC, I killed the Ubuntu One daemon (on my Ubuntu 10.04 machine) and *bam* ping times immediately dropped from 2000-ms to sub 60-ms.

I never had this problem with Ubuntu One on my 9.10 PC (and the Ubuntu One daemon was running on the 9.10 during this entire test).

---

