---
title: "No Sound/Can't open Sys Setting after 10.10 RC upgrade"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by VaiPhile on 2010-10-02
Last night I upgraded to 10.10 RC, and everything went smooth.  A lot of problems were resolved in the upgrade, but unfortunately I got two new problems.

1.  No Sounds at all.  My speakers hum, and I can control the level of the hum/mute with Kmix, but no sounds makes it through.  So Kmix is controlling the hardware, but somewhere the sounds isn't making it there.

2.  No system settings.  The system settings panel appears in the app tray when I run it, but after a minute of thinking (and not opening) it disappears.

```

:~$ sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I appreciate the help!!

---

### Post by VaiPhile on 2010-10-02
Sound is back!  I opened Phonon and elevated the analog output above the digital in all of the categories, and :guitar:!  That solves the sounds... but the system settings still refuses to open.  

I had this problem before with the desktop effects after the 9.04 upgrade I think.  It was a driver initialization issue that was killing it.  Any ideas?  I'm really not sure where to start since the setting panel doesn't open at all.

---

### Post by lflindsey on 2010-10-20
Removing PulseAudio fixed the problem for me.  Also installed the gstreamer backend for phonon.  I can't say for sure which had the desired effect, but pulse seems to be more trouble than its worth either way.

---

