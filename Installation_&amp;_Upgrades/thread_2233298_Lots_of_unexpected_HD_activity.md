---
title: "Lots of unexpected HD activity"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by EnglishElectricAndy on 2014-07-07
I've upgraded from Xubuntu 13.10 to 14.04 two days ago (not an early adopter) and found that the LED indicating hard drive activity is illuminated all the time, along with the noise that I normally hear when the heads are scaning the drive. To be frank, I'm beyond my level of understanding as to why this is happening, typing 'top' into the terminal doesn't show what processes might be causing such activity.

---

### Post by tgalati4 on 2014-07-08
Perhaps you are out of RAM and are using swap:

```
free
```

---

### Post by Old_Grey_Wolf on 2014-07-08
You could try running iotop in the terminal. You may have to install it. When you type iotop in the terminal it will tell you how to install it. If it is already installed, it will tell you you need to use sudo. I don't remember if it was default in Ubuntu or if I installed it.

[ATTACH=CONFIG]254580[/ATTACH]

---

