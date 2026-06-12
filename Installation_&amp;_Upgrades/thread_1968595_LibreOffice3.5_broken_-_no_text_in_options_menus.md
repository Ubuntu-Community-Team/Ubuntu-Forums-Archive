---
title: "LibreOffice3.5 broken - no text in options menus"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by kohoutek1 on 2012-04-29
Hi, everyone.

This is the first time I've tried to use LibreOffice since the 12.04 upgrade, and I have problem with it: When I open any of the settings or options windows, there's no text in the options menus. This affects ALL settings dialogs. I can't change anything or work with any documents because of this. 

LO3.5 was updated in the repos on April 28. Connected?

To fix, I purged all LO files, then reinstalled from Software Center. I thought the issue might be related to the installation of LO in the /opt/ directory before the upgrade... that that installation might be conflicting with the new one. Nothing fixed.

Screenshot attached. 

Anyone else having this major issue?

---

### Post by kurt18947 on 2012-04-29
No problem with mine.  I've had this 12.04 install since A2, I've just kept updating it.  I wonder if your problem has something to do with video drivers?  If you're using proprietary drivers, perhaps disable them and see if that helps?  You didn't say what desktop you're using.  If unity, perhaps install gnome-session-fallback and log on with Gnome Classic (no effects.)  I'm using gnome-shell with the current Nvidia driver and smooth sailing.  I hope you're able to solve your dilemma.

---

### Post by kohoutek1 on 2012-04-29
Couple of things:

No other apps are affected by this.
No change has occurred in my hardware.
LO 3.5 was fine before the 12.04 upgrade, and I presume before the update of 4/28.

Fortunately, I kept my head cool and relied on my memory of where settings are in LO to get through a pretty important document I had to make. 

The problem is pretty severe here. Here's another screenshot of a different window:

---

### Post by kohoutek1 on 2012-04-29
I just filed a bug at Launchpad. I really need to get this fixed by tomorrow morning, or my day is going to be very rough!

:mad:

---

### Post by keithpeter on 2012-04-29
Hello kohoutek1

I have one PC with a clean install of 12.04 and a small netbook with an install that has been upgraded over the last few weeks from a daily. I can't see any issue with LO.

Have you tried making a new user account and logging in under that? Should dump any preferences.

Tomorrow: suggest a bootable usb? Or even a 10.04 live disk session?

---

### Post by kohoutek1 on 2012-04-29
> **keithpeter said:**
> Hello kohoutek1

I have one PC with a clean install of 12.04 and a small netbook with an install that has been upgraded over the last few weeks from a daily. I can't see any issue with LO.

Have you tried making a new user account and logging in under that? Should dump any preferences.

Tomorrow: suggest a bootable usb? Or even a 10.04 live disk session?

I tried your suggestion of setting up a new user account. LO3.5 opened, and on that user account, there is no LO-menubar. The problem is actually worse: No text in top-level menus, application-wide.

Again, it's the only application affected.

I'm adding a screenshot of the whole desktop under the new user. It's GNOME Classic, but I've observed the same problem in my own user account, both GNOME Classic and Unity.

---

### Post by kohoutek1 on 2012-04-30
As I stated earlier, I reported this as a bug at Launchpad: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/991574](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/991574)

However, at the risk of being pushy, I wanted to put my dependencies list here, as well, to see if someone on this forum might be able to notice anything out of the ordinary before the developers get to it.

It's attached:

---

### Post by rmartinez79 on 2012-05-23
Using Ubuntu 12.04 + XFCE4.10 (from ppa).
I also had this issue.
FIXED (sort off): The menu became visible when I disabled display compositing. (Main Menu -> Settings -> Settings Manager -> Window Manager Tweaks -> Compositor -> Enable display compositing).

---

### Post by kotek on 2012-06-10
Another "sort of" solution: in ubuntu-tweak changing the default font (ubuntu) to some other ones (best seems to be Nimbus Sans) displays almost all the menus back...

---

### Post by 53om on 2013-01-26
I have nothing in any of my menus in any LibreOffice applications. AND they keep crashing. Anybody else with this prob? I tried uninstalling and reinstalling without results.

Thanks!

Ubuntu 12.04

---

