---
title: "cpu usage for kwin higher in jaunty than intrepid"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dumbkiwi on 2009-04-12
Hi,

I've just upgraded to jaunty beta on a couple of machines with nvidia video cards.

It seems that the cpu usage on kwin (with desktop effects turned on) is alot higher in jaunty than it was in intrepid.  I'm using the nvidia driver.

Are there any nvidia/desktop effects settings that could lower cpu usage?

Cheers

Matt

---

### Post by garretwp on 2009-04-13
Do you have any plamoids loaded on the desktop? For example do you have the calendar plasmoid loaded? There is a known bug that causes high cpu usage when using the calendar plasmoid. If this is loaded on your desktop, remove it.

- Garrett

---

### Post by MacUntu on 2009-04-13
> **garretwp said:**
> Do you have any plamoids loaded on the desktop? For example do you have the calendar plasmoid loaded? There is a known bug that causes high cpu usage when using the calendar plasmoid. If this is loaded on your desktop, remove it.

- Garrett

No, also happens without calendar widget. Load never drops below 10-15% - unusable on laptops.

---

### Post by Asraniel on 2009-04-13
try to fill a bug on bugs.kde.org, kwin is developed very actively.

---

### Post by taavikko on 2009-04-13
```
Tasks: 200 total,   1 running, 199 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.9%us,  0.1%sy,  0.0%ni, 98.7%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6021408k total,  1151428k used,  4869980k free,    41460k buffers
Swap:  9767480k total,        0k used,  9767480k free,   464448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3622 devil     20   0  960m 146m  36m S    6  2.5   0:52.81 amarok
 2817 haldaemo  20   0 36508 5140 4056 S    0  0.1   0:00.20 hald
 3530 devil     20   0  290m  42m  26m S    0  0.7   0:14.59 kwin
 3536 devil     20   0  676m  56m  26m S    0  1.0   0:06.06 plasma
 3581 devil     20   0  327m  30m  15m S    0  0.5   0:00.50 konsole
 3631 devil     20   0  503m  42m  25m S    0  0.7   0:03.12 ktorrent
 3859 devil     20   0 19116 1392  988 R    0  0.0   0:00.07 top
    1 root      20   0  4104  928  632 S    0  0.0   0:01.34 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd

```

Not noticing it here, just restarted after 4 days of uptime the numbers were pretty much the same.

Note that running 9800gtx+ nvidia here. So the issue might be that some lower-end cards have issues with it.

---

### Post by MacUntu on 2009-04-13
Oh damn... in my case it was the activated "Show FPS" plugin. After disabling it I got significant lower CPU load.

---

