---
title: "Upgrade from 9.10 to 10.4 -&gt; boot issues"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by wheniwork on 2010-06-28
Upgraded to 10.04 and now my system will not boot. The screen hangs on the 10.04 load screen and when I look at whats happening I get this:

[IMG]http://wheniwork.com/other/photo-1.jpg[/IMG]


I did just have a bunch of issues with my RAID1 LVM filesystem, but fixed that due to my mdadm.conf having the array defined with drive letters (/dev/sdX1) etc. Fixed that by just using the UUID. But now this.

Looks like the boot device is mounting and starting to boot but then hangs on this screen. Any ideas? Where should I start?

Thanks for the help.

---

### Post by wheniwork on 2010-06-28
I think it has something to with when I ran:

```
update-initramfs -u
```

That messed something up. Perhaps it was something in my mdadm.conf that is not right. How can I redo the:

```
update-initramfs -u
```

Since right now it won't boot?

---

### Post by aphatak on 2010-06-28
I would try booting from a live CD.  Once you are logged in from the live CD, you can run commands on the hard drive that is giving you grief, edit configuration files, and do all sorts of corrective stuff.

---

