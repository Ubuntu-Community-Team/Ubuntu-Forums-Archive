---
title: "[SOLVED] Nvidia Multi Display Help"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by puner on 2008-07-30
Hello, I have two monitors and I recently installed Hardy 8.04. When I first logged in Ubuntu used my right (smaller) monitor without any permission. What I would like to do is use my left (bigger) monitor. I searched google for this problem and was lead to the Twinview tutorial here at the forums.

I installed the restricted Nvidia drivers and then in terminal I entered;

```
gksudo nvida settings
```

To enter the Nvidia control panel, but nothing happens...I dont see anything.

---

### Post by tamoneya on 2008-07-30
the correct command is:```
gksudo nvidia-settings
```

Note the spelling on nvidia and the hyphenation.

If that still doesnt work make sure it is installed with ```
sudo apt-get update
sudo apt-get install nvidia-settings
```
Then run the first command again.

---

### Post by puner on 2008-07-30
> **tamoneya said:**
> the correct command is:```
gksudo nvidia-settings
```

Note the spelling on nvidia and the hyphenation.

If that still doesnt work make sure it is installed with ```
sudo apt-get update
sudo apt-get install nvidia-settings
```
Then run the first command again.

^Thanks

It was the fact I didn't install the settings manager.

I was using this [tutorial]("http://ubuntuforums.org/showthread.php?p=1773584") before this post

---

### Post by tuxxy on 2008-07-30
YOu shold change your post to solved now

---

