---
title: "video problem"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by ethanvil on 2006-06-11
I have a NVIDIA Vanta card and when the desktop is suppose to be showing all i see is a black screen with a cursor! please help so i can resolve this problem and so i can stop using windows and be a first time linux user thanks

---

### Post by dermotti on 2006-06-11
from command line run

**sudo apt-get install nvidia-glx**

once thats done run
[B]
sudo dpkg-reconfigure xserver-xorg[/B] and select **nvidia** as your driver.

reboot or restart X.

If that doesn work, re-run  **sudo dpkg-reconfigure xserver-xorg** and select the **vesa** driver, then reboot.

---

### Post by Jason_25 on 2006-06-11
You might need nvidia-glx-legacy since that's a TNT based card.

---

