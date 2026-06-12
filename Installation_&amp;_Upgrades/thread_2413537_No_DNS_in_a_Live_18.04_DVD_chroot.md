---
title: "No DNS in a Live 18.04 DVD chroot"
date: 2019-02-26
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-02-26
I tried to upgrade a server from 16.04 to 18.04, unfortunately there were problems that left the system un-bootable but sort of accessible. Guess that's what I get for going to sleep. The greeting comes up and I can get into a recovery shell, unfortunately that shows there are a lot of unconfigured and possibly missing packages. I decided to try a chroot from a live cd but I'm having a problem.

The Live DVD boots and works, if finds the NIC and configures it and accesses the Internet.

I decided to try to use it to chroot into the root file system of the the failed upgrade and see if I can add the packages I need and get the thing configured. Unfortunately I can get into the chroot  but when i get there there is no DNS so downloading missing packages is impossible 

In the original live environment DNS works fine.

To get in the chroot I do this

```
# mount /dev/sda3 /mount
# mount -t proc /proc /mount/proc
# mount -o bind /sys /mount/sys
# mount  -o bind /dev /mnt/dev
# mount -o bind /dev/pts /mount/pts
# chroot /mount
# source /etc/environment
```

Does anyone know what I did wrong?

---

