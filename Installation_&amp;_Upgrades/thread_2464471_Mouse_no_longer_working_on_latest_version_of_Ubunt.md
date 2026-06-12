---
title: "Mouse no longer working on latest version of Ubuntu LTS."
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by mikesa2 on 2021-07-02
I have recently installed the latest LTS version of Ubuntu and initially there were no issues.  Everything worked fine.

However, since yesterday, as soon as I click on a browser icon (Firefox, Chrome, Opera) or click on a program icon (e.g. Thunderbird), neither the browser or the program launches.  Instead, the mouse simply freezes and no longer works.  I then have to turn off the power as no way can Ubuntu be shut down otherwise.  What could be the problem?

In the circumstances, is there any way to re-install Ubuntu but keeping all my files and settings and not removing any installed programs?  If not, is there a way to restore the mouse function?  I have also tried another mouse but in vain.  The issue did not resolve.  Can someone please advise what I need to do?  Thanks.

---

### Post by tea for one on 2021-07-02
> **mikesa2 said:**
>  I then have to turn off the power as no way can Ubuntu be shut down otherwise.

This is generally not a good idea because it can damage the file system. It would be more graceful to use REISUB.

Unfortunately, Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the _B_ for an **O**

[https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)

---

