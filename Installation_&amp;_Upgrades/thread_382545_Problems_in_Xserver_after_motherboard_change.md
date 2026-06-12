---
title: "Problems in Xserver after motherboard change"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by gabrielrm on 2007-03-12
After i change the motherboard i have problems running xserver and tell me that there's no screen but after running "envy" (thank you tseliot :)) and restart gdm i'm able to run Metacity but no Beryl. :(
I'm confused and not know what to do ...
I'm new to Ubuntu and Linux and have to excuse my spelling.
The other moterboard die because of PSU and this one has same chipset, nforce2...
and video is AGPx8 Ti4200 on AsRock K7NF2-RAID motherboard.

Thank you!

---

### Post by Captain_Riker on 2007-03-12
Hello there,

Question:

Did you just replace the old motherboard with a new one but did not reinstall your OS?

I need some more Information about this to help.

Greetings

---

### Post by gabrielrm on 2007-03-12
Yes, just replace the old one, without reinstaling the OS.

Greetings

---

### Post by gabrielrm on 2007-03-12
Yes! I found what i was doing wrong!
The old "working" xorg.conf had a line with BusID and the actual working xorg.conf does not have that line. That's all and now it's working again!
I love Ubuntu :)
Thank you Captain_Riker.

Best regards.

---

