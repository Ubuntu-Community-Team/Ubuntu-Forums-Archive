---
title: "request: new videocard auto-runs dpkg-reconfigure"
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2006-04-21
I have Ubuntu 5.10 installed and it was working great, no problems on the install.  I then replaced my original video card with a new one and Ubuntu reported an Xserver error and refused to load the GUI.  I then had to use another computer to search the forums, repeatedly, until I found the advice to run 'sudo dpkg-reconfigure xserver-xorg' which finally fixed the problem.

My question/request is:
Can Ubuntu detect the change in videocard and automatically prompt the user "Would you like to reconfigure your video settings?"  

This simple step would have saved me about 30 minutes, and I'm sure it's a common problem, i.e, it probably happens to ANYONE who changes videocards.

---

### Post by gondilon on 2006-04-21
what kind of video card is it?

---

### Post by bsmith1051 on 2006-04-21
I started-off with an ATI Radeon 8500 and then replaced that with an Nvidia Geforce2 MX 400.

---

