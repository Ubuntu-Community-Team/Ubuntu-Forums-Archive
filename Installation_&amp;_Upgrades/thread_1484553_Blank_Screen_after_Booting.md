---
title: "Blank Screen after Booting"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Twentydragon on 2010-05-15
I recently installed Ubuntu 10.04 on my desktop computer through Wubi, and it caused the system to lock up after booting and before actually letting me do anything.  So I wiped Windows XP off and installed Ubuntu by itself, thinking that was the problem.  Now, I'm confronted by a completely blank and black screen immediately after the Ubuntu startup logo.

Here are the system specs I know:
Processor: AMD Athlon 1.49 GHz
Video Card: ATI (unknown model) 256-512 MB internal RAM
RAM: 2 GB
Sound Card: unknown
In Windows XP, it ran two monitors with different sizes as an extended desktop.

Please help.  I have no idea what I'm doing.

---

### Post by Catharsis on 2010-05-16
While booting, hold down Shift to get to grub. Then hit 'e' to edit, and remove "quiet  splash". Ctrl+x to boot.

If that doesn't do anything (besides show a bunch of text), do the same but this time replace "quiet splash" with "nomodeset" and boot.

---

### Post by Twentydragon on 2010-06-10
At this point, I can't even get it to move past the Ubuntu title screen.

I failed to follow the advice given me by Catharsis and wound up reinstalling Windows XP.  After failing to get that working properly, I decided to try installing Ubuntu again.  The installation process now doesn't move past the logo screen, with or without "nomodeset" on.

Also, if it makes any difference, my mouse is plugged into *this* computer, so I'm using the keyboard on the one in question.

---

### Post by jokei on 2010-06-10
Similar issue, did the install on my girlfriends laptop, install finished and it said Restart your computer, went to do this and when powering up again it just goes to a black/blank screen.

No Ubuntu menu at all...  I don't think it's loaded the video drivers, but am unsure - as I can't see anything.

The laptop in question is a 
Fujitsu Siemens
Amilo Li 1718
Model: MS2212

---

### Post by Catharsis on 2010-06-16
> **Twentydragon said:**
> At this point, I can't even get it to move past the Ubuntu title screen.

I failed to follow the advice given me by Catharsis and wound up reinstalling Windows XP.  After failing to get that working properly, I decided to try installing Ubuntu again.  The installation process now doesn't move past the logo screen, with or without "nomodeset" on.

Also, if it makes any difference, my mouse is plugged into *this* computer, so I'm using the keyboard on the one in question.

Try replacing "quiet splash" with "xforcevesa noapic noapci nosplash irqpoll"

---

### Post by Twentydragon on 2010-06-16
I couldn't find the "quite splash" option, nor anywhere to type options in.  I ended up giving up and buying Windows 7, which is now working fully.  Thank you for your efforts, but this issue is now resolved/moot.

---

