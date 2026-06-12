---
title: "Upgrade to 2.6.20-16-generic kernel is causing system lock-ups"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by SeanHodges on 2007-06-02
I upgraded to the recent kernel 2.6.20-16-generic when it became available (I think about a week ago?), but I've been experiencing some complete system lock-ups since I upgraded.

Here are some of the usual offenders on my system:

- I'm running Ubuntu in 386 mode on an AMD64 Dual-core (some people suggest this can have problems in small cases, though i've not had any problem until now)

- I'm using the proprietory nvidia driver, installed via the restricted drivers utility. Havent tried removing/upgrading it yet, but hoping to solve this without tainting my repository if possible.

- I'm using a wireless card, although since Fiesty it has been working great out-of-the-box with the native rt61 driver

The lock-ups appear to be random, sometimes while I'm using it, and sometimes while in screensaver mode.

I've rolled back to using the previous 2.6.20-15-generic kernel (selecting it as default in Grub), and my lock-ups have disappeared!

Has anyone else got this problem? any ideas?

---

### Post by LarsBjerregaard on 2007-06-02
Hi Sean

You will probably find the main discussion (all 45 pages of it) of your problem going on here:
[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

My advice: Stay tuned to:
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996](https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314)

---

