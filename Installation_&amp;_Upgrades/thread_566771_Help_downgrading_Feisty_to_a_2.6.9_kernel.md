---
title: "Help downgrading Feisty to a 2.6.9 kernel"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by mattmull on 2007-10-03
Hi,

I'm trying to get Ubuntu Feisty working with Clearcase, but I need to use the RedHat ES4 2.6.9 kernel in order to build and load a Clearcase module.

I can boot and load all the modules I need, but my /dev tree is missing a ton of entries.  I know somewhere along the way from 2.6.9 to 2.6.18, things started switching over from devfs to udev, so I'm guessing that's the problem.  I tried creating the /dev entries I needed by hand, but I still had funkiness with network mounts, hotplugging of devices, and a bunch of other stuff.  The RedHat ES5 kernel actually works perfect with Feisty, but the Clearcase version we use only supports up to ES4.

I tried Dapper, but it looks like the /dev file system works the same way as Feisty.

Has anyone downgraded to a much earlier 2.6 kernel successfully, or can someone point me in the right direction.

Thanks.

---

### Post by peabody on 2007-10-03
Not sure what Clearcase is.  Any chance you'd be able to run the RHEL or CentOS version of Linux you need in something like the free vmplayer?  Doing what you want to do sounds like it's going to be a pain.

---

