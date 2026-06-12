---
title: "nVidia 6800GT (AGP) Install Probs"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by Leebobs on 2005-07-26
I have just installed Ubuntu 5.04 on a fresh hard disk with my new Graphics Card an ASUS 6800GT AGP.

Install went fine & text based start up is fine. When I enter X my mouse icon shows and responds correctly. However, the background is completly distorted, it appears as if 6 images have been interlaced on-top of each other.

I get no start up sound and entering a user name and password and hopefully pressing enter

does jack all

Anyone know of how to fix this issue

---

### Post by Leebobs on 2005-07-27
Bump.

Anyone?

---

### Post by varunus on 2005-07-27
Can you post your /var/log/Xorg.0.log file and your /etc/X11/xorg.conf?

You could also try hitting CTRL-ALT-F1 and then CTRL-ALT-F7 and see if your screen fixes, I've seen that work for some people.

You may want to just skip what I said above and install the nvidia proprietary drivers.  It may help you out.  There's a howto in the "Tips and Tricks" section of the forum, I think.  There's also one on [www.ubuntuguide.org](www.ubuntuguide.org) on how to install the NVIDIA proprietary drivers.  You should be able to do it from the console.

---

