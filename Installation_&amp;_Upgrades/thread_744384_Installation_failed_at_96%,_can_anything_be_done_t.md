---
title: "Installation failed at 96%, can anything be done to finish it?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by eFFeeMMe on 2008-04-03
The pc is a 5 year old laptop from HP, the hard disk has been changed 2 years ago but isn't in very good conditions.
During the installation it gave a problem saying something about the partition manager. The installer then just died, but the livecd kept on running perfectly fine. Booting from hard disk, the system cannot start the GUI, it reverts to the command line.

What does the installer do after the 96% mark? Should I try reinstalling or can I just finish moving some files? 96% is the farthest I got in installing Xubuntu onto the machine.

---

### Post by kellemes on 2008-04-03
Have you tried the following to get some graphical environment running?
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by eFFeeMMe on 2008-04-03
It's not doing much sadly. Asking me a bunch of questions about my keyboard, then overwriting a possibly-customized configuration, backing it up, and then prompting me to the command line again.

---

### Post by kellemes on 2008-04-03
try..
```
startx
```

---

