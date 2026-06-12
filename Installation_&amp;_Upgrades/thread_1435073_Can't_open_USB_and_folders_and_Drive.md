---
title: "Can't open USB and folders and Drive"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by black scorpio on 2010-03-21
After I update my karmic koala yesterday 03.20.2010 their is no sight of auto pop up upon inserting USB drive and also folder from Places shortcut can't be open. What was the problem please help me.

---

### Post by quixote on 2010-03-23
Maybe something didn't upgrade correctly.  Try```
sudo dpkg --configure -a
```That should try to fix anything that's broken.  If that doesn't do it, try booting into recovery mode, plug in an ethernet cable, choose the option for "root shell with networking", and run the most recent upgrades again: ```
apt-get update
```followed by ```
apt-get upgrade
``` (You don't need "sudo" first because you're already root.  For that reason also be very careful not to make any typos.)  

Once it's all done, type ```
reboot
```and see if it helped.

---

