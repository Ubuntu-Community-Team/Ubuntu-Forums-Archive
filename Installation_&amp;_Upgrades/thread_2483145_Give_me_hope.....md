---
title: "Give me hope...."
date: 2023-01-21
forum: Installation &amp; Upgrades
---

### Post by bejingie on 2023-01-21
After two years of happy Linux usage, I decided to try Ubuntu yesterday. Loaded 20.04 onto Dell laptop, 64 bit. Everything went great. With help from the web search, I found how to start an applmage and run my Arduino 2.0 program. Then I discovered that no external drive was mounting, neither thumb usb, or my terabyte usb hard drive, nor my Pico W. A web search shows many, many others with similar issues. I found from some advice that I could use the included app, called disks, to mount my devices manually. Ok. But, I need auto mount for some devices. Tons of advice online, but none worked for me.

Here is my question, and excuse my bluntness.

Why would such a widely acclaimed piece of software like Ubuntu, not be able to auto mount a usb drive or device right after a fresh install? And evidence online points to the fact that this issue is widespread. And why should I continue trying Ubuntu?

thanks

---

### Post by Impavidus on 2023-01-21
When I plug in a usb drive, it's mounted automatically. There are a few things that could be wrong.

What filesystem is on your external drives? For some, additional software may have to be installed.
Is the filesystem on the external drive damaged?
How do you attempt to access the external drives? Some software, in particular snaps, cannot access external drives.
Is your system configured not to mount filesystems when plugged in? All Ubuntu flavours with a GUI automount by default, but it can be disabled.

---

### Post by tea for one on 2023-01-21
> **bejingie said:**
> Why would such a widely acclaimed piece of software like Ubuntu, not be able to auto mount a usb drive or device right after a fresh install?
The following two quotes are found here [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
> By default, storage devices that are plugged into the system mount automatically in the /media/<username> directory
> By default, disk drives do not auto-mount in Ubuntu Server Edition

---

### Post by TheFu on 2023-01-21
> **bejingie said:**
>  Here is my question, and excuse my bluntness.

Why would such a widely acclaimed piece of software like Ubuntu, not be able to auto mount a usb drive or device right after a fresh install? And evidence online points to the fact that this issue is widespread. And why should I continue trying Ubuntu?

I appreciate bluntness.  I'll try to be just as clear.

In Unix, the power to mount is the power to destroy.  The ability to mount has always been reserved for the admins, not end users.  It was only when USB storage became widely used that attempts to allow use of that storage by end users was added.  Over the 2 decades since that first happened, a number of security failures have happened related to USB storage.  Most people don't care, until they see a problem directly.  99.9% of the time, a flash drive being connected to a desktop isn't a problem, but it is possible on most OSes, especially "that other OS", for USB devices connected to cause root-level access and to load device drivers automatically as an attack vector into the entire system.

What you see as an issue, I see as a security feature.  I'm still shocked that average users are allowed to mount storage. My Linux and Unix systems prevent that capability.  Others say that Ubuntu desktops (non-server) releases should have this auto access enabled by default. That is the intention, so not having it working seems like a bug ... or incompatibility with the USB controller or flash storage.  IDK.  

Typically, almost all flash storage just works for access with Linux, though there are definitely some flash drives that won't boot.  I don't think that is Linux-specific, since the boot aspects would happen before the OS is started. It would be a firmware/hardware thing in the computer, USB controller, and/or flash storage.

There is some software called autofs, which has been around since it was called amd/automounterd for the last 30 yrs.  I use this to mount SPECIFIC USB devices to specific location, with specific mount options.  This lets the system admin side of me feel better, since I control how, where and what are mounted.  It let's other users have access to their storage, provided it meets the criteria I configured to be mounted using autofs.  Additionally, autofs will umount storage automatically, if it isn't used/active.  That basically means that if no file is open on the storage for 1-2 minutes, the storage is umounted automatically.  For someone new to Unix/Linux, autofs is a little complex to setup.  There is an oddness for 1 part of the configuration, even for Unix people.  autofs works the same on all Linux distributions, but there isn't any GUI for it.  After setup, it handles things automatically.

Should you keep trying Ubuntu?  Only you can answer that question.  It is completely up to you.  I wrote a few articles for why I choose Ubuntu LTS over other options: 
[https://blog.jdpfu.com/2013/07/29/which-distro-do-you-run-why](https://blog.jdpfu.com/2013/07/29/which-distro-do-you-run-why) - picking a distro
[https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release) - why LTS matters

---

