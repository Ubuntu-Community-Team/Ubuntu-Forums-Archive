---
title: "Nvidia driver doesn't persist through kernel updates?"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by theanswriz42 on 2010-03-07
I updated to 2.6.32-15-generic today, rebooted and noticed my system kept going into low graphics mode. Is there a way to get it to persist through kernel updates?

Cheers

---

### Post by Funnnny on 2010-03-07
I have one guide here, wrote by reading some guides in here. I'm just can't find those old guides...
It probally the problem that your driver wasn't got recompile when kernel update
[http://nguyenthanhcong.com/reconfigure-nvidia-driver-for-the-new-kernel/](http://nguyenthanhcong.com/reconfigure-nvidia-driver-for-the-new-kernel/)

---

### Post by theanswriz42 on 2010-03-07
Sweet, thanks!

---

### Post by psyke83 on 2010-03-07
Let me make a suggestion, to you and anyone else who wonders why it's necessary to recompile the NVIDIA driver with each kernel update: don't install using the upstream tarball, ever*.

The reason why you need to recompile the driver with each kernel update (using instructions such as the blog post listed above), is because you are not taking advantage of the automatic integration provided by Ubuntu's nvidia packages.

The nvidia-{current|180|173|96} packages use [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") to automatically rebuild the kernel modules with each kernel update. Most users should be using these packages, and will never have problems with kernel updates.

*Obviously there are exceptions - if you have a new card that needs the latest bleeding-edge driver, or if you're an advanced user, go ahead and compile the drivers from the upstream tarball. If you were an advanced user, however, you would have known that it was necessary to manually re-compile the driver and wouldn't have started this thread.

---

