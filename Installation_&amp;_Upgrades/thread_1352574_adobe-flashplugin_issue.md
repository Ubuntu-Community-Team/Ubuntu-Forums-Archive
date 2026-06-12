---
title: "adobe-flashplugin issue"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2009-12-11
I have an adobe-flashplugin update that is showing in Update Manager. Yesterday I had an update for the installer for adobe-flashplugin. 

I was able to d/l and install the installer through the Update manager. The adobe-flashplugin is still listed, but I am not able to select it to update.
'
Anybody else having this issue? Or could someone point me in a direction to fix this?

Thanx in advance!

---

### Post by aysiu on 2009-12-13
I'm not sure I understand the problem.

Can you post a screenshot of your Update Manager window? Is the option for upgrading Adobe Flash Plugin greyed out or something?

---

### Post by lsutiger on 2009-12-13
Thanx aysiu! I have followed you a bit here and had one of my first experiences with Linux made better through your help.
Now down to business....
I can not select the update. attached is my awful GIMP'd screenshot with the adobe update which I can not select. It is not greyed out...I just can not sleect it to be installed/updated.

---

### Post by aysiu on 2009-12-13
Interesting. Can you close that window and then paste these commands into the terminal and paste the output back here? ```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```

---

### Post by lsutiger on 2009-12-13
Thank you once again! 
I ran the update via cli and it is now removed from update manager and the update was applied...hopefully it fixes some jumpiness to flash video!

Thanx again!

---

