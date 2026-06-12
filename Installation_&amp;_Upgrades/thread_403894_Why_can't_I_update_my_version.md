---
title: "Why can't I update my version?"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by Red Knuckles on 2007-04-07
Why does Adept [in Kubuntu Feisty] tell one a new version upgrade is availalbe and then when one selects to install it it then tells you 'Could not download release notes' Please check that your internet connection is active???   How may I update my version??? :-?  Obviously I have a 'net connection or I couldn't run 'Fetch Updates'.  I also ran 'sudo aptitude dist-upgrade' and sudo apt-get dist-upgrade' and they did nothing at all. Anyone know what's up???:confused:

---

### Post by Apostata on 2007-04-08
Going through the same thing here.

---

### Post by sk8dork on 2007-04-08
same here...maybe they're getting ready to release an update but they don't quite have the version notes up yet?

---

### Post by zvacet on 2007-04-08
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by sk8dork on 2007-04-08
> **zvacet said:**
> ```
sudo aptitude update && sudo aptitude upgrade
```

this does not do it. the issue here is that in kubuntu feisty while using adept-manager after you fetch updates the version upgrade button becomes available and when you press it and then click next you get an error: could not download the release announcement. please check that your internet connection is active.

---

### Post by Apostata on 2007-04-10
bump

---

