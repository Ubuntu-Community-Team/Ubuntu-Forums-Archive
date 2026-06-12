---
title: "Precise 12.04 in Dell latitude e6510 internal microphone not working"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by mcarro on 2012-04-27
Fresh install of Precise Pangolin (12.04) on a Dell Latitude e6510 with intel audio.  The internal microphone does not work (nothing is registered and no audio signal appears in sound-related config windows).  Tried to configure driver with alsamixer.  Maybe it needs some specific options?

---

### Post by gordintoronto on 2012-04-27
In Sound Settings, in the Input tab, what is displayed? On my system, the default input volume was extremely low.

---

### Post by rfictus on 2012-04-29
This is what my input looks like: [http://imgur.com/NzTmv](http://imgur.com/NzTmv). Maybe you can relate mcarro??

---

### Post by mcarro on 2012-04-29
The levels were Ok.  Adding 

options snd-hda-intel model=dell-s14

to 

 /etc/modprobe.d/alsa-base.conf

made the internal mic work, but the external mic stopped working.  The internal one is more interesting for me now (don't have to connect stuff, etc)

Thanks for all replies.

---

### Post by rfictus on 2012-04-29
Any idea what I would have to add to /etc/modprobe.d/alsa-base.conf for my system? Vaio VPCCW16FG??

---

### Post by mcarro on 2012-04-29
> **rfictus said:**
> Any idea what I would have to add to /etc/modprobe.d/alsa-base.conf for my system? Vaio VPCCW16FG??

Sorry I can't be of help with this one...

---

### Post by rfictus on 2012-05-01
Right, so I added this bit of code:

options snd-hda-intel model=toshiba-s06

to: sudo gedit /etc/modprobe.d/alsa-base.conf

Works for my Vaio strange enough, maybe will fix your external mic too mcarro ??

---

### Post by shaktiman1234 on 2012-09-19
can someone suggest what to add for dell studio 1435

---

