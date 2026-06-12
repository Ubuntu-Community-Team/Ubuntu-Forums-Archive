---
title: "Finally installed, but more problems.."
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by RageWarp on 2007-11-05
so i finally got the alternate cd to boot and install, but now when ubuntu loads up at the logo screen with the load bar it just hangs at a black screen after that with nothing. i have no idea what the problem is.
can anyone help

---

### Post by Pumalite on 2007-11-05
Try:

Ctrl+Alt+F1 to get command line.
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
(I'm not sure is a graphical interface problem, but you don't loose anything trying)

---

### Post by RageWarp on 2007-11-05
well ive tried the sudo dpkg-reconfigure command already by pressing esc before it boots, and i chose the vesa driver and i still get the same problem

---

### Post by Pumalite on 2007-11-05
Post your specs. You might be trying the wrong iso. (might need a lighter Desktop?) Bad burn? [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x, etc.

---

