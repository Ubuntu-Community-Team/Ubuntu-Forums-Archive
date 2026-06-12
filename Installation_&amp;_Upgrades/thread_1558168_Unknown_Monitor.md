---
title: "Unknown Monitor"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by eyeamok on 2010-08-21
I installed 10.04 on new computer for office, got everything working great at home with old 15" monitor, took to office hooked up to Multisync 97f monitor, and not recognized 640x480 is best. I Have onboard Geforce 6150se/ 430 and have the newest driver installed from Nvidia 256.44. I tried to install everything that said multisync in synaptics but screen jumps around when trying to click on anything because it don't fit right. Can Anybody Help me or tell me what to do?? Or should I get a different Monitor, which I really don't want to do. Please Help

Thank You

---

### Post by eyeamok on 2010-08-22
come on, someone , anyone, have an answer??

---

### Post by davidmohammed on 2010-08-22
how are you trying to change the resolution - 

try

sudo nvidia-settings

---

### Post by eyeamok on 2010-08-22
I will try that tomorrow morning when I get to office, The way I was trying was from /Preferences/Nvidia Settings. The Nvidia app installed when I installed driver and that is what i was trying to use. I tried installing a generic nvidia driver from synaptics and it gave me 800x600 with no options, From there I tried /Preferences/monitor and was unknown monitor, So I reinstalled proper driver and tried using tool that installs in preferences and administration, still NoGo.

---

### Post by davidmohammed on 2010-08-22
the command I gave you is the same as when you navigate through preferences.

Sounds like you may need to clean up your nvidia driver installation.

suggestion:

sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then navigate to 

administration - hardware drivers.

activate the recommended driver given to you.

reboot

then use nvidia-settings.

---

### Post by eyeamok on 2010-08-23
Thank You very much, that fixed the problem, once again Thank You 

Solved

---

