---
title: "Where does this regression belong to?"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-09-11
After recent updates, the light on my Thinkpad keyboard that indicates the sound off doesn't turn on anymore when pressing the mute button. Muting still seems to work but it's just the light that stopped.

Any ideas? Ideas on how to fix it too?

---

### Post by b3n87 on 2009-09-11
Although I cant help with anything else, I think your problem may be to do with switching from hal to DeviceKit

[http://www.ubuntu.com/testing/karmic/alpha5#hal%20deprecation]("http://www.ubuntu.com/testing/karmic/alpha5#hal%20deprecation")

---

### Post by andresmh on 2009-09-12
I ran this perl script to test the turning on/off of LEDs but I didn't see any lights blinking:
```

foreach(1..32){ $cmd = "xset led $_; sleep 2; xset -led $_"; print "$cmd\n"; system($cmd); print "\n"; }

```

---

