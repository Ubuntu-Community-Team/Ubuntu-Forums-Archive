---
title: "Upgrade to 12.02 from &quot;failed&quot; 11.04 to 11.10 upgrade"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Terry Su on 2012-05-14
I've upgraded 11.04 to 11.10 with result that system stalls with "Booting system without full network configuration...".   When I log in to tty1 things seem to work normally.  I've worked on problem for a few hours according to instructions in Ubuntu Forums thread "waiting for network configuration" with no success. 

 Login message on terminal says "New release '12.04 LTS' available. Run 'do-release-upgrade' to upgrade to it."

Would it be dumb to go ahead and do this in spite of problem -- maybe it'll fix it?

when halting system I get "Unable to connect to system bus..." message and have to push power switch to shut down power.

System76 PanP8.    I have done nothing unusual to system.  Almost like it came out of the box aside from some software.

---

### Post by darkod on 2012-05-14
Since 11.10 didn't work I guess you can try upgrading to 12.04 LTS. But I doubt anyone can promise you it will work.

You might wanna back up important data before you start.

---

### Post by Terry Su on 2012-05-14
Thanks darkod,

I'm going to work on some things with symlinks that were suggested in the mentioned thread.   Need to learn more about what they are and how they're used.  I don't see one in /var/run and I haven't been into /var/run/lock.

---

### Post by Terry Su on 2012-05-14
Oh, yeah, 

I didn't really expect any guarantees.  I'm not a fool, I just wondered what kind of response I might get.

---

