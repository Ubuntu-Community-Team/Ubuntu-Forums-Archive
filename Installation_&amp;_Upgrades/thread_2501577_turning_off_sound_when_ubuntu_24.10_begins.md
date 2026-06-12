---
title: "turning off sound when ubuntu 24.10 begins"
date: 2024-10-13
forum: Installation &amp; Upgrades
---

### Post by tuesdaybarrett on 2024-10-13
How can you turn off sound when logging in?Thx for help

---

### Post by vincentwolff on 2024-10-24
I don't know if that breaks anything, but what worked for me was:
sudo mv /usr/share/sounds/Yaru/stereo/warty-startup.oga /usr/share/sounds/Yaru/stereo/warty-startup.oga~

the warty-startup.oga is the sound file that is played at startup, and if you rename it, nothing is being played.

---

### Post by tuesdaybarrett on 2024-10-25
big thx that worked for me.

---

### Post by corradoventu on 2024-10-26
In the login screen before entering the password, at the top right of the screen you have the icon to control volume

---

### Post by Dennis N on 2024-10-26
You can simply turn it off from Settings > Sound > Sounds > "Startup Sound" (on/off)

---

