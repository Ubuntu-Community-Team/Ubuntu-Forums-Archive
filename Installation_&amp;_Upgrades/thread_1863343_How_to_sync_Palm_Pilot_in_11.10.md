---
title: "How to sync Palm Pilot in 11.10?"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by heynnema on 2011-10-17
Palm sync worked fine in 11.04 using gnome-pilot. This option doesn't appear available in 11.10. I've tried all of the other sync utils that I can find in synaptic, or the software center (J-Pilot, Pilot Manager, etc.) and NONE of them work... let alone designed to sync datebook/contacts with Evolution.

Any ideas?

Cheers, Al
:confused:

---

### Post by kmichels on 2011-10-18
I also used gnome-pilot and now that doesn't work.  I did get J-Pilot work, but I want to sync with Evolution because it has a nicer interface.  Is there still a way to sync directly with Evolution?  Or if not directly is there a way to sync J-Pilot with Evolution?

---

### Post by heynnema on 2011-10-18
I tried to sync just my contacts (only) with J-Pilot as a test, and only 4 contacts came over. Am I missing something?

Cheers, Al

---

### Post by kjaspan on 2011-10-27
> **kmichels said:**
> I also used gnome-pilot and now that doesn't work.  I did get J-Pilot work, but I want to sync with Evolution because it has a nicer interface.  Is there still a way to sync directly with Evolution?  Or if not directly is there a way to sync J-Pilot with Evolution?
You say you did get Jpilot to work but did you get it to sync? I absolutely cannot connect. I have tried pilot-xfer --port=usb: --sync=<directory path> but that fails to connect too. Looks like we've been cut off at the knees with this release (alas). I would hate to be forced to revert to Windows.

---

### Post by kjaspan on 2011-10-28
> **kjaspan said:**
> You say you did get Jpilot to work but did you get it to sync? I absolutely cannot connect. I have tried pilot-xfer --port=usb: --sync=<directory path> but that fails to connect too. Looks like we've been cut off at the knees with this release (alas). I would hate to be forced to revert to Windows.
Well folks, some limited success. Referring to the bug report #138823 ([https://bugs.launchpad.net/ubuntu/+source/pilot-link/+bug/138823](https://bugs.launchpad.net/ubuntu/+source/pilot-link/+bug/138823)) I tried pilot-xfer with the debug settings suggested (PILOT_DEBUG=DEV PILOT_DEBUG_LEVEL=DEBUG PILOT_LOG=1 PILOT_LOGFILE=/tmp/pilot_log_file) and got the connect tones. However it was waiting to identify the user and I don't see a way to specify the user with any flag in pilot-xfer as yet. I will report back if I find something.

---

### Post by kmichels on 2011-11-02
> **kjaspan said:**
> You say you did get Jpilot to work but did you get it to sync? I absolutely cannot connect. I have tried pilot-xfer --port=usb: --sync=<directory path> but that fails to connect too. Looks like we've been cut off at the knees with this release (alas). I would hate to be forced to revert to Windows.

I didn't do anything special.  I plugged in the palm pilot using a USB cable.  I then pushed the hotsync button on the palm, and hit the hotsync button in the Jpilot program at the same time.  It then synced.

---

