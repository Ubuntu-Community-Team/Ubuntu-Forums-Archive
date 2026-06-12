---
title: "Upgraded to 10.10...somehow running 11.04"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Captain Hank on 2010-12-14
Yesterday, I upgraded my system from 10.04 to 10.10.  Everything went fine with the upgrade.  Today, I had an issue with connecting to a wireless network, and in the past restarting my computer fixed that.  After I restarted, my desktop seemed to revert to its 10.04 appearance and was running noticeably slower than before I restarted.  Confused, I checked "About Ubuntu" to make sure that the upgrade had, in fact, gone well.  Much to my surprise, it claims that I'm now running 11.04.  

So...how on earth did I do that, and how can I go back to 10.10?

---

### Post by Rubi1200 on 2010-12-15
Hi and welcome to the forums :)

Run this command from the terminal and post the output here please:
```
cat /etc/*release
```

---

### Post by Captain Hank on 2010-12-15
Thanks for the welcome!

Interesting.  The output is: 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Looks like it's a weird problem with "About Ubuntu," and a false alarm.

---

### Post by Rubi1200 on 2010-12-15
Good news then :)

You can mark this thread Solved, if you think it is, using the Thread Tools near the top of the page.

Enjoy!

---

### Post by sikander3786 on 2010-12-15
It is indeed 10.10. Looks like a bug. I came across another similar problem today.

[http://ubuntuforums.org/showthread.php?t=1645948](http://ubuntuforums.org/showthread.php?t=1645948)

---

