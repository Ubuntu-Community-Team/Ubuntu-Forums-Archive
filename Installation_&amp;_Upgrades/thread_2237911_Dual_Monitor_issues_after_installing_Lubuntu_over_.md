---
title: "Dual Monitor issues after installing Lubuntu over Ubuntu"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by barrymcclellanduk on 2014-08-04
Hi,

I've tried finding a solution to my issues but maybe I am a unique snowflake :)

I have an old Laptop (Dell Inspiron 1720) with a broken screen so I decided it could be my media box/Plex server.

I only had an Ubuntu 12.04 CD laying around (been a long time since I took a look at Ubuntu, last time I really used it was Edgy).  So I installed 12.04 and upgraded it to 14.04.  All went well.  Installed the nvidia drivers and the performance jumped (Although it still won't remember my settings for disabling the laptop screen even if I run it as GKSU and save the xorg.conf from within...) - note: I don't have any blank CDs and the laptop won't boot from USB

I decided to see how much of a performance boost I would get from switching to the Lubuntu desktop so I installed the Lubuntu-Desktop bundle, rebooted and switched to Lubuntu at login.

Now, the major issue starts here.  The laptop screen AND the external monitor are powered on (not usually an issue as I just usually disable it once I'm in and get on with my life) but it has it set to one large desktop and I'm at the right, I can move the mouse off the left of the screen, essentially helpless.  I've tried hitting Alt+F2 to get up the Run prompt but I can only assume it's appearing on the "left" side of the screen, so I've tried typing the command for nvidia settings, but again, it must be appearing on the left of the screen (well, I assume so as I can't see it).

Any ideas?  It's been a long time since I've used linux as a desktop so I'm feeling very novice-like

Thanks

---

### Post by Bucky Ball on 2014-08-04
Lubuntu should have a panel across the top, yes? Can you access it or is it off the 'top' of the screen?

You can also hit ctl+alt+F1 to get to a CLI. You could try installing there arandr: sudo apt-get install arandr

arandr will allow you to set two separate screens again. Should be in Accessories (Preferences in lxde?). You could probably change things in Settings>Display, but not familiar enough with Lubuntu to know what it uses/how it uses it. 

Just a note, installing lxde would have given you the Lubuntu desktop environment without dragging in the default apps, packages and bloat you probably don't need. Installing lubuntu-desktop is essentially the same as installing Lubuntu on top of the existing Ubuntu install. They may happily co-exist, but it's generally problematic. Going for just the DE is a better option, although can still provide conflicts.

---

### Post by barrymcclellanduk on 2014-08-04
> **Bucky Ball said:**
> Lubuntu should have a panel across the top, yes? Can you access it or is it off the 'top' of the screen?

Nope, just desktop background.

I'll switch over and give the rest a try now though :)

---

### Post by barrymcclellanduk on 2014-08-04
No joy.  If I hit ALT+Fx it kindly powers down my external monitor and switches to the broken screen.  Using the External screen switch button on the laptop keyboard (FN+LCD) does nothing, where it normally does.

---

### Post by Bucky Ball on 2014-08-04
It should so something is amiss. Perhaps 'off the top'. Tried the other suggestions in my last post?

Ah, just read your last post. I said 'ctl+alt+F1'. Please reread and try out. ;)

---

### Post by barrymcclellanduk on 2014-08-04
Yeah, sorry, I had tried Alt+F2 previously but tried Alt+F1 anyway on your say-so incase other magic would happen, hence the Fx (I forget people can't see wha'ts in my head.. sorry :) )

Anyway, got it working.  I gave up and did what I should have done initially, which was to dismantle the laptop and disconnect the LCD cables from the mainboard.  Problem solved as bios now identifies the external output as the main monitor 

Thanks for the tips though

---

### Post by Bucky Ball on 2014-08-04
All good. Glad it's working. Please mark as solved to help others by following the second like in my thread. Good luck.

---

### Post by barrymcclellanduk on 2014-08-04
Doesn't feel solved so much as worked around.. Lol, there should be a button for that :)

Additionally, managed to get booting from USB working after flashing the BIOS.. Woo.

Closing thread. Thanks

---

### Post by Bucky Ball on 2014-08-06
Yea, a 'resolved' button would be good; we've talked about it ...

---

