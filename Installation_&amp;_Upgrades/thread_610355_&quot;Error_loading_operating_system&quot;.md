---
title: "&quot;Error loading operating system&quot;"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by PaddyMcNasty on 2007-11-11
I have a tiny little problem... I broke my new PC!

I have had it for 2 days, and I'd been playing games in Windows only so far. So I started installing Ubuntu today and after partitioning it started installing and quite near the start told me it couldn't install certain files due to an error which was probably caused by a faulty CD drive.

It then continued to install for about a minute then suddenly stopped. So I rebooted and it just comes up with "Error loading operating system".

So holding back the tears I inserted the Windows recovery CD and after appearing to do a whole load of nothing it asked me if I wanted to reinstall windows on one of the partitions or if I wanted to delete a partition. I got scared and turned it off after this.

Bearing in mind I'm a bit of a n00b, please to god help me!

Thanks
Patrick

PS If the only option is to swipe the hard drive I suppose I can do that cos I don't have any important files on the PC yet, just games. It's just such a pain!

---

### Post by PaddyMcNasty on 2007-11-11
PPS. Mesh PC
1.86 GHz Core 2 Duo
1GB RAM
250GB SATA hard drive
GeForce 7300GS

---

### Post by Cochise on 2007-11-11
try installing it again or install grub from the livecd that'll will let you boot windows at least

---

### Post by froy02 on 2007-11-11
If you're using vista continue with installation till you get to the choice install windows or repair installation. Choose repair installation.  You may get back windows.  Knowing the windows version will make it easier to answer your question.

---

### Post by PaddyMcNasty on 2007-11-12
Thanks for your responses, I did reinstall Ubuntu and it did the trick. Went for that because I'm running XP not Vista (don't trust it yet). It seems that the error occurred in reading the disk not writing it (I think and thank God) so it went smoothly this time round. Except that is for some security updates, but I can install them once I get the restricted drivers for my wireless card working and can get on the net.

There was a scary moment when I selected Windows to boot into, went away and came back to find it had loaded Ubuntu. But it worked fine when I restarted so my guess is that Windows just crashed when I went away (surprise surprise).

Anyway, thanks for your help,
Appreciate it
Patrick

---

### Post by bulldog on 2007-11-12
> **PaddyMcNasty said:**
> Thanks for your responses, I did reinstall Ubuntu and it did the trick. Went for that because I'm running XP not Vista (don't trust it yet). It seems that the error occurred in reading the disk not writing it (I think and thank God) so it went smoothly this time round. Except that is for some security updates, but I can install them once I get the restricted drivers for my wireless card working and can get on the net.

There was a scary moment when I selected Windows to boot into, went away and came back to find it had loaded Ubuntu. But it worked fine when I restarted so my guess is that Windows just crashed when I went away (surprise surprise).

Anyway, thanks for your help,
Appreciate it
Patrick
 FYI,grub will be loading ubuntu by default [10 seconds I think]
In this time you can choose to boot an other OS which should be listed in grub.
You have three entrys for ubuntu,though,and just one for windows.

This can be changed if you want to boot to windows by default.

---

