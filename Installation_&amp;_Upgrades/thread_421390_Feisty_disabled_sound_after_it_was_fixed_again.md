---
title: "Feisty disabled sound after it was fixed again?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2007-04-24
Ok, I was fed up with a lot of things melting down on my machine after upgrading to Feisty, that I did a fresh reinstall.  Things were working, including sound (which was one of the things Feisty destroyed).

Then while using gedit, I noticed warnings in the terminal that /usr/bin/esd was missing. I assumed those were sound events, and installed esound.

Sound stopped working.  I uninstalled esound, but sound still stopped working.

I checked ALSA mixer (Xfce's, alsamixergui, etc.). Nothing seems amiss. The GNOME Also Mixer shows "IEC958 Playback Source" unchecked. The terminal gives me warnings when I check/uncheck the field:
> ** (gnome-alsamixer:5540): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!
It doesn't remember if I check them off and exit. They are unchecked when I rerun the program.

I have already tried using the latest version of ALSA, compiling it, etc. No help there.

---

