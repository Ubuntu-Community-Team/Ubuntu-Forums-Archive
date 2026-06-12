---
title: "How to fix wireless problem - or how to roll back?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by mrwhoohoo on 2008-04-25
I used the automatic upgrade and Hardy has trashed my wireless network card which worked fine under previous release, using firmware. Now it doesn't even appear in the hardware manager thing.  How do I recover from this? Or how can I roll back to where I was? 
Steve

---

### Post by Pumalite on 2008-04-25
What's your card?

---

### Post by mrwhoohoo on 2008-04-25
> **Pumalite said:**
> What's your card?

It's a Broadcom 43xx in an HP Pavilion zd7030 notebook. When I installed 7.10, it prompted to tell me that it wasn't working and that there was firmware workaround. I did the research to get it working and I carefully stored the procedure I had used. Now (1) it simply doesn't recognize that there's a card there; and (2) when I type lpsci - first step in the procedure - it comes back 'command not recognized'; (3) card does not appear in the manual configuration wizard - although my nvidia card, which was quirky in 7.10 does. The light indicating that the card is on won't light. Booting under windows everything works fine.

Steve 

<vent> I have to say that I'm pissed as hell because (a) this is supposed to be a stable  release (b) which was offered for automatic install by the update wizard (c) which I had assumed would not screw with these lower level hardware tweaks - or would have the common decency to warn me. I can live with FF not running my extensions, but this is core stuff. I won't be recommending Ubuntu to buds any longer.</vent>

---

### Post by Pumalite on 2008-04-25
This might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

---

### Post by mrwhoohoo on 2008-04-25
> **Pumalite said:**
> This might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

Thanks - I'll chase this one down through the wireless forums.

---

### Post by fusionisthefuture on 2008-04-25
i have to say i was much happier with the upgrade from fiesty to gutsy than i am with this one.  i also have a broadcom 4312 and in gutsy i did not need ndiswrapper or any fwcutting or anything, it just worked.  now that wiki page is telling me i need to do ndiswrapper, probably because its written for fiesty, and for future reference, just pasting links is many times of very little help, you didnt even point out to the OP that he was just typing lspci wrong.  if anyone learns how to get their wireless on hp lappies working please post.

---

### Post by dtgolder on 2008-04-26
This thread worked for me:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

---

### Post by lanruisen on 2008-04-26
> **dtgolder said:**
> This thread worked for me:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Look for the Hardy fix (almost at the end)

Well, I tried it twice and it didn't work for me. My wireless also died after Hardy update.

---

### Post by mathenge on 2008-04-26
I have the same broadcom chipset on my Dell Latitude 620. Like you I had a work-around for getting wireless and the nvidia card working in Gutsy. For the wireless card, I had to blacklist the bcm43xx driver that Gutsy insisted on detecting and trying to load, and instead, use the ndiswrapper package and the Windows XP drivers. For the video card I used Envy to install them.

For the upgrade to Hardy, the Envy developer strictly tells you to remove the driver before upgrading - video.

For wireless, I guess I was lucky. In running the live-cd, I noticed that the live-cd detected my card even though it didn't install the firmware (since that's proprietary). All I did was install the restricted modules. I've attached a screenshot.

However, since you've already upgraded, ndiswrapper may be getting in the way. You should probably try to remove it first (modprobe -e ndiswrapper). You'll also have to stop it from being loaded since you need a reboot.

To see if ndiswrapper is actually installed, you can type:

         lsmod | grep ndiswrapper

Let me know what you find.

---

### Post by lanruisen on 2008-04-26
This post worked for me. 
[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

Post #7

---

