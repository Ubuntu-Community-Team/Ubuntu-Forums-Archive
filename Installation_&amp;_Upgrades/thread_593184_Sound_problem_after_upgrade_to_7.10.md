---
title: "Sound problem after upgrade to 7.10"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Ken Milburn on 2007-10-26
Under feisty I had correct alsa sound.  The soundcard is part of the motherboard.

After the upgrade to gutsy, I had limited sound or no sound (OSS was the only setting that worked).

The log in sound sometimes works, TVtime works & the sound preferences test - OSS works.
What does not work is audio CDs or ogg & ESD.

At log in I sometimes get Error Gnome settings daemon indicating a sound card settings problem.
I have installed a number of mixers with no change.

ALSAMIXER: function snd_ctl_open failed for default: no such device.

gconfaudiosink: Could not open resource for writing.

Device manager identifies my sound as C-Media PCI CMI8738-MC6 (model 55)
Sound Preference option OSS tests OK.  All other options fail.
The only hardware option available in Sound Preference is PCI IEC958 which I have un-selected
because of what I read in the postings.  The motherboard sound does not support optical output.

Ubuntu 7.10 LIVE appears to work correctly.

What options do you suggest?  Perhaps I should try a clean install.

---

### Post by Ken Milburn on 2007-10-31
I solved my problem by doing a clean install.
I formated the / partition and my problem still existed.
I formated both the / and home partitions and the install found my sound card.

What forced me to do the above was another problem which was my screen resolution became stuck at the highest possible resolution and would not accept a change.  I have not seen this so far on my new install.

---

