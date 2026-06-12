---
title: "Hardy will not boot after upgrade"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Billabond1 on 2008-08-17
Hi all,

I have just installed the newest Kubuntu.  I went to upgrade everything (used terminal, not adept).  After the upgrade (which appeared to be successful), I rebooted the machine.  Now, upon booting, the grub screen will come up real quick, then a screen that says "starting up" in the top left corner.  As soon as the start up screen goes away (1 or 2 seconds), the computer reboots.  This happens every time.  Tried the recovery mode, but this does the same thing.

Any help would be appreciated.  Thanks in advance.

---

### Post by Billabond1 on 2008-08-18
I decided to do a fresh install.  After the install, i ran the upgrades again. Same problem.  I can not figure out what is wrong, there is no errors or anything.  Please help.

---

### Post by tropdoug on 2008-08-23
Seems you not getting many replies, perhaps this will stimulate some. 

I have an almost similar problem, but mine just sits on the comment 'starting up' and goes nowhere. I think the issue might be that Grub has not been written correctly see 

[http://ubuntuforums.org/showthread.php?t=873546](http://ubuntuforums.org/showthread.php?t=873546)

which is slightly different but might be what we are both looking for. I am about to try this again.

Doug

**Yes that was the problem. Re write Grub to fix per thread above.**

---

### Post by Sef on 2008-08-23
Can you boot into the system using an older kernel?

---

### Post by Partyboi2 on 2008-08-23
Maybe one of these bug reports might help.
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/15531](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/15531)
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/26058](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/26058)

---

