---
title: "installing wireless packages= broken keyboard?"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by phobophilia on 2008-08-21
Oh great internet gods of ubuntu:

I haven't been able to get my wireless card to play nice with ubuntu 8.04, so yesterday I downloaded some wireless packages from the synaptic package manager. (I couldn't exactly tell you which ones they were- sorry.) I restart the system, and my keyboard no longer works properly- pressing a key gets either nothing, or a huge line of that particular character. (I.e., dddddddd) 

I can't log in through the usual startup screen, and the keyboard still doesn't behave in recovery mode. (The keyboard does work while using the windows part of the hard disk.)

Is there any command to undo/erase all packages downloaded on a certain date?

Muchos gracias,
-P

---

### Post by pytheas22 on 2008-08-21
> Is there any command to undo/erase all packages downloaded on a certain date?

I don't know of a way to do that automatically, but if you open Synaptic (Applications>Administration menu) and go to File>History, you can see which packages you downloaded before the problem started.  Then you can use Synaptic or apt-get to uninstall them.  Hopefully you have a keyboard that works that you can use to log into Ubuntu to get this done.

Also, if you get this solved, I'll help with the wireless too if you post:

```
lshw -C Network
lspci -nn
lsusb
```

and tell me exactly why it wasn't "playing nice."

---

