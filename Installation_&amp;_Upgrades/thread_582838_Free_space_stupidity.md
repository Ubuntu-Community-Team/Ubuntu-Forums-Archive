---
title: "Free space stupidity"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by zx80user on 2007-10-20
When attempting to upgrade to 7.10 from 7.04, I get this:

Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 220M free space on disk '/boot'. Please free at least an additional 9914k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Well, that is pretty silly! The total partition size, as created by previous installs, is about 220M and I cannot grow the partition easily. And clearly the upgrade does *not* need 220M of free space in /boot.

Is there any way to route round this (I am using sudo upgrade-manager) :confused:

---

### Post by Arenlor on 2007-10-20
There is something you could try
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
``` and see how that goes, but try deleting any old kernels you have that you don't need.

---

### Post by zx80user on 2007-10-20
That just gives me the same message:

Not enough free disk space
The upgrade aborts now. The upgrade needs a total of 220M free space on disk '/boot'. Please free at least an additional 9914k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I've already deleted every unused kernel, initrd and the rest.

---

### Post by Velociraptor on 2007-10-20
I get the same problem upgrading to gutsy :(

---

### Post by Velociraptor on 2007-10-20
I think I got this working :), go through the menu...

System -> Administration -> Synaptic Package Manager

Search for: linux-image

And mark all of the older kernel packages for removal, and click Apply. (I kept the kernel package that I currently boot with, but deleted all the other ones.)

For some reason that stops the /boot error message. Even though I had already manually deleted those older kernels from /boot. So /boot still has the same amount of free space after running the above. Weird.

---

### Post by zx80user on 2007-10-20
Thanks. Yes, that has fixed the problem. Clearly there is a bug in the installer, even if it is not a critical one.

---

