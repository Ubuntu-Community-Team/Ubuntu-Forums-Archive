---
title: "ubuntu 8.10 unstable dual booting problem"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-11-29
I am experiencing that during dual booting I used vista with 8.10 sometimes it start ubuntu without any problem, but sometimes it goes to console and hang at "Starting Powernowd" then I have to manaully put the electricity of the computer else it hangs foreever their. I have used wubi to install ubuntu.

---

### Post by manishtech on 2008-11-29
You can come over this problem by removing powernowd

When selecting at GRUB prompt, select Ubuntu (Recovery Mode), then after it asks you in a blue screen what to do. Select to drop to root shell. Over there type

```
apt-get remove powernowd
```

Remember, this daemon lets you to control fan and other hardware power related settings. Though most of the time you wont be doing so.

---

