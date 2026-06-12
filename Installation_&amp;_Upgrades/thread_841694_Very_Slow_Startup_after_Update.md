---
title: "Very Slow Startup after Update"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by 9v1cl0 on 2008-06-26
I just upgraded from Ubuntu 7.10 to 8.04.  Now it takes a very long time to boot up completely.  The desktop boots up almost instantly but the panels take about 10 minutes more.  It worked fine before the update.  Any ideas on what is wrong?  Thanks

---

### Post by 9v1cl0 on 2008-07-07
Please Help

---

### Post by Rallg on 2008-07-07
Do you also see the same behavior if you select "Gnome fail-safe" at the login screen? If the panels load much faster in fail-safe mode, it may mean that you somehow "updated" to an incompatible driver.

Whether or not that happens, try this: Boot to recovery mode. When you finally get the command prompt, do

sudo apt-get update && sudo apt-get dist-upgrade

That will obtain required software (if any) that might not have been in the package when you upgraded. When it settles down, re-boot normally. If the re-boot causes a problem, then re-boot a second time.

---

