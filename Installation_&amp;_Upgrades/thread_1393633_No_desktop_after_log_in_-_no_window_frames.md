---
title: "No desktop after log in - no window frames"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by kamaji792 on 2010-01-29
I did a clean install of Ubuntu Netbook Remix (UNR), after trialing it for some time running off a 4GB SD card.  The install goes OK but then I have a big update (100+ MB).  I do this via **sudo apt-get upgrade**.  At the end as requested I restart the system.

I get a log-on screen and successfully log-on but I get no desktop.  The background is the one that appears after logging in.  The good news is I get a white terminal console without any of the normal window dressings, like a title bar etc.  The console is only active if the mouse is over it.  I can run applications like **nautilus**, **firefox**, etc. but they are missing the window frames and title bar (so no minimise, maximise, and close buttons).

Any help greatly received.

[edit-1]
After spending some time looking for a solution I gave up and just re-installed UNR 9.10 and all is fine.

For the record the following is quite a popular command to try and re-configure X (I did not get round to trying it):

```
sudo dpkg-reconfigure xserver-xorg
```
[/edit]

---

