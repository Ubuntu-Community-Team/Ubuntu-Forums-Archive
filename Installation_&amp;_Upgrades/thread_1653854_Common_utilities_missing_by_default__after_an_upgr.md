---
title: "Common utilities missing by default  after an upgrade to 10.04 (lucid)"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by newbee75 on 2010-12-27
Hi all, 

I had my desktop at an old debian release. After following the "upgrade" prompts from the update manager, I upgraded the system to ubuntu 10.04 (lucid). However, after the gnome desktop started following the upgrade, i noticed that a number of utilities like the "terminal" "vim" " gedit" etc were missing (they existed prior to upgrade)by default. I am having to manually install them using 'apt-get install' every time I try and use a utility and find it missing. Does anyone know : 

1)why these basic utilities aren't installed by default ? 

2) Is there a way I can select a "package" of these basic utilities and install them in one go as opposed to installing each of them as and when I  discover what is missing  ? 

Thank s a lot for your time and help!

---

### Post by wojox on 2010-12-27
Try this:

```
sudo apt-get update; sudo apt-get install --reinstall ubuntu-desktop
```

No that isn't common to have all those applications missing.

---

### Post by newbee75 on 2010-12-27
Thanks Wojox! I will give that a try..

---

