---
title: "Strange video results"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by andersn on 2008-02-18
Hi all, trying to set up an old Compaq for my youngest son. Since it lacks some memory I choosed the Xubuntu version (looked slim and nice).
Install went fine (text install) but when Xfc starts the resolution is wrong. All text and images are distorted to a limit where I can't even read it.
Should I just try and grab another screen page (Ctrl-F2) and run some kind of X re-config, if so, what is the correct syntax? I think the video card is an old Diamond Stealth. I have tried to run one of those live-cd things on it, so I know it works (at least it did with Knoppix and Mandriva Live-CD), took some time swapping since I only have 128MB :-)

Looking forward to some suggestions...

/A

---

### Post by Partyboi2 on 2008-02-19
To reconfigure the xserver press Ctrl+Alt+F2 to get to a terminal and type
```
sudo dpkg-reconfigure xserver-xorg
``` choose ati for the driver and answer all the questions right through. If ati does not work then choose vesa as the driver.

---

