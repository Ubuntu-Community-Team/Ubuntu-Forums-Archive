---
title: "Firefox updates killed firefox"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by yma981 on 2010-07-07
I upgraded Firefox to v 3.6.6 among other packages. Now Firefox is refusing to start, it says starting then nothing starts, i repeat it multiple times and still nothing?!!!

---

### Post by tommcd on 2010-07-07
Did you upgrade firefox from Ubuntu's repos, or did you update firefox from firefox's own update notification?

Try starting firefox with a different profile from the terminal:
```
firefox -P
```
Or rename your .mozilla directory in your home directory .mozilla.bak, and then launch firefox.
This will rule out a corrupt profile as the source of the problem.
Also try disabling your addons. There may be an addon that does not work well with the newest firefox.

---

