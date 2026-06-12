---
title: "Automatix"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by aibradford on 2007-03-10
When i open automatix, the splash screen comes up, it loads the needed things... then nothing. It just is gone. Any help?

---

### Post by wireddad on 2007-03-10
Silly question, are you sure you had installed the correct version?

---

### Post by neymac on 2007-03-11
> **aibradford said:**
> When i open automatix, the splash screen comes up, it loads the needed things... then nothing. It just is gone. Any help?

After the last update the same occurs  here.

---

### Post by SinoDave on 2007-03-11
I had the same problem, and the fix for me was really simple. Try running Automatix from the terminal (automatix2 from the terminal prompt) and see if it errors out with a missing iPod icon. If so, just run the following command from the terminal prompt:

```
sudo cp /usr/share/icons/Tango/24x24/devices/multimedia-player.png /usr/share/icons/Tango/24x24/devices/multimedia-player-ipod-video-black.png
```

Hope this helps!

-SinoDave

---

### Post by MyNameUhBorat on 2007-03-11
Awsome post. You just saved me from pulling me hair out. lol

---

