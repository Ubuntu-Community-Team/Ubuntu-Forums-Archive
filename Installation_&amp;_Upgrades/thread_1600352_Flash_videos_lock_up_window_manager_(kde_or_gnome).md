---
title: "Flash videos lock up window manager (kde or gnome)"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by wishes on 2010-10-18
I'm fairly decent Linux admin (ok, i've been paid to do it for the last 10 years now, maybe better than fair), however this problem has me stumped.
Ever since i dist-upgraded to 10.10 playing flash videos longer than a minute will *sometimes* lock up my window manager. 
I am unable to click on other windows, or links in current window.
If i open a terminal after  starting the video i can still run commands in the terminal after its locked up, but not use the mouse in any form at all.
I can get to tty1 or any other console, kill flash, kill the browser, etc. 
Until i restart gdm or kdm it is still locked up however.
I have tested with both kde and gnome. Tested with kdm and gdm. Tested with firefox and chrome (both use different installs of flash plugin - chrome brings its own).
I created a new user on the system to test enviroment, no luck there.
I eventually reinstalled yesterday with a fresh 10.10, and still I am having this problem.
It *often* happens, but not always. Always on videos longer than about a minute at a guess, i have not timed it.
Only ever happens on flash videos - ie youtube etc.

Any other ideas? Suggestions?

Liz
ps. Please try to avoid basic newbie suggestions, pretty sure i have passed that long ago.

---

### Post by efflandt on 2010-10-18
Are you running 32 or 64-bit Ubuntu. What video card/chip do you have, and are you running proprietary drivers for it?

In 64-bit I noticed that with flashplugin-installer I was getting segfaults of flashplayer.so (10.2 r85) which caused npviewer.bin in Firefox 3.6.10 to crash.  But I never really noticed when it happened other than crash reports in 10.10 beta or looking at /var/log/messages in Lucid.  So maybe it was just flash ads.  Since uninstalling that and installing real 64-bit flash (which I think Lucid shows as 10.2 r161 and Maverick shows as 10.2 d161) I have had no flash errors at all.  And I have been using 64-bit Hulu Desktop (which uses flash) to view hours of TV shows that I do not get on broadcast TV.

My PC is i5 650 3.2 GHz w/GT 220 using nvidia 2.60.19.06 drivers (or 195 something in Lucid)

PS: When I recently did a 32-bit 9.10 to 10.4 upgrade on my laptop, ubuntu-restricted-extras were no longer installed and flashplugin-installer appeared to be installed in Synaptic, but did not work and not show up in Firefox Add-ons.  Even installing ubuntu-restricted-extras did not restore flash.  I had to mark flashplugin-installer for Reinstallation in Synaptic before it would work.

---

### Post by wishes on 2010-10-18
The original install was running 32bit, the fresh install 64bit.
Interesting idea regarding the video, its a nvidia chipset running nvidia
I dont recall the exact chipset off hand (its at work, im now at home), but its about 2 years old and has DVI out

---

### Post by wishes on 2010-10-31
Okay, I have more information. I rarely listen to music on this PC but decided to this morning, blow me down if this happened again.
So looks like its sound related vs anything else. I killed rhythmbox and anything using /dev/dsp etc but still couldnt click on other windows or use them.

Anyone know offhand any similar bugs?

---

