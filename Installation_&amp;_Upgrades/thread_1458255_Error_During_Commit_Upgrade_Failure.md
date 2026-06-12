---
title: "Error During Commit Upgrade Failure"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Devon64327 on 2010-04-19
When I try to upgrade ubuntu 9.10 to 10.04 I get the error message 

Error during commit
'E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.'
Restoring original system state

After it finishes downloading the files.
I completely removed all openoffice related files on my computer and i still get the message. Any help?

---

### Post by Lupatrian on 2010-04-22
Me, too - same issue; I retried and got same.

Then I tried doing it this way [http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html](http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html)
and got the same error message.

---

### Post by alpharesearch on 2010-04-22
I have the same issue! Did anybody write a bug report yet? looks like sudo apt-get remove openoffice.org-filter-binfilter fixed it for me...

Regards,
Markus

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/450569](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/450569)

---

### Post by caro on 2010-04-22
I just got the same error.

---

### Post by Zeedok on 2010-04-23
Try this:

[http://ubuntuforums.org/showthread.php?p=9162177](http://ubuntuforums.org/showthread.php?p=9162177)

I'm trying it now, so fingers crossed.

---

### Post by caro on 2010-04-23
> **Zeedok said:**
> Try this:

[http://ubuntuforums.org/showthread.php?p=9162177](http://ubuntuforums.org/showthread.php?p=9162177)

I'm trying it now, so fingers crossed.

This worked for me.  Thanks Zeedok.

---

