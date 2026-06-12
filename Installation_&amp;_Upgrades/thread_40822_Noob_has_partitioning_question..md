---
title: "Noob has partitioning question."
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by Marrojj on 2005-06-10
To make a short story long..

I'm a noob trying to make the jump from M$ to Linux for the first time. My first attempt to install Ubuntu wasn't successful because my D-Link wireless pci card was not detected, and I had no way to log onto the internet to search for help. Apparently, I need to download drivers, and/or MadWifi, to configure the wireless card.. so I'm setting up a dual boot xp/ubuntu system - that way I can us xp to access the internet and download files, then switch to Ubuntu to work on setting up the card. Here's my question: How can I setup the partitions so that files I download with xp would be accessable in Ubuntu. NTFS is not Linux friendly, is it?

Regards,

John

---

### Post by dsmarty on 2005-06-10
You can create a fat32 partition, such a partition is supported by both Windows and Linux.
You can map the partition in windows as a drive and you can mount it in Linux.

If it's only necessary for read-only access you can mount NTFS.

```

mount -t ntfs [device] [mountpoint]

```

---

