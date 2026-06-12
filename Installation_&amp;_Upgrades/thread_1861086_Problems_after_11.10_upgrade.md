---
title: "Problems after 11.10 upgrade"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by azupan on 2011-10-15
Here's what happened:

[LIST]
[*]Shutdown and Restart buttons have disappeared from KDE Plasma menu. Kubuntu login screen was replaced by ubuntu login screen. In order to shut down, I have to logout from KDE, and shutdown from Ubuntu. Annoying. The reason might be that I have converted from Ubuntu to Kubuntu a while ago because of problems I had with Unity.
[*]Firefox slowed down beyond useless. It takes a couple of seconds before it reacts to anyting, and it uses 2x100% CPU on multicore machine despite of the fact that I disabled all add-ons. How does it manage to do that is beyond me. Unfortunately, I need it for development. I'd substitute it with Chromium, but it doesn't support activities, and doesn't have all the stuff I need. Rekonq is nice, but doesn't have all the functionality.
[*]LibreOffice icons do not show on desktop widgets. Looks like mere annoyance, but how can I know which application I'm launching?
[/LIST]
Any help would be appreciated.

---

### Post by chrestomanci on 2011-10-17
> **azupan said:**
> Here's what happened:

[LIST]
[*]Shutdown and Restart buttons have disappeared from KDE Plasma menu. Kubuntu login screen was replaced by ubuntu login screen. In order to shut down, I have to logout from KDE, and shutdown from Ubuntu. Annoying. The reason might be that I have converted from Ubuntu to Kubuntu a while ago because of problems I had with Unity.

I have found a fix for the shutdown problem. See my comments on [Thread 1860008](http://ubuntuforums.org/showthread.php?t=1860008)

---

### Post by azupan on 2011-10-17
Thanks.
 
I've done some research of my own in the meantime. I've prepared new, fresh Kubuntu installation in an empty partition, and as far as I was able to test it so far, it works OK. 
 
I suspect the reason for my problems is that I converted my Ubuntu to Kubuntu installation a while ago, because of problems I had with Unity. Once I'm sure, I'll mark this thread as Solved.
 
I still have another, larger empty partition free, and it looks like I'll have to migrate my stuff there- as soon as I decide whether to use Kubuntu or OpenSUSE.

---

### Post by azupan on 2011-10-17
UPDATE: Yup, it was the ol' Unity allright. Looks like it doesn't get along with KDE very well. Firefox works OK on fresh installation, and shutdown buttons are there as well. I haven't tested LibreOffice icons, though, because I was forced to switch to OpenSUSE for some other reasons. MySql Workbench doesn't work anymore, and I need it for my work.

---

