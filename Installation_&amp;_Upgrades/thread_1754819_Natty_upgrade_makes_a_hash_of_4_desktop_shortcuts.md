---
title: "Natty upgrade makes a hash of 4 desktop shortcuts"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by 81084997 on 2011-05-10
For years I've had ctrl + alt + 1-4 (keypad) as shortcuts to desktop 1-4. It's worked flawlessly under everything from Slackware, through Debian and even the gnarled mess that Ubuntu is becoming.
 
But now, ctl + alt + 1 dumps whatever window is active on my desktop to the bottom left corner of that desktop. Ctrl + alt + 3 dumps it to the bottom right corner; CA7 goes top left and you can guess the rest.

What is this remarkably useful feature called and how do I turn it off so that I can just switch to desktop 4 whenever I want to?

---

### Post by BlouBlou on 2011-05-10
It may be a compiz problem, try configuring it by ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by 81084997 on 2011-05-10
> **BlouBlou said:**
> It may be a compiz problem, try configuring it by ```
sudo apt-get install compizconfig-settings-manager
```

Quick thinking that Ubuntaneer!

It's the woeful 'put' plugin in compiz.

Seemingly on my default in Natty - perhaps some dev uses it :confused:

---

