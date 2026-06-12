---
title: "No Sound on Intel NUC D34010WYK i3 Haswell Intel HD 4400"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by parisv on 2014-01-30
I'm trying to get the sound working via the mini hdmi socket on an Intel NUC D34010WYK. It uses an Intel i3 with integrated 4400 graphics.


Here are some details that might be useful:

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


# uname -r 
3.11.0-13-generic

# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


I've downloaded and installed the intel drivers from here: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

But no joy.

Not sure if I should be using alsa/pulse audio or xfce-mixer/gstreamer? not sure how to install alsa either?

at the moment all i have in sound video is alsamixer gui which was me messing around installing stuff.

---

### Post by parisv on 2014-01-30
h/w picture attached

---

### Post by Marc_Aronson on 2014-08-23
Did you ever solve this problem? I am having on-again, off-again with my intel NUC using mythbuntu 14.04...

---

### Post by parisv on 2014-08-25
No, I didn't spend to much time on it though, ended up using windows!

---

