---
title: "uodated to 23.04 and Firefox lost all settings, passwords, and bookmarks!"
date: 2023-04-20
forum: Installation &amp; Upgrades
---

### Post by leopards on 2023-04-20
After the updating to 23.04, a new version of Firefox was installed, and now all my settings, passwords, and bookmarks! are gone, and it will not let me set my old profile to default!! Help!

---

### Post by bimblesticks on 2023-04-21
Firefox has been installed as a snap package by default since Ubuntu 21.10. Snap packages are updated and managed by snapd, the system update shouldn't have had any effect on this.

Did you install Firefox in a different way at some point? If it was installed from a PPA or something it could have been affected by the update.

You mention all your settings, passwords and bookmarks are gone, but then reference your old profile - can you see your old profile in `about profiles`? If it's not letting you set it to default is it giving you a specific error message?

---

### Post by leopards on 2023-04-21
When I set it to default profile, it tells me it is from and old version and might corrupt the data then it only gives the options to cr3ate a new profile or quit!

---

### Post by #&amp;thj^% on 2023-04-21
If you still have the older >>".mozilla', then delete the newer ".mozilla"
It's in your home/user:
```
ls '/home/me/.mozilla' 
extensions  firefox
```
I had to replace the whole *.mozilla* folder before my older restore folder would allow the change.
Make sure you have a back-up first. Good Luck

---

