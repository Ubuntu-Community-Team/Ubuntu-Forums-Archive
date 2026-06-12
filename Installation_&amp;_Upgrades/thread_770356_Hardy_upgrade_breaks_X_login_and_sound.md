---
title: "Hardy upgrade breaks X login and sound"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by steevc on 2008-04-27
I ran the upgrade process from Gutsy and it ran with no problems. When the PC rebooted I didn't get the the graphical login. Logging into the console I tried startx, but that got errors until I changed the driver back from nv from nvidia. Then I could run KDE. At least I can set high scan rates that were not available before.

Rebooting again still got no login screen. Whatever it was doing the monitor could not sync to it. So I'm stuck with console login and startx for now. I've not tried reconfiguring from scratch yet.

Within KDE I have a couple of issues. I'm getting no sound at all, but no errors when I play in Amarok. Could this be related to Pulse Audio?

Also the KDE MediaManager is not running, so I don't see storage media in Konqueror.

Most applications seem to be working, but lack of sound is a serious handicap.

I'll give this upgrade 8/10 so far.

---

### Post by dentaku65 on 2008-04-27
Can you post the output of:
```
uname -r
```

---

### Post by steevc on 2008-04-27
I get

2.6.24-16-generic

---

### Post by dentaku65 on 2008-04-27
> **steevc said:**
> I get

2.6.24-16-generic

Try to istall this package:
```
sudo apt-get install linux-ubuntu-modules-2.6.24-16-generic

```

---

### Post by steevc on 2008-04-27
> **dentaku65 said:**
> Try to istall this package:
```
sudo apt-get install linux-ubuntu-modules-2.6.24-16-generic

```

I already had the latest version.

Thanks for helping.

---

### Post by steevc on 2008-04-29
I seem to have solved the main issues. I got the login screen back by finding an old xorg.conf with more settings. The new one was very sparse. Before that I managed to lose my mouse cursor when I did startx. That was frustrating.

The sound issue was as simple as turning up a channel in KMix, but I don't get that channel in my session. It appears in someone else's.

Thanks anyway.

---

