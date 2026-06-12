---
title: "NVidia Legacy"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2006-06-05
I've seen a few posts about this, but I haven't seen a dfinite answer so I'm alittle confused.  I had installed the nvdia legacy drivers.  After upgrading to Dapper, I could not log in.  I realized it might be the drivers, so I reverted my xorg.config to use nv.  This solved that issue.  I checked Synaptic and it does not show a legacy driver for for the current kernel.  Does this mean I can use the regular driver or does it mean that the legacy driver has not been posted yet and I can't use the nvidia driver until it becomes available?

Thanks,

Steve

---

### Post by click4851 on 2006-06-05
I was wondering the same thing, I had the same issue, and reverting to my backup config. I'm down the road, but it begs the question, if there was a driver available, why didn't it at least update. Course this is probably related to the "media codec 2 step" everyone is dancing to. I will be glad when that ends.

---

### Post by CronoDekar on 2006-06-05
Should work, or at least I got the legacy driver working on my old comp.  Have you tried reinstalling the driver?  You have to do that whenever you change or upgrade your kernel.  I know I was pulling my hair out over it awhile back until I realized that one little in in tseliot's HowTo post and everything was working.

---

### Post by SteveF on 2006-06-06
I don't see a legacy driver for the new kernel installed during the upgrade.  Are you saying the old one should work or that I should use the regular driver instead of the legacy driver?

Steve

---

### Post by CronoDekar on 2006-06-06
You should still use the legacy driver.  I didn't even take a look at what the kernel number listed on the nvidia-glx-legacy driver was, and just now noticed it doesn't quite match with the kernel. (2.6.5.11 driver on the 2.6.15.22 kernel.)  Still works though, just gotta try to reinstall the driver I think.

---

### Post by tseliot on 2006-06-06
[QUOTE=SteveF]I don't see a legacy driver for the new kernel installed during the upgrade.  Are you saying the old one should work or that I should use the regular driver instead of the legacy driver?

Steve[/QUOTE]
You can use the legacy driver.

Please read Method 1 of this guide of mine where I also deal with legacy cards:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by SteveF on 2006-06-06
Well, you are both correct.  Not sure why it has to be reinstalled, but obviously it did.  I followed tseliot's method 1 and it worked without problems.

Thanks,

Steve

---

