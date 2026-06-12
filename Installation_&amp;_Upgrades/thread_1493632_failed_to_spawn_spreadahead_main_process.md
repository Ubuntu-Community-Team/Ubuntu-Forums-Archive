---
title: "failed to spawn spreadahead main process"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by dhayfule on 2010-05-26
Hi,

I have recently upgraded 9.10 to 10.04 through the alternate CD.

However, each time when I boot my system, post upgrade, I receive this error:

INIT:failed to spawn spreadahead main process: unable to execute: No  such file or directory

After that it waits for a long time to show the desktop.

Is this a bug with upgrade?

---

### Post by dino99 on 2010-05-26
goto synaptic and select mountall package reinstall it

sudo dpkg-reconfigure mountall
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dhayfule on 2010-05-27
tried it....
Still the same

---

