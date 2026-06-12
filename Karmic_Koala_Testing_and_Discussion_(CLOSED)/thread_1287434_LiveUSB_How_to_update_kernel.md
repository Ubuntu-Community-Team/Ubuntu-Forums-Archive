---
title: "LiveUSB: How to update kernel?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2009-10-10
I have a LiveUSB created with the "USB Startup Disk Creator" in Karmic. On the LiveUSB, I also have Karmic installed.

Today, a kernel update was available. I did a 'sudo aptitude safe-upgrade' and I got the following message:
```
update-initramfs is disabled since running on read-only media
```
So, I guess the new 2.6.31-13 kernel has not been installed. However, as I want to keep my USB stick up to date, I would really like to update my kernel. Is there a possibility to do this?

---

### Post by hal10000 on 2009-10-10
some usb sticks have a small switch to turn on/off read/write-mode

---

### Post by andrewabc on 2009-10-10
I presume you have persistent option when you created it so you can save stuff to it?

I tried liveusb of jaunty and tried installing stuff, but I think it only installs stuff to /home, I remember trying to install a piece of software and it failed.

Maybe they changed that since then.

Do not attempt to 'install' ubuntu to the usb stick as grub will point to it and you'll mess everything up.

---

### Post by ernstblaauw on 2009-10-10
> **andrewabc said:**
> I presume you have persistent option when you created it so you can save stuff to it?

I tried liveusb of jaunty and tried installing stuff, but I think it only installs stuff to /home, I remember trying to install a piece of software and it failed.

Maybe they changed that since then.

Do not attempt to 'install' ubuntu to the usb stick as grub will point to it and you'll mess everything up.
I have indeed the persistent option enabled and all other updates do install fine, so that's not the problem. I guess it has something to do with the fact there is no grub; you cannot select a kernel at all when booting.

Do other people have some idea how to apply kernel updates?

---

### Post by ernstblaauw on 2009-10-13
I've created a Launchpad entry: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/450259](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/450259)

---

### Post by Luffield on 2009-10-13
> **ernstblaauw said:**
> I have indeed the persistent option enabled and all other updates do install fine, so that's not the problem. I guess it has something to do with the fact there is no grub; you cannot select a kernel at all when booting.

Do other people have some idea how to apply kernel updates?
The only way I can think of is installing a normal version of Ubuntu on a USB stick. I'm actually posting this from an old laptop that recently developed a problem with the motherboard causing it not to recognize its hard drive and its DVD drive - but luckily, the USB ports still work. I booted it from a live USB stick and it ran well, so I did a full installation on another USB stick and it worked even better - it's faster (although quite slow sometimes) and I can use it just as I use my other computer, including kernel upgrades.

---

