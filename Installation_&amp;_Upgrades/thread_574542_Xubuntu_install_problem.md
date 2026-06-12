---
title: "Xubuntu install problem"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by MobiusNZ on 2007-10-12
Hey guys,

I've just installed Xubuntu on a system I'm going to use as a media centre. The install went fine, except for one thing: When the installer wrote the partition changes to disk, and fstab, the desktop picked up the new drive and mounted it, causing the formatting the installer was trying to do to fail. This has happened before when I last installed Xubuntu... the only way round it I've found is to quickly right-click on the desktop volume icon and unmount before it starts to format.

Any ideas on how to sort this one out for future reference?

---

### Post by ryanVickers on 2007-10-13
Before you start doing things with partitions, go in System > Administration > Removable Devices and Media and un-check auto-mounting new stuff ;)

---

### Post by MobiusNZ on 2007-10-13
Cheers,

How's a new Xubuntu user going to know that? I'd think the live cd should have it preset, at least for non-removable partitions... :S

---

### Post by ryanVickers on 2007-10-13
oh, ***x***ubuntu, right ;)  That was the gnome menus, but I imagine the feature is still present somewhere ;)

Yeah, it should detect to see if partitioning software in running and automatically disable it!

---

