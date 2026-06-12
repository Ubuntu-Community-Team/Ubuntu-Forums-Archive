---
title: "Flash Player will NOT stop trying to install itself"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by Pinkbelly on 2007-02-25
Whenever I try and install/update something (Beryl, wine, etc), a setup for flash player always pops up during the install/upgrade.  This is very annoying.  Any tips for stopping the rogue flash player install?

---

### Post by solar george on 2007-02-25
Have you ever tried to install flashplayer?

---

### Post by Pinkbelly on 2007-02-25
Yep, as I write this im using Flash.  It just keeps trying to download and install itself over and over, whenever I update/install something completely different.

---

### Post by solar george on 2007-02-25
Try removing any third party repositories.

---

### Post by Pinkbelly on 2007-02-25
Ok, I removed all 3rd party repositories and tried to install something (amsn).  Flashplayer still tried to get me to accept license agreement to download and install.  arg!!

---

### Post by Pinkbelly on 2007-02-25
Any other tips?  This is getting frustrating.

---

### Post by solar george on 2007-02-25
Try going through the install.

---

### Post by chickensofdoom on 2007-02-25
I'm actually having the same problem right now. I installed flash, and now it tries to install itself every time I install something. I tried going through the install process and it just fails.

---

### Post by chickensofdoom on 2007-02-27
Figured out the solution.

Most likely after trying to install Flash plugin, you still had to reinstall it via firefox for it to work, right? If so, you had the same problem as me.

Simply open up a terminal and use
sudo apt-get remove flash**plugin**-nonfree

It will leave flash **player** intact, and stop trying to install itself at every install.

---

