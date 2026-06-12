---
title: "Ubuntu 15.10 software updates causing sound issues"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by steve237 on 2015-11-26
Hi-

Just installed ubuntu mate on a new lenovo x250 and had some frustrating problems.

Installed the 15.10 AMD64 image successfully, and encountered a couple of sound-related problems, one of which I was able to find a fix for (not detailed here), the other for which I cannot find a complete fix for.

The problem for which I can not find a complete fix ONLY begins occurring after running software update, and does not occur if running from the unupdated 15.10 install. 

The problem is as follows:

1) When headphones are plugged in, no sound is playing, AND the computer is running from batteries, the headphones produce a very loud static/hissing sound.  This sound ceases when something is played or the GUI sound prefs panel is opened.  This problem can be alleviated by commenting out the line "load-module module-suspend-on-idle" in /etc/pulse/default.pa.  

2) When plugging headphones in while on AC, there is ~0.5 seconds of similarly very loud static.  This is not the 'connection' popping sound that sometimes occurs when plugging in analog audio, but a (brief) sustained episode of static, also very loud.  I have tried several fixes (generally involving changes to alsa-base.conf) that were suggested for similar problems on various forums, but they are not effective. 

//

I did a fresh install to try to diagnose WHAT parts of the software updates were causing the above problems.  I tried doing all of the updates except for several mpeg related updates (most obviously related to audio in my rather unsavvy understanding, see image below).  If this is done #1 of the above problem *mostly* goes away, but the same loud static is head when unplugging the power cord, which would not occur with the aforementioned pulse fix. #2 above is not affected by bypassing those updates, and still occurs. 

[ATTACH=CONFIG]265783[/ATTACH]



These audio issues are not untenable, but are highly suboptimal. Coming from several years on linux mint, where things never updated, I am not sure if this a hiccup that will probably disappear, or a note worthy bug. If anybody is interested, I am happy to provide more information about my system, settings, etc.  But, I'm not sure what of those would be helpful here, so I don't want to just barf a bunch of terminal copypastes here if they won't be useful.

---

