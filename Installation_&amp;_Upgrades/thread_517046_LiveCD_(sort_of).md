---
title: "LiveCD (sort of)"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by kg4mxz on 2007-08-04
Right now I am running Kubuntu off of an external hard drive set up with persistence.  However, the company which I work for requires software to be installed requiring Feisty (persistence doesn't work in feisty without a patched kernel). What I would like to do is install Kubuntu to the external hard drive and somehow have the installation harness the power of the livecd's auto hardware detection system, as I would like to still be able to use multiple computers with this external hard drive installlation.  Has anyone ever tried this / is it possible?

Thanks,
kg4mxz

---

### Post by aysiu on 2007-08-04
The live CD and the installed version have the same hardware detection system--it's called the Linux kernel.

---

### Post by kg4mxz on 2007-08-04
Right... But the last time I tried doing that, I had to manually configure X to use a different graphics driver each time I switched laptops or it would wouldn't boot into kdm... That was on Mandriva though, I don't know if Kubuntu is any different...

---

### Post by aysiu on 2007-08-04
> **kg4mxz said:**
> Right... But the last time I tried doing that, I had to manually configure X to use a different graphics driver each time I switched laptops or it would wouldn't boot into kdm... That was on Mandriva though, I don't know if Kubuntu is any different...
Well, you'll have to do that with any installation.

It has nothing to do with harnessing the power of hardware detection. An installation is static and has an X configuration. Once it's configured, you have to configure it again when you're changing setups. The same thing happens when you boot a live CD, because it is not a static installation.

Maybe you could save several different versions of the /etc/X11/xorg.conf file and create a little shell script that allows you to easily switch between them, depending on what computer you have connected?

---

### Post by kg4mxz on 2007-08-04
will do... Thank you much aysiu

---

