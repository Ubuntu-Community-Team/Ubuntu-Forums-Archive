---
title: "Multi monitor problem"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by vinit320 on 2013-01-28
So I am not new to ubuntu and have been using ubuntu for the past 5 years. And it has worked flawlessly uptil now. 

I recently installed 12.10 and was quite happy with it. Until I switched to a dual monitor setup. 

I have a gtx 650 and have successfully installed the drivers. Everything was working perfectly fine on a single monitor but the moment i shifted to dual monitors, things just went bad. I searched on the web and found a lot of links but no good solutions. This may already be posted before, so apologies.

every time i boot into ubuntu, the resolution is all bad. My one monitor is 23 inch (1920 x 1080) and the other is 19 inch(1440 x 900). I cannot reset or change the values in the xserver settings. If i try and apply them, nothing happens. Even rebooting does not help.

And before anyone asks, yes i did use disper as well and this is what i get:

could not find nor create MetaMode:  :: DFP-0: 1440x900 +0+0, DFP-2: 1920x1080 +1440+0

Please advise as to how to get the dual monitor thing to work keeping in mind that the drivers are installed.

---

### Post by ManchesterHustler on 2013-01-28
Main:
[http://ubuntuforums.org/showthread.php?t=1785878](http://ubuntuforums.org/showthread.php?t=1785878)

Other:
[http://ubuntuforums.org/showthread.php?t=1465119](http://ubuntuforums.org/showthread.php?t=1465119)

:)

Sorry if those aren't much help, they were the best I could find stating monitor problems with any previous Ubuntu builds

---

### Post by dino99 on 2013-01-28
so are you having LCD + CRT display ?  and how are they plugged ?

if you are using one of the latest 3.8 kernel, such troubles should be gone. Rename or delete the xorg.conf then reboot (actual kernel directly deal with X, and bad setting into xorg.conf is often worst than nothing)

also edgers ppa might be tested (nvidia-current/nvidia-313)

---

### Post by vinit320 on 2013-01-28
No. The three links posted were already checked by me and they didnt help at all.

Also, I tried deleting the xorg file but to no avail.

the 19" monitor is connected via DVI and the 23 inch is connected via HDMI.

The problem is when I goto the nvidia settings, the max resolution i can set for both my monitors is 1024x768. It gives me no other option higher than that. 

Also, if I keep shifting drivers from additional drivers section in software sources, everything works perfect, but the moment I reboot, things go bad again. Any advise?

---

