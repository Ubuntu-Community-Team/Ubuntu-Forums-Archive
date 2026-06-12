---
title: "ATI X1400 Mobility problems"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by winter_mute on 2009-03-26
I just updated to Jaunty, and I can't seem to get X working.  It comes out as a blank screen, with no errors in the logfiles.  I've tried manually setting the driver to radeonhd in xorg.conf, but that fixes nothing.  The GDM logs say it's unable to connect to X server.  Any tips?

EDIT:  Even the vesa driver doesn't get X running.  I have no clue what to do...

---

### Post by krazyd on 2009-03-26
Was this a fresh install of Jaunty, or an upgrade from intrepid?

Can you post your xorg.conf?

---

### Post by lazy13 on 2009-03-27
winter_mute, I have the same card and had similar problems.  I had to purge the fglrx packages and use the ati "wrapper" driver (directly referencing mesa in xorg.conf wouldn't work for me either.)

My advice, set your device to "ati" and purge any fglrx drivers.  See this link for more in depth instructions.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by winter_mute on 2009-03-27
Thanks, lazy!  That worked perfectly!  I guess the upgrade from 8.10 didn't disable fglrx like I expected it to.  So glad I didn't have to do a fresh install. =P

---

