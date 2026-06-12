---
title: "Saving bandwidth and updating two systems"
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by oygle on 2015-08-26
Using mobile broadband with limited bandwidth. Have two systems running Kubuntu, one a 64 bit desktop, the other a 64 bit laptop.

If I have them both on the same 64 bit version of Kubuntu, can I simply keep one (say the desktop) updated, and then copy the .DEB files over to /var/cache/apt on the laptop ?

After the copy/sync , what should be run on the laptop to ensure all is updated, WITHOUT going out to the internet ?

These 2 computers are connected via a router. What file sharing application is the best and easiest to use ?  (samba, etc). I don't have any file sharing between them as yet.

---

### Post by papibe on 2015-08-26
Hi oygle.

I have a similar situation, although not mobile. I have a bunch of machines running 32bits and another bunch running 64bits.

Currently I am very pleased with **apt-cacher-ng**. I acts sort of like a a web caching proxy but for deb packages. The first machine you upgrade would force the service to download the packages from the Internet and cached them locally. When the next machine upgrades, the service realize that the packages were cached and serve them over the LAN. Not only you save bandwidth, but from the second machine forward the updates are very fast!

There's no much tutorials I can point you to, but I'd be happy to help you setting it up.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by oygle on 2015-08-26
Hi papibe,

Thanks for your reply. I see there are some docs at [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server) , but seems a bit messy. Will take you up on your offer to help. Just need a little bit of time to make the desktop the same version of the laptop.

---

### Post by papibe on 2015-08-26
Yes, that it is a bit messy. It is actually much simpler than that.

This it is a little better. Not well formatted, but instructions are more accurate: [apt-cacher-ng automatic proxy configuration]("http://ubuntuforums.org/showthread.php?t=2061528&highlight=apt-cacher-ng"). Note that the import part is optional. It has some benefits, but it is not mandatory.

I wouldn't bother making an effort upgrading your machine so that all versions are equal. I won't save you bandwidth, and you won't be doing much caching at all ;)

First things first, let's do a little of design.

I have apt-cacher-ng running on my home server. It works great because it is, almost, a 24x7 service. Every time I need to upgrade a machine, even the server itself, the service will be running and caching.

One disadvantage of this method is that you won't be able to upgrade if the service is down (actually you can, but you need to mod some files. It just brakes the transparency).

If you don't have a server, I believe the desktop could be a good candidate since it is easier to have it on most of the time.

Let us know how it goes.
Regards.

---

