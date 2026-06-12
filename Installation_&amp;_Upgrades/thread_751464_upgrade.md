---
title: "upgrade"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by rlittler2001 on 2008-04-10
can someone tell me how to ugrade from ubuntu 5.10 to ubuntu 7.10

---

### Post by tamoneya on 2008-04-10
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)
It doesnt talk about 5.10 since it is not supported any more but it does mention 6.06.  I would follow those directions and it should work.

---

### Post by gunksta on 2008-04-10
As Tamoneya already mentioned 5.10 is no longer supported. Thus, the developers have probably not looked for potential gotchas when upgrading from 5.10 to 7.10.

Thus I believe upgrading could be tricky and have unexpected side affects - In other words strange stuff might break.

I would recommend backing up all of your data and doing a fresh installation of 7.10. If this is impossible, I would recommend upgrading to 6.06 (I am sure there are posts here in the forum to help guide you / fix things). Once you have confirmed that this upgrade is stable, you should be able to proceed upgrading to 7.10 more safely.

Obviously, this will take significantly longer than a fresh install unless you have a lot of data you have to back up first. But, it will work. 

Furthermore, if you have edited any files by hand, such xorg.conf or added non-standard repositories the odds that something will break go up significantly, unless you can restore the original .conf files and uninstall the non-Ubuntu applications.

---

### Post by zvacet on 2008-04-11
To upgrade from Breezy to Dapper look [here.](http://ubuntuforums.org/showthread.php?t=746011&highlight=breezy)When you have Dapper you can upgrade directly to Hardy,but wait until Hardy becomes stable(two weeks).

---

