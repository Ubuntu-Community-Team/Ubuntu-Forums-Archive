---
title: "Can't boot from USB LiveCD"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by karl_eller on 2010-04-18
I'm trying to boot off a USB LiveCD of Ubuntu 9.10 in order to save some data off a botched UNR install. However when I try to boot off said USB drive, I get this error:

```

process 2425: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending != NULL" failed in file dbus-pending-call.c line 596

```

The error repeats constantly until I turn off the netbook (EeePC 1008HA).

I've tested the USB drive using the "Check disk" option in the boot menu, and it comes up clean.

Any ideas why this is happening?

---

### Post by kukker32 on 2010-04-18
why are you using usb live cd?

try burn a live cd instead..
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

if not working try mount The .iso i mean there's a place in the installation program is some "help me boot"..

try this first and tell me what happens.

---

### Post by karl_eller on 2010-04-18
> **karl_eller said:**
> netbook (EeePC 1008HA)
Netbook, so no CD drive ;) And I can't mount the ISO if I don't have an OS to boot into.

As a further update, I've re-written the .iso to the USB drive, in case it was corrupted. It'll boot to the LiveCD's boot screen (where it has options to run live CD, install, check disk, etc), and if I run the "Check this CD for defects", everything comes back fine. If I run Ubuntu from the live CD, it will start to boot, get to "Running /scripts/init-bottom" and then hang there for a minute or two, before the screen goes blank and then it starts displaying the error in my initial post.

---

### Post by kukker32 on 2010-04-18
which version of ubuntu are you trying to boot??

---

### Post by karl_eller on 2010-04-18
I've tried Ubuntu 9.10, Ubuntu 9.10 Netbook Remix and Kubuntu 9.10, all of which fail (although Kubuntu gives a different error).

---

### Post by kukker32 on 2010-04-18
i have a notebook acer extensa 5230E. (with cd drive :D )
and im running ubuntu 9.10 gnome
try 10.04 LTS.. or a different usb stick..
or if your desperate :P try change your computers boot order in the bios (f2, del, esc, f8, f10) i dunno which key under startup...

---

### Post by karl_eller on 2010-04-18
I've tried a number of different USB sticks with a few different distros, and they've all failed to run properly.

I ran MemTest for 8 hours overnight, so I don't think it's a memory problem.

---

### Post by utnubuuser on 2010-04-18
I've found I can only boot live-USB created with 9.04.

---

### Post by karl_eller on 2010-04-18
It had worked before, obviously, since I had installed UNR 9.10 on the netbook using a USB drive. That ran fine for about 2 months until it started freezing up with a kernel panic yesterday. While trying to fix that, I managed to toast GRUB2, which I need a LiveCD to fix, and I can't do that because I can't get a LiveCD to boot.

---

### Post by karl_eller on 2010-04-19
So I've managed to get it to boot off a LiveUSB by disabling ACPI and the like, as well as using a shiny new USB drive, so this problem looks like it's solved itself...

---

