---
title: "Slow/laggy browsing on new web sites, then things are fine"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Saneless on 2009-10-01
Anyone else get this issue?  When I launch the browser it takes at least 10-15 seconds for the start page to come up.  Once it does it's ok.  But if I load a new site, that takes another 10-15 seconds.  Usually if I click around on it it's quick, but sometimes it's not.  New domains always seem to have this issue.

This is not a problem with the router or internet.  A windows and mac machine browsing at the same time on the same router don't have these issues, nor does my iphone.   Also, once something gets going, like a download, my speeds are as fast as they always have been  (600-900KB/s).

This is driving me nuts.. I didn't have this issue in 9.04, it was only when I installed from scratch with Alpha 5 and has been an issue ever since.  I'm going to reinstall beta from scratch to see if it helps, but I just want this fixed.  I saw some bugs, and then people closed them out saying they weren't important or something.. bleh.  Help :)

---

### Post by blakamin on 2009-10-01
Same thing here. At first I thought it was my wireless but then I ran 9.04 live disc. (Karmic is the only OS on this laptop).
Got any links to the bugs?

---

### Post by jbslaw on 2009-10-01
DNS lookups are the problem.  Take a look at this discussion: [https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940]("https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940").  Some tinkering with /etc/nsswitch.conf per the suggestions in the comments will probably help.

---

### Post by blakamin on 2009-10-01
Cheers, worked perfectly... amazing that this is still an issue!

---

### Post by Saneless on 2009-10-01
Thanks jbslaw.  I've seen some things about that file but that is the first I've seen that particular bug thread.  Since I'm not that detailed into networking I wouldn't have searched for "excessive time for dns lookup" so thank you for pointing me in a considerably right direction.

---

