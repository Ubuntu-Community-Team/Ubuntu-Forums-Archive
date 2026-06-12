---
title: "offline nvida install"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by ChazZeromus on 2008-07-26
What exactly do I need for an offline nvidia driver installation?  I have downloaded the Ubuntu DVD instead of the CD, so what do I still need besides the nvidia driver installation run file I got from nvidia?

---

### Post by pytheas22 on 2008-07-26
You don't need to use the .run file from nvidia.  You can use Ubuntu packages instead; it's much easier.  I'm not sure, however, if the packages for the nvidia closed-source driver are on the Ubuntu DVD.  If you enable the DVD as a repository (using the System>Administration>Software Sources utility) and then open up Synaptic (System>Administration>Synaptic Package Manager), you can search for 'nvidia.'  Do you see the driver listed?  If so, you can install it.

Otherwise, you will have to grab the nvidia package another way.  If you can get an Internet connection temporarily, that would be by far the easiest way to do it.  If you really can't get online at all, there are other ways to do it, but I won't list the steps (because they're long) unless you need them.

---

### Post by ChazZeromus on 2008-07-26
Oh well, can you give a link please?  And I really hope by having the DVD, it can solve most problems.

---

### Post by pytheas22 on 2008-07-27
You can download the nvidia package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then transfer it to your Ubuntu computer (using a USB driver or whatever).  The problem is that you may need to install other packages first, before the nvidia driver will work.  If that's the case, the installer will tell you which ones you need, and you'll have to go back to packages.ubuntu.com to find them.  But with some patience, you can get it done this way.

But as I said, I would first check to make sure that the nvidia proprietary driver isn't included on the Ubuntu DVD, because that would be easier than manually tracking down the driver package and its dependencies.  Or, again, see if there's any way to get your machine on the Internet temporarily, and you can use [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to easily get the driver installed.

---

