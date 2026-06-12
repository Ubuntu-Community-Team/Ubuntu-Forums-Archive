---
title: "lubuntu 11.10 installation stuck on &quot;Starting bleutooth&quot;"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by gillbert on 2012-04-11
I'm trying to install linux (lubuntu 11.10) on a old Compaq Evo N1020v (with internet connections. I've now twice managed to install it successfully, but it won't start. It will boot just nicely from the live lubuntu CD. Now it boots up, shows a lubuntu screen and after that ger suck on a black screen with the text 
```

* Starting NTP server ntpd                                                   [ OK ]
* Starting bluetooth                                                         [ OK ]
_

```

After I force a restart I get a similar screen (without showing the lubuntu screen before) with the text
```

[   25.068044] AC´97 1 access is not valid [0xffffffff], removing mixer.
[   25.068130] ali mixer 1 creating error.
_

```
Next time after restarting:
```

* Starting NTP server ntpd                                                   [ OK ]
* Starting bluetooth                                                         [ OK ]
[   24.404040] AC´97 1 access is not valid [0xffffffff], removing mixer.
[   24.404128] ali mixer 1 creating error.
_

```
And then the second screen again after the next restart, and so on.

Has anyone encountered something similar?

---

### Post by gillbert on 2012-04-12
Installed lubuntu from the live CD instead of the alternate and now it works (just to let you know).

---

