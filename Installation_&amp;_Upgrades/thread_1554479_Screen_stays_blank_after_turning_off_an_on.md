---
title: "Screen stays blank after turning off an on"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by edannert on 2010-08-16
Hi there!

I just installed Mythbuntu 10.04 and have my Sony LCD TV connected via a DVI to HDMI cable. The issue I am encountering is that everything works fine until I turn off the TV and turn it back on later, because the screen stays blank and from what the TV tells me there is no signal. I have no idea what can cause this. I checked the TV settings in terms of power saving and turned it all off. I turned off the screen saver in Ubuntu, but still the same issue. My motherboard uses the ATI HD4200 onboard graphics engine.

Anyone, any ideas? Getting more and more frustrated and considering changing the motherboard... which I don't want :-(

Thanks,
Andreas

---

### Post by rmemm on 2010-08-24
I have similar problem.  HDMI connection to a VIZO HD TV.  I'm using the fglrx radio drivers.  Not sure which chipset -- but one of the later video chipsets for HD support.  

Restarting the X server with ctrl-shift-backsapce works to get video back -- but that seems to be a bit extreme -- that is it kills your login session.

Next time it happens I'm going to try switching to the console with ctrl-alt-f1, then back with ctrl-alt-f7 -- to see if this helps, i.e., by forcing a screen refresh and a video mode change.  I can't test this yet because my black screen problem does not always happen when I turn the TV off and on -- but it does happen.

I would love to hear what other people think about this issue.

By the way I'm using Ubuntu 8.04  -- but plan to upgrade to 10.04 soon.

Rob

---

