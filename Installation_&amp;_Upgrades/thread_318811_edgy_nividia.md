---
title: "edgy nividia"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by marku on 2006-12-14
hope someone can help. using xubuntu and ubuntu 606 with nvidia fx5200 card. installed driver - (legecy) and configured with no problems. tried to install 610 u,k.x and none will get past black screen with "ubuntu$". can anyone help to get me into gui to install distro and driver? thanks for help. marku

---

### Post by ZERO_SHIFT on 2006-12-15
To install driver I recommend Automatix2 @ [http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38) Then selecting the install nVIDIA drivers.

As for returning to the GUI I think you should re-install.

However if you check the forums you might be able to fix the configure file to view the GUI again.

Good luck.

---

### Post by Titus A Duxass on 2006-12-15
The last time I looked the Automatix site had some problems.

As an alternative.

Make sure you have the correct repo's enabled.
Then do (from a terminal):
Sudo apt-get install nvidia-glx

Then:
sudo nvidia-xconfig

That works for me everytime.

---

