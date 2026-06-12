---
title: "Can't install Server amd64"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by noblealaric on 2011-07-12
For whatever reason, I cannot for the life of me install server amd64 on my server machine. I have a quad-core phenom 1st gen. USB/CD/HD, it doesn't matter what media its from. It randomly freezes on unpacking or configuring, the steps after configuring the network. If I shutdown, I can sometimes get further, or sometimes its shorter. I can't have it connected to the internet when installing or it goes bonkers. I have tried most of the fixes suggested around the forums, to no avail. 

Now here is the crazy thing, I installed Ubuntu 64 Desktop with no problems. So for now, I will continued to install desktop and using tasksel to change it to a server.

Oh BTW, I just found out installing desktop works, but I have had this server install problem since Gutsy. The 32bit version installs just fine.

---

### Post by tgalati4 on 2011-07-12
Sounds like a module problem.  Do an lsmod on both the desktop and server installs and see what the difference is.

It could also be the default configuration settings of the kernel--there are differences between the desktop and server.  If, after you install the server from the desktop, it locks up, then you can be reasonably sure that it's a kernel configuration setting.

I would try an alternate disk install of the server.  Do a "CD Check" to make sure that you have a good burn.  If the machine crashes during install, then reboot with a desktop LiveCD and see if there are any log files in /var/log.  There should be some clues left behind.

If this is a home server machine, then simply run the desktop version and load your services.  With a quad-core machine, the graphical load is quite small (1 to 2% perhaps).

---

