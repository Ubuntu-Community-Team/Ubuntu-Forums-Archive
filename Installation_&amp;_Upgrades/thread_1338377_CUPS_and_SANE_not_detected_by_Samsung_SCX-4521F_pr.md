---
title: "CUPS and SANE not detected by Samsung SCX-4521F printer installation script"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by testmiss123 on 2009-11-26
Samsung SCX-4521F printer installation script gives me the following messages:

CUPS that is required for driver package to work properly was not
detected on your system. Please exit installation procedure and install
CUPS package from your Linux distribution CD-ROM or from Linux distribution

So I did:** sudo apt-get install cupsys cupsys-client**

But the message still remained the same. I ignored it and moved on to the next line and the warning was:

SANE that is required for driver package to work properly was not
detected on your system. Please exit installation procedure and install
SANE package from your Linux distribution CD-ROM or from Linux distribution
vendor web site

So I did: **sudo apt-get install libsane-extras**

I still get the  same 2 messages. Why do I get these messages?   Can I proceed by ignoring these messages?  If not how can I avoid these two warning signs? Can someone help me?

---

