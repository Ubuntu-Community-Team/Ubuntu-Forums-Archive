---
title: "Upgrade to 11.04 failed"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by wagnersblackberry on 2011-05-05
I ran the software manager upgrade/update install of 11.04. When I reboot almost immediately a quick error flashes on screen that says something like "missing prefix" then it goes to an unfamiliar menu with kernel choices that are very old and look nothing like my desktop. I think it may be some old install or something I dont know. I have an eee pc. I originally installed with WUBI but have done other kernel upgrades with no issues.

---

### Post by bcbc on 2011-05-05
That "prefix not set" message is expected, and harmless (according to the grub developer.) I've been running a wubi natty and it appears every time you boot.

The new kernel should be 2.6.38-8. If you don't see that, then why don't you boot up a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That might help figure out what's going on. Also, when you upgraded did you get any errors or messages that indicated something strange was happening?

---

### Post by riddz on 2011-05-11
> **bcbc said:**
> That "prefix not set" message is expected, and harmless (according to the grub developer.) I've been running a wubi natty and it appears every time you boot.

The new kernel should be 2.6.38-8. If you don't see that, then why don't you boot up a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That might help figure out what's going on. Also, when you upgraded did you get any errors or messages that indicated something strange was happening?

I upgraded to 11.04 while 10.10 was installed with wubi. but after when i reboot "prefix" is not set appears...!!!!! however windows still boot up normally..

---

