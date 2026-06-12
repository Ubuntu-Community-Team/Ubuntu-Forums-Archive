---
title: "Install/LiveCD on Dell Latitute CPx H500GT laptop probs"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by John Stumbles on 2005-06-26
when installing or booting from the LiveCD on on my Dell Latitute CPx H500GT laptop there comes a point (during setting up graphics on the liveCD) when the screen display breaks up and rolls vertically upwards - as when the vertical hold doesn't sync on a CRT display. On the install it's happened after the initial setup and reboot phase, and installation seems to paus waiting for some reponse from me but I couldn't see what it was asking me! :-(

I tried typing Y and enter but that didn't move things along. Ctrl-C got thigs going and I got the gui up and seeming OK, but I'd like to know what I might have missed

Fortunately once installed the screen breakup doesn't occur on bootup.

When running, however, if I stick a CD in the drive it doesn't automatically get mounted (though pmount /dev/cdrom works). Worse, it doesn't automatically mount CF cards in a USB reader (though according to /var/log/messages it sees the card reader itself being attached to the system) and I haven't a clue what to tell pmount to call it.

---

