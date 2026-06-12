---
title: "Update Manager shows gstreamer0.10-plugins-bad"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by xtiano77 on 2009-12-10
When I run the Update Manager, it always shows the following option, although I cannot check it:

gstreamer0.10-plugins.bad

Could anyone tell me what this is and how to fix it? Is it something wrong with my system?

Ubuntu 9.10
Intel Dual Core, Quad Processor
2GB Memory
500GB Drive

---

### Post by lemming465 on 2009-12-12
gstreamer0.10-plugins-bad contains dodgy multimedia codecs which might not work correctly.  It's a use at your own risk situation; the "bad" ones let you possibly play weird audio or video content you couldn't otherwise access.  They won't generally do harm to your system, other than messing up the playback, or at worst locking up something and requiring a reboot to recover your audio or streaming video.

If updates aren't working, the first quick fix try is to open a command terminal window, and try some package maintenance such as```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade -f
```
The next thing to try is removing the offending package and reinstalling it.  The third step would be to ask if you have any non-Ubuntu repositories such as Medibuntu enabled.

---

### Post by xtiano77 on 2009-12-24
It worked just fine. Thanks a bunch.

---

