---
title: "Ubuntu 13.10 - Unity panel does not appear after login (desktop icons appear fine)"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by Wug on 2013-11-22
This problem existed briefly during 13.04 as well (I updated from 12.10 to 13.04 to 13.10).  After logging into the graphical environment, the desktop loads, but the unity panel, indicators, and launcher are all missing.
The window decorator appears to be working correctly (windows have borders, etc).
I tried purging packages unity-.* and reinstalling them, but this has not helped.
dconf reset -f /org/compiz has not helped either.
I've looked in the lightdm log location but nothing appears to be out of the ordinary.
I just reinstalled my graphics drivers (proprietary) because I was unable to boot properly, any attempt to start a graphical session of any kind would hang the computer.

I have a radeon 7970, and am using the latest beta driver from here: [http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64)

Any thoughts?

---

### Post by fantab on 2013-11-22
How about:

```
sudo apt-get install ubuntu-desktop --reinstall
```

---

