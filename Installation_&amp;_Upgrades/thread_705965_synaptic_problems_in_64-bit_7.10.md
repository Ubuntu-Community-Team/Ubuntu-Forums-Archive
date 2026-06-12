---
title: "synaptic problems in 64-bit 7.10"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Godofgrunts on 2008-02-23
I'm running 64-bit Ubuntu for the first time and I'm have some major issues.

FIrst, firefox doesn't install any plugins, it all ways says that it cannot find them.
Second, synaptic doesn't seem to be working correctly. It comes up fine, but I cannot search for any packages or libaries other then the ones already on my system (I really need ia32-libs)
Third, I'm trying to install Folding at home SMP client. I know I need the above package but I thought I'd add this anyway.

Please help as I'm getting quite frustrated with the 64-bit version.

---

### Post by taurus on 2008-02-23
Make sure you have all the repos enable in /etc/apt/sources.list first before you attend to install anything else.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all lines except the last one, Source code, and Cdrom in the window below.  Close it and then press Refresh.  Now, see if you can Search for the packages that you have in mind.

---

### Post by Godofgrunts on 2008-02-24
Thanks so much! How come that isn't automatically enabled?

---

### Post by taurus on 2008-02-24
Because the installer couldn't detect your network during the installing process.  Instead of probing and probing, wasting time, it moved on to the next step, assuming your computer didn't have a network connection.

That's why all or most of your repos in /etc/apt/sources.list are disable, with a # in front.

---

