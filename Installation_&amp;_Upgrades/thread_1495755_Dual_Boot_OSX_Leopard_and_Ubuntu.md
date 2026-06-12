---
title: "Dual Boot OSX Leopard and Ubuntu?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by jamesbeat on 2010-05-28
I have been an Ubuntu user for several years now, but when I got an iphone, I had to install Windows XP on a partition so that I could use itunes properly.

It occurred to me the other day that I could use OSX instead, so that I could rid myself of Windows once more.

The installation went ok, but when I tried to restore Grub, I hit a problem.

When I installed Windows, I used this guide to restore Grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I am using Grub Legacy.

When I tried to use the same technique to restore Grub after installing OSX Leopard, it didn't work.

I typed this:

sudo grub

> root (hd0,0)

> setup (hd0)



I know that I should be using (hd0,0) because that's what I used before with Windows, but now it gives me an error message telling me that it couldn't mount the partition.

I can mount the Ubuntu partition with the live cd and view my files as normal.

Any ideas?

---

