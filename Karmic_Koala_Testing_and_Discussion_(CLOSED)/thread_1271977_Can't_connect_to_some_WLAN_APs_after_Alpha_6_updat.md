---
title: "Can't connect to some WLAN APs after Alpha 6 update"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by piquadrat on 2009-09-21
Hi,

since I did an apt-get update last Wednesday (I think), I can't get my laptop to connect to my home WLAN access point anymore. dmesg says this when I try to connect:

```
wlan0: disassociating by local choice (reason=3)
```

On another AP, it connects without problems. And on an Alpha 5 Live CD, it also works on my home AP. The WLAN card is from Intel (Intel Corporation PRO/Wireless 5100 AGN). Any ideas what the problem could be?

If nothing helps, I'd like to revert my installation to Alpha 5. Is this possible without doing a complete new install?

---

### Post by piquadrat on 2009-09-22
This is getting weird. If I start nm-applet with root rights (gksudo nm-applet), the connection stays alive. What the...?

---

### Post by piquadrat on 2009-09-23
Am I the only one having this problem?

---

### Post by maheshasolkar on 2009-09-23
Wireless connection in Karmic has been pretty iffy for me. It refuses to connect sometimes. I restart NetworkManager a few times, and it connects.

Sometimes, I have to take my laptop closer to the AP for it to connect. Once connected, I can move it away and the connection stays.

There's no pattern, so I can't look for a bug or file one.

I am going to wait and watch on this one.

---

### Post by suoko on 2009-09-24
i have problems with my eeePC too since latest updates.
must be a temporary problem

---

### Post by jimcox6309 on 2009-09-24
Updated karmic alpha 6 this morning (Sept 24).  After restart the wireless applet was gone.
(ancient Dell 8100 2g ram, 60gb toshiba hard drive

---

### Post by Rallg on 2009-09-24
Indeed. After this morning's updates (Sept 24) the WiFi on my Eeepc no longer works. It still works in Windows XP on the same computer.

Symptoms:

Wireless no longer launces automatically at startup.

If I try to launch the Network manager via System preferences, it does not launch.

If I try nm-connection-editor via Terminal, I get an error message saying that this file cannot be found:

libnm-glib-vpn.so.0

---

### Post by Arlanthir on 2009-09-24
I updated it a while ago and I lost network manager too.
But now I've updated it again with a wired connection and it's all good :)

---

### Post by orc_dragoon on 2009-09-24
Ive just updated now and the applet is gone and I cant connect via Wireless. Ill try wired soon.

---

### Post by suoko on 2009-09-28
i'm using wicd in the meantime and it works with no problem

---

