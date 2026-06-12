---
title: "Kubuntu A2 going backwards!"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-06-13
For the most part I love ubuntu, as a rule it just works. Kubuntu however hasn't worked so well recently. Firstly both ubuntu and kubuntu set themselves up to 1080p for my non-1080p tv. Just clicking on display settings in kubuntu sets it right without my having to touch the actual settings. If it can get it right then why not on bootup??? Also once it is set right why does it change it's mind again when I reboot? This was the case in jaunty, however I upgraded last night and now every resolution, even 1024x768 is off the edge of my 50" screen at every side.

Also I must enter the wpa key every time the pc starts up, I really do think kubuntu has either amnesia or dementia.

Is anyone else having these problems and does anyone have a solution?

---

### Post by taavikko on 2009-06-13
If this is upgraded from jaunty, there is possibility that some cruft that affects new 4.3b settings, create a new user and login to that account to see if problem persists.

---

### Post by kingborel on 2009-06-13
Alphas cannot go backwards. They add features which may or may not break. That is a fact of life, and the whole point of alpha versions. If it's broken, file a bug report. Do not expect an Alpha to work perfectly

---

### Post by caryb on 2009-06-13
From my experience some of the old config files don't migrate too well, try removing the old config file after KDE version upgrade. ```
sudo rm -R ~/.kde/share/config
``` then logout & back in again.


Cary

---

### Post by Slug71 on 2009-06-13
> **kingborel said:**
> Alphas cannot go backwards. They add features which may or may not break. That is a fact of life, and the whole point of alpha versions. If it's broken, file a bug report. Do not expect an Alpha to work perfectly

This. 

Alpha 1 is usually still in planning stage. Alpha 2,3,4 is usually where a lot of big changes begin to make their way into the release. So it doesnt go backwards. This is what Alpha testing is about and what we file bugs for.

---

### Post by jerrylamos on 2009-06-13
> **Slug71 said:**
> This. 

Alpha 1 is usually still in planning stage. Alpha 2,3,4 is usually where a lot of big changes begin to make their way into the release. So it doesnt go backwards. This is what Alpha testing is about and what we file bugs for.

Sure Alpha 2 goes backwards in terms of usability and functionality.  Yes we file bugs.  

1. The A2 note says to wait for A3 for Grub2 to be able to multiboot.  Since all my test installs are multi-boot, then A2 is a non-starter with Grub2.  Looking at the bugs & fixes, so far no clean way to get Grub2 to select the other images.  I've tried.  Next step is to use Supergrub to install Grub (good luck).
2.  Karmic boot in 10 seconds?  With A2, no way!  Haven't timed it yet but on my IBM Thinkpad T40 seems like double A1.

So A2 looks like 2 steps backward before getting going forward again.  It takes a while for the bug fixes to come thru.

Jerry

---

### Post by xebian on 2009-06-13
Backward is relative to where you are.   If you are too forward as in final. A2 is backward indeed.  There will be 6 Alpha, 1 Beta, 1 RC, then Final.;)

---

### Post by macroshaft on 2009-06-13
> **kingborel said:**
> Alphas cannot go backwards. They add features which may or may not break. That is a fact of life, and the whole point of alpha versions. If it's broken, file a bug report. Do not expect an Alpha to work perfectly

I've said it before and I'll say it again, please try not to be so literal. I don't expect the alpha to work, I'm just reporting a bug and finding out if it's an easy fix or a genuine problem. So I was inventive with my title, that doesn't mean I literally think the alpha is going backwards.

---

### Post by macroshaft on 2009-06-13
> **caryb said:**
> From my experience some of the old config files don't migrate too well, try removing the old config file after KDE version upgrade. ```
sudo rm -R ~/.kde/share/config
``` then logout & back in again.


Cary

Have tried this and now it does not automatically change res as soon as I open display settings, other than that no change. Also I noticed that since the upgrade wireless refuses to connect. At one point it showed something like 15 instances of my router, it keeps asking for the wpa key over and over. I have found wireless in kubuntu (jaunty/karmic) to be very tempremental at best, often refusing to reconnect after a disconnection and requiring a reboot.

---

### Post by PRGUY85 on 2009-06-13
I see improvements yet I have the following remarks:

1) I don't see all the new features and plasmids that they added.  I can't see the standard Microblogging plasmid or the new animated wallpapers.

2) I have always had a problem with activating the Nvidia driver on Kubuntu (not on Ubuntu with Gnome).  When I do, everything looks crisp yet bigger than what it was.  It is as if the resolution went down so everything looks a bit big and crowded yet looks detailed and crisp.  It gives it a cheap look I can't get around of, not by reducing font size or anything.

3) I really like the new Package Manager front-end on KDE.  It almost battles the great frontend on fedora 10-11 with packagekit.

4) I can't connect to secure wireless networks, something others have issues with.

---

### Post by Nullack on 2009-06-13
Regressions should be expected

---

### Post by frustphil on 2009-06-14
I am also having this problem since Jaunty. It doesn't know my native screen resolution. It always sets a higher resolution each time I boot.

---

### Post by 23meg on 2009-06-14
The development branch is always prone to regressions; the important thing is to fix them before release. If you need help pinpointing the reasons behind specific issues and [reporting bugs]("https://help.ubuntu.com/community/ReportingBugs"), please start separate threads with titles that describe those issues.

---

