---
title: "Installing xulrunner-1.9.1 in ubuntu 10.04"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by evenchayah on 2010-12-01
I recently upgrade to ubuntu 10.04 from 9.10 on an x86-64 machine.

I was having trouble with Eclipse and deduced it was an issue with xulrunner.  I found that I had two versions of xulrunner installed - 1.9.1 and 1.9.2.  I followed advice and removed xulrunner-1.9.1, which cleared up the problem with Eclipse.

However, now I find that Xiphos (a Bible study software) crashes at startup. I believe this is because it needs xulrunner-1.9.1.  I also have other mysterious behavior.  Gnucash Help no longer works, "Help and Support" under System no longer opens, etc.  I believe all of these are related to xulrunner.

Is there any way to reinstall xulrunner-1.9.1?  It is no longer available as a package in Synoptics.

[BTW, I have tried several steps with Xiphos with help from Xiphos developers to no avail.]

---

### Post by evenchayah on 2010-12-06
I believe this post may be better under general help.  Could a moderator please move the post to a more appropriate forum?  Thanks.

---

### Post by evenchayah on 2010-12-06
I believe I have resolved this issue.  Apparently there was something broken in the environment settings.  I ran:
sudo xulrunner --register-global
in the install directory (in my case: /usr/lib/xulrunner-1.9.2.12).  This seemed to resolve all issues.

---

### Post by Rick B. on 2011-01-17
Thanks for the solution you posted here. I've been struggling with this problem for the past 2-3 weeks. I applied your solution and Xiphos is working again. Thanks for the tip!

---

