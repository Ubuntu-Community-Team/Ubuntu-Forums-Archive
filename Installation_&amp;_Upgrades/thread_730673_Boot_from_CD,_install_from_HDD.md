---
title: "Boot from CD, install from HDD?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Sted2008 on 2008-03-21
I'm trying to install Ubuntu onto an old laptop, unfortunately I can only get so far before the CD drive gives up.
With the normal desktop disk I can see the desktop but if fails to finish loading. With the alternative CD it fails when it is installing the software.
I have an external USB drive handy, unfortunately the laptop won't boot from USB.
Is there a way of booting from CD (or floppy) and then install from the USB HDD?

Thanks in advanced.
Steve

---

### Post by Peter09 on 2008-03-21
Might be worth telling us what the spec of the laptop is, RAM etc
PC

---

### Post by logos34 on 2008-03-21
> **Sted2008 said:**
> I have an external USB drive handy, unfortunately the laptop won't boot from USB.
Is there a way of booting from CD (or floppy) and then install from the USB HDD?

No, unfortunately.  There is something called an SBM (Smart Boot Manager) floppy, but it doesn't support USB boot, only internal cdroms.  

Do you have any version of windows installed on this machine?  Because if you did you could try this install from (internal) hard disk:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

Basically you'd just copy the alternate iso to the HDD and go from there. But that's no guarantee that the installation won't fail just like before.

Here's another (viable?) option:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by Sted2008 on 2008-03-21
Thanks to you both for replying.
My Laptop is a celeron 500, 256mb RAM, 6Gb Hdd

I wiped windows when I first tried to install, however I might try a small Linux distro (Damm Small Linux) and get that installed before the CD Rom gives up,  and do the install from Linux!

I'll let you know how it goes.

Cheers
Steve

---

