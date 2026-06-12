---
title: "Install HPLIP in 19.10"
date: 2019-10-19
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2019-10-19
What is the best terminal command line to use to install HP's HPLIP control in a fresh install on Ubuntu 19.10?

I have tried sudo apt install hplip but only get the message: hplip is already the newest version (3.19.6+dfsg0-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks in advance.Bob.

---

### Post by rbmorse on 2019-10-19
Not sure I understand the question, but if you're looking for the GUI front end for hplip you need:

sudo apt install hplip-gui

---

### Post by bob brazie on 2019-10-19
That it. Thanks.

---

