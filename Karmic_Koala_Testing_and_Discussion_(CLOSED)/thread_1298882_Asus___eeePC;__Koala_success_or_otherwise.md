---
title: "Asus   eeePC;  Koala success or otherwise?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NE Key on 2009-10-23
9.10 RC now running on an eeePC 900a - with great success, straight out of the box.

(Now with ndiswrapper 'cos the ath5k driver for the wireless Atheros chip is not so good). 

Looks good and performance (subjective assesment) is excellent.

---

### Post by Kobalt on 2009-10-23
Using it on my eeePC 1005HA-H, everything is just great and the battery life is awesome, almost the same as in Windows. Great Koala so far :)

---

### Post by davidryderuk on 2009-10-23
Yes, it runs great on my eeepc 1000. I'm happy about being able to view flash full screen again and scrolling horizontally on the touchpad. Additionally compiz is more attractive since it no longer seems to slow my computer down.

---

### Post by winotree on 2009-10-23
Everything* works out-of-the-box on my 701(B) purchased early December, 2007.  It seems like a new device -- way faster all the way around: start-up, programs, pages, shut-down.  With a fresh install that means I've got* GRUB2* and *ext4* [isn't that correct??] and no, none, not any problems, issues, glitches, whatsoever.   This has been worth waiting for!  :D

* Don't have program installed for camera so can't comment on that [yet]

---

### Post by flipper9 on 2009-10-23
I've been very happy with Karmic (even from the alpha releases) with my Asus Eee PC 1000h with 2gb RAM and 160gb SATA drive (stock).  Everything has worked out of the box, things have been smoother than with Jaunty in the graphics department, and I use a lot of compiz effects without too much trouble.  Great job Ubuntu crew!!!!! :guitar:

---

### Post by flipper9 on 2009-10-23
> **winotree said:**
> With a fresh install that means I've got* GRUB2* and *ext4* [isn't that correct??] 

Yes; if you did a fresh install, then you got Grub2 (should show up as version 1.96 beta 4 or something like that on boot) and ext4 by default.

---

### Post by maizein on 2009-10-23
> **winotree said:**
> Everything* works out-of-the-box on my 701(B)... * Don't have program installed for camera so can't comment on that [yet]

Thanks for the info. Have you tried Skype? The mike is always a problem with Ubuntu on the eeepc 701...

I'm dying to remove TinyXP and install this but I'm afraid Skype won't work out of the box...

---

### Post by HotShotDJ on 2009-10-23
With eeePC 900, everything seems to work "out-of-the-box" using Karmic UNR.  I'm especially impressed with the built-in webcam & microphone.  They just worked (after enabling "microphone 2" in sound preferences) -- and the quality is much better than I expected.  I've tested it with Cheese and with Empathy Google Talk.  This from a free "hand-me-down" that we just acquired last week.

---

### Post by maizein on 2009-10-23
> **HotShotDJ said:**
> With eeePC 900, everything seems to work "out-of-the-box" using Karmic UNR.  I'm especially impressed with the built-in webcam & microphone.  They just worked (after enabling "microphone 2" in sound preferences) -- and the quality is much better than I expected.  I've tested it with Cheese and with Empathy Google Talk.  This from a free "hand-me-down" that we just acquired last week.

Great! I hope it's the same with the eeepc 701! Did you have mike issues with previous versions of Ubuntu? 

By the way, have you tried switching to "desktop mode" and then back to "netbook mode"? That was also a bug in previous versions...

Thx!

---

### Post by AlanR8 on 2009-10-23
Been running Karmic on my EeePc 700 series since Alpha 3. Everything just worked from the first install. Skype was not an issue either.

Enjoy

---

### Post by HotShotDJ on 2009-10-23
> **maizein said:**
> Great! I hope it's the same with the eeepc 701! Did you have mike issues with previous versions of Ubuntu? I haven't tried previous versions.  It just so happens that we were given this netbook last week and I put Karmic UNR on it straight away.  The previous owner had Xubuntu Hardy on it, but I never tried it.
> **maizein said:**
> By the way, have you tried switching to "desktop mode" and then back to "netbook mode"? That was also a bug in previous versions...Still broken as of last week.  Perhaps I'll try it again after I get it back this weekend and update it.

---

### Post by maizein on 2009-10-23
Thx!

---

### Post by GoldNugget on 2009-10-23
Karmic runs perfectly on my eeepc 900. None of the glitches present in previous versions are present. I was even able (finally) to tether my Blackberry to use as a wireless modem (needed a Bluetooth adapter and Blueman from the repositories). 

The video problems seem much better recently and flash videos and accelerated games are much smoother.

Wifi and shutdown work properly now. The windows fit the screen better. (This was especially frustrating during install) The ability to Alt-Click and drag windows is enabled by default.

Battery life is better (although it always tells me my battery is broken on startup. Then the panel icon comes up and shows the correct usage.)

This looks to be the best Ubuntu ever. Thanks devs!

---

### Post by Master One on 2009-10-26
I am just about to install Ubuntu 9.10-RC on my Asus Eee PC 901GO, and I was wondering about the following things:

[LIST=1]
[*]Last time I read about Debian/Ubuntu on an Eee, a special "Eee" kernel and special ACPI scripts were needed/recommended. I guess the kernel issues are history with 2.6.31, but what about the full use of all Eee ACPI functions (like the original functionality of Fn + F1-9 and the 4 extra-keys)?
[*]What about the "SuperHybridEngine" for powersaving?
[*]What about extra functionality, like underclocking, to extend battery-life?
[*]Is there a tray-app available to configure the extra functionality?
[*]Is everything supposed to work out-of-the-box, or is something additionally needed/recommended after the initial installation?
[/LIST]

---

### Post by Master One on 2009-10-26
[deleted]

---

### Post by Saiph on 2009-10-26
Great on my eeePc 901 but the external vga dont. When I switch it on, eeePc freeze. Now what ?

---

### Post by Master One on 2009-10-27
Well, Ubuntu 9.10-RC + UNR is installed now. Most indeed works out-of-the-box, but:

[LIST]
[*]Nothing with "SuperHybridEngine", an therefore no max powersaving. Before with Asus Xandros and SuperHybridEngine on AP (Automatic Powersaving) the fan did not go on at all until after some time has passed depending on the used application (so it was completely silent first). Looks like max powersaving can not be achieved without some additional application (either something with ACPI scripts, or an applet for configuration).
[*]In the official repos there is an eee-applet and the eeepc-acpi-scripts. The eeepc-acpi-scripts can not be installed, is reports BROKEN, and conflicts with acpi-support. The eee-applet can be installed, but does not work, because it tries to change configs at the wrong place (there is no more /proc/eee).
[/LIST]
Hopefully something is going to take a look at these issues, it would be sad, if Ubuntu can not reach the same degree of functionality and battery-life as Asus Xandros.

---

### Post by ignaciouy on 2009-10-27
Karmic RC is working great on my 1005HA! speed is great, everything (except de internal mic) work great out of the box. Battery life is close to that on windows xp, with compiz enabled.

At first I tried UNR, with the desktop interface (not UNR), and compiz didn't work really nicely, fan on all the time, and generaly poor performance.
Regular desktop edition worked great instantly.

There's a confirmed bug open on launchpad for the internal mic (sound preferences shows only the external plug option), so hopefully it will get fixed soon.

I'm having a similar problem where my eeepc freezes when an external monitor gets plugged. Also, when I managed for it to work, panel launchers got all over the place and panels in general just got all disorganized overall, thought this was getting fixed on a launchpad bug file I saw long ago. 

Overall, a great release, with pleasing artwork and great performance, fit and finish. Congratulations and thank you Ubuntu team!

---

### Post by Master One on 2009-10-28
> **ignaciouy said:**
> Battery life is close to that on windows xp, with compiz enabled. At first I tried UNR, with the desktop interface (not UNR), and compiz didn't work really nicely, fan on all the time, and generaly poor performance. Regular desktop edition worked great instantly.
That sounds odd, because UNR is just the user interface, the underlaying installation is exactly the same. I installed Ubuntu 9.10-RC from the alternate CD, because I wanted full SSD encryption, and then added UNR afterwards (with "aptitude install ubuntu-netbook-remix"). The first thing I always do, is to disable compiz (didn't work with UNR at all when I tried it with Ubuntu 9.04 some time ago). As mentioned, the fan always on issue, which wasn't the case with Asus Xandros, indicates, that "SuperHybridEngine" is not supported, and therefor no max powersaving. Had no chance to compare the runtime on battery yet, but I am pretty sure, it's less than with Asus Xandros and SuperHybridEngine set to "Automatic Powersaving".

Does anybody know, if there are plans to fix the additional Asus Eee features, like the eee-applet and the eeepc-acpi-scripts?

---

### Post by vavoem on 2009-10-28
Systems hangs when connecting external monitor 
I have a message battery broken 1.9% message when starting up.
I absolutely hate the new gdm screen, it looks like from the dark ages.

But otherwise it is more responsive graphic performance has been enhanced largely and all the fn f1-f12 buttons work instantly 
I had to enable double finger scrolling but works. 
No green screen webcam issues in skype any longer.
Microphone2 works good.
hibernate and suspend both work good it even reconnects my wireless.

So more positives and only a few minor negatives of which i am sure  will be fixed in the future.

Asus e900 (feels like brand new again except for the crappy loose keys on my keyboard off course ;)

---

### Post by winotree on 2009-10-28
Just wanted to verify this with several days use before saying anything -- *the CPU temperature of my device is much lower than it was.*  

The default Xandros was a steady 57C during normal web usage.  
Changing to Xubuntu [Jackalope] 9.04 brought it down to 54C on average.  
The recent clean install of Koala consistently yields 51C.  Has anyone else experienced this?  Needless to say, I'm impressed.  :D

---

### Post by Master One on 2009-10-29
winotree, how did you check the temperatures?

In the meantime, I found out a little more about the SuperHybridEngine, which works by setting the mode (Power Saving, High Performance or Super Performance) through /sys/devices/platform/eeepc/cpufv, but without a tray-applet managing this setting, it's just not practicable (especially since the preferred mode in Xandros was "Automatic Powersaving", which is not a mode, but the applet setting one of the three mentioned modes automatically on demand). By default the SuperHybridEngine is set to "Super Performance".

I also switched off the webcam (by writing "0" to /sys/devices/platform/eeepc/camera), since I usually don't need it.

---

