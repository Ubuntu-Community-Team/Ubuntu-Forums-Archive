---
title: "upgrade to 14.04 touchpad issues"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by cropr on 2014-04-26
I have a Dell XPS 13, that I just updated from 12.04 LTS to 14.04.  After the upgrade my touchpad is no longer working as it should.  I can use it as a mouse but, I can no longer use 2 finger scrolling or 2 finger tap for a right-click.  The touchpad is available in in the 'xinput list' command, but using synclient it complains with 'no synaptic driver loaded'.  I don't get a touchpad tab in system settings When looking in dmesg  I get following 4 lines
 
```
[23374.821709] psmouse serio1: synaptics: device claims to have extended capabilities, but I'm not able to read them.
[23375.021874] psmouse serio1: synaptics: device claims to have extended capability 0x0c, but I'm not able to read it.
[23375.422201] psmouse serio1: synaptics: Unable to initialize device.
[23380.826643] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input19
```

Any clue how to solve this?

---

