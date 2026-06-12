---
title: "ugrade manager hanging"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by rogerdokon on 2008-05-19
Hi,

I have been using Ubuntu for a few versions. It has been working pretty well so far. I believe I am on the latest release. 

I been having a problem with the upgrade manager freezing and not downloading or installing patches that have been piling up. I have read some blogs that have help me install patches by hand. After doing this I still have 17 patches that won't install by hand and the upgrade manager will not show in the tray on the right side bottom. I tried removing and installing  several time with no luck.
I need some help.

Regards

Roger Okon

---

### Post by dstew on 2008-05-19
Try these commands:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```After that check if your Update Manager is working better.

---

