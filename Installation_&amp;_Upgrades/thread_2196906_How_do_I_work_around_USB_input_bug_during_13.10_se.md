---
title: "How do I work around USB input bug during 13.10 server install (apply patch to ISO)?"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by xyzman on 2014-01-01
Basically the problem was discussed here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1244176). What I miss is how to apply the proposed solution to the server installation image on my USB stick. Unfortunately, there is no way I can plug the PS2 keyboard in...

---

### Post by sudodus on 2014-01-01
Welcome to the Ubuntu Forums :-)

Do you need version 13.10, or would it work well enough with the long time support version 12.04 LTS?

---

### Post by xyzman on 2014-01-01
I need 13.10 for [this]("http://forum.xbmc.org/showthread.php?tid=174854") XBMC setup. I discussed the possibility of using other Ubuntu builds with XBMC fork maintainers over IRC, but they say that 13.10 is the only option... Tried the desktop version as well, but neither keyboard nor mouse are recognized by GUI.

I am not that good in Linux architecture despite using Ubuntu for several years - the patch seems to be dealing with kernel package update, so can I somehow package different kernel (like from 14.04 daily build) to installer?

---

### Post by sudodus on 2014-01-01
Yes it is possible. If you activate a PPA or the ***proposed*** repository, you can install linux-image-(whatever-version-number) with ***sudo apt-get*** or ***synaptic***. But I think there are [COLOR=#ff0000]other people who can help you in a better way[/COLOR] to select what kernel to install and how to do it.

---

### Post by xyzman on 2014-01-01
I worked around the core issue by using [this]("http://www.buyincoins.com/item/339.html") PS2->USB adapter and PS2 keyboard from 90s. Still, I'd like to see the problem being solved the proper way.

---

### Post by sudodus on 2014-01-01
I'm glad you have something that works now :-)

That bug seems to have high priority, so I think we'll find a bugfix soon. It will be generally available after some testing.

---

