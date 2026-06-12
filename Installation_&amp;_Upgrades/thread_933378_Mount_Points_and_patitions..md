---
title: "Mount Points and patitions."
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by extruct on 2008-09-29
Hello, I reinstalled the whole pc including ubuntu, but before installing it I want suggestion about what to mount on different partitions.
Until now I used ~20GB for /
Around ~140GB for /home/
and 1GB for swap

But I also can mount different folders likes /usr /opt and etc.
What they mean? And is it worth to create a new partition for some of them? If yes how much space allocate for it?

Thanks a lot!

---

### Post by jemate18 on 2008-09-30
> **extruct said:**
> Hello, I reinstalled the whole pc including ubuntu, but before installing it I want suggestion about what to mount on different partitions.
Until now I used ~20GB for /
Around ~140GB for /home/
and 1GB for swap

But I also can mount different folders likes /usr /opt and etc.
What they mean? And is it worth to create a new partition for some of them? If yes how much space allocate for it?

Thanks a lot!

This might give you a hint.. This is my setup

(1) hard disk 80GB which is /dev/hda

This are my partitions and mountpoints

Device ----------Mounted on-------Size
/dev/hda1 -------- /boot -------- 100MB
/dev/hda2 ---------swap ---------2GB
/dev/hda5 ---------/--------------10GB
/dev/hda6 ---------/opt-----------5GB
/dev/hda7 ---------/usr/local-----10GB
/dev/hda8----------/home----------50GB

Note.... Swap is not mounted and cannot be mounted on any filesystem....
my RAM is 1GB the recommended size of swap is 2x your RAM....

Hope this helps

---

