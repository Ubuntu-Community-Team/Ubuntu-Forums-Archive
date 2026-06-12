---
title: "Need a little help with ZFS Fuse"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by terryb8s on 2011-05-22
Hey Guys/Gals,

I need a little help moving my ZFS pool (RAIDZ1) from freenas 0.72 to Ubuntu 11.04 Desktop or Server AMD64.

I have installed ZFS-Fuse, had a look at doing a ZFS import but the pool doesn't seem to show up.

I'm not sure how to proceed, I have read some forum posts that say that an export needs to be done but I'm not sure how to do this.
:confused:
Cheers

---

### Post by fineghal on 2011-06-10
Need a little more information.

Are these separate machines that you're physically moving the drives/raid from? 

Have you re-installed the OS on the machine?
Did the installer touch your zpool drives?
Which version of zfs-fuse are you running?

I am unsure if freenas has a gui option for this, but if the installation still exists, you should ssh in, switch to root and run a 'zpool export naspool' or whatever the name is. 

You might try using the latest version of zfs-fuse, as I recall the one in the ubuntu repository is a bit out of date.

What does 'zpool import' give you as output? If run without arguments it should scan and then list all available storage pools.

---

