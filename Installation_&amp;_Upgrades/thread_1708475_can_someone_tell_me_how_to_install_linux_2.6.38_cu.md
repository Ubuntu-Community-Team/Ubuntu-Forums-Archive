---
title: "can someone tell me how to install linux 2.6.38 custom kernel"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by jewfromdahood on 2011-03-16
I want to upgrade my custom "kosher" kernel on 2.6.35-27-kosher I made using git and this guide [http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/](http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/) my kernel I made has the 233 lines patch. So how exactly do I make a new Ubuntu kernel with 2.6.38, enable that scheduling in the make menuconfig or make xconfig and the localmodinfo as well. I want to get this new kernel as supposedly has better drivers and I hopefully finally can unlock the wireless N of my laptop and ditch G only as I kept is disabled as I got tired of resetting the wireless card every 1/2 hour from dropping from a bug in the n wireless on the Intel 5300 wifi. I also am using Ubuntu 10.10 amd64, using ATI fglrx drivers, not the ubuntu repo ones, the ATI ones from their site.

---

### Post by jewfromdahood on 2011-03-16
bump

---

### Post by dabl on 2011-03-16
You might want to try aptosid -- a 2.6.38 kernel is currently offered in the repository.  The Live CD is still at 2.6.37 -- you'll have to install, and then run dist-upgrade, to get a 2.6.38 kernel.

[http://aptosid.com/index.php](http://aptosid.com/index.php)

Otherwise, you need Ubuntu 11.04.  You can get a daily build CD image here:  [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by jewfromdahood on 2011-03-16
please explain how exactly should i do this?

---

### Post by jewfromdahood on 2011-03-17
bump

---

### Post by dabl on 2011-03-17
Make a Ubuntu 11.04 Live CD from the daily build ISO.  Boot it -- it uses a 2.6.38 kernel.  Test your hardware -- does your wireless card work better, or not?  If yes, then probably you will want to install 11.04 when it is released in a few weeks.

Building a custom 2.6.38 kernel, for use on your 10.10 system, is an advanced project -- not for the novice.  No one is going to teach you how to compile a kernel in a forum post.  Here are some places to start your studies:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)

---

