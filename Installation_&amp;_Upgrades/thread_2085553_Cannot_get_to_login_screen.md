---
title: "Cannot get to login screen"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by ifatman2g on 2012-11-18
Ubuntu will not get to the log in screen, it changes from purple to a lighter purple to black, it keeps like that in a loop, I've installed GSM and gnome shell and it still keeps going this started immediately after I upgraded to 12.10

---

### Post by Bashing-om on 2012-11-18
ifatman2g;  Hi ! Welcome to the forum.

Upgraded -> were you using a proprietary driver in the former version ? The upgrade I understand breaks it....... requiring (un)install and (re)install. Methods differ depending on which vendor graphics card is installed.
Can You boot "recovery mode" and post results of terminal codes:
```
sudo lshw -C display
lspci | grep VGA

```Can you boot up with the "nomodeset" boot option ?
```
https://help.ubuntu.com/community/BootOptions
```information helps us to help you <== BDQ

---

