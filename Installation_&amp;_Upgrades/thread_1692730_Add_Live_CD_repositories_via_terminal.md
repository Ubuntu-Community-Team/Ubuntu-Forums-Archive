---
title: "Add Live CD repositories via terminal?"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by avatarmonkeykirby on 2011-02-21
I regularly break my Ubuntu installations, and usually find ways to fix them by booting into the live disk. This time I broke the gui and don't have any network. How do I add the CD repositories so I can "apt-get" from the live disk?

---

### Post by mikewhatever on 2011-02-21
Try **sudo apt-cdrom add** - more info on what it does in 'man apt-cdrom'.

---

### Post by avatarmonkeykirby on 2011-02-21
```

sudo apt-cdrom add -a
sudo aptitude update

```

thanks mike =]

---

