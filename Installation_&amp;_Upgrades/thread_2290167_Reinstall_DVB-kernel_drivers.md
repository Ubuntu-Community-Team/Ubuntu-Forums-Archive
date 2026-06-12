---
title: "Reinstall DVB-kernel drivers"
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by viktorw on 2015-08-10
[Solved]
Hi!
I messed up my DVB-drivers, bad, I think.

The original preinstalled kernel drivers worked almost fine, the card initialized correct, I could scan for channels, but some of my recordings failed.
I tried the new v4l driver, it compiled fine, but at reboot I got the usual symbol error crap :P. 
So I tried uninstalling the new drivers, only resulting in nothing at boot. No even an error.

So I tried reinstalled my kernel thinking the original drivers would be installed again, but still nothing at boot.
> sudo apt-get install --reinstall linux-image-$(uname -r)

I tried installing other kernels, but still nothing at boot
Well, I tried installing one kernel (not in the repo) with 3 .deb files instead of sudo apt-get, and the card initialized fine, but then other problems appeared.

How do I get my original semi-working drivers back ?

Edit: Some info on my system:
I have an Ubuntu 14.04.2 LTS, currently running Linux 3.16.0-45-generic
I have a Nova-S-Plus DVB-S and a WinTV Nova-HD-S2

>  cx88xx: Unknown symbol i2c_bit_add_bus 
part of my dmesg

Edit again:
Never mind! I got it working with the older 3.13.0-57-generic kernel and the lastest v4l-dvb drivers. 
I have no idea what I did differently but it works, thanks anyway!!

---

### Post by wyliecoyoteuk on 2015-08-10
Som eless vague information might be a start.
What version of Ubuntu?
What make/model of tv card?

---

