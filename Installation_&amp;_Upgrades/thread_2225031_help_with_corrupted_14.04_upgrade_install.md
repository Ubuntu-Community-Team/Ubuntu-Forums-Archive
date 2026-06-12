---
title: "help with corrupted 14.04 upgrade install"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by mshallop on 2014-05-19
I installed 14.04 by upgrading from 13.10.  I've have a few issues, but nothing preventing me from working.

Today, I started having problems with my headset - it no longer showed up in my device listings, and although I could control volume settings from the headset controls, no sound was sent to the headset and the headset's mic was not recognized.

I tried update alsa-utils but no update, then I r&r'd pulse audio packages and that's when everything went south.

On reboot, I lost a crapton of stuffs - in my system settings window, I now only have Language Support, Security & Privacy, Printers, Landscape Service, and Software & Updates.  Everything else is gone.


I removed the pulse-audio packages I installed previously and rebooted but no change.  I updated the available packages with apt-get and rebooted - no change.

Since I upgraded from 13.10, I never created an install disk.  

Is there a command or set of commands that can validate the 14.04 base install and reload w/e packages went missing without having to do a complete re-install from media and losing all my files?

thanks...

---

### Post by mshallop on 2014-05-19
[COLOR=#333333][FONT=UbuntuRegular]I ended up removing the packages that I added:[/FONT][/COLOR]
sudo apt-get purge pulseaudio paprefs pulseaudio-esound-compat kmix
[COLOR=#333333][FONT=UbuntuRegular]and then I reinstalled the desktop:[/FONT][/COLOR]
sudo aptitude install ubuntu-desktop
[COLOR=#333333][FONT=UbuntuRegular]I got all of the system-setting/control panel option back. I rebooted and confirmed that the changes persisted and my environment is back to as it was.


Posting this answer in case it helps someone else.[/FONT][/COLOR]

---

