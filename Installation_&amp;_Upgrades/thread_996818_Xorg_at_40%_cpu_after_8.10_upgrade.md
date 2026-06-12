---
title: "Xorg at 40% cpu after 8.10 upgrade"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by muycapaz on 2008-11-29
Not exactly 40% but always between 30% and 50%.  I've searched Google and apparently my graphic chipset (Intel 82845G/GL[Brookdale-G] according to sysinfo) can be a problem.  Here's what I've blindly done with no improvement:
[LIST]
[*]>sudo dpkg-reconfigure xserver-xorg
[*]added INTEL_BATCH=1 to /etc/environment
[*]reinstalled package xserver-xorg-video-intel
[/LIST]

Yes, I rebooted after each change and, yes, I reran the dpkg-reconfigure after the video-intel reinstall.

I have an old Compaq laptop running 8.04.1 and Xorg is generally around 10% or less and this old dog is now a lot "snappier" than my 8.10 system where before the upgrade it less so.

Any pointers appreciated.

---

