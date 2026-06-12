---
title: "How to Switch to Kubuntu?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Landscapeman on 2008-06-19
I am trying to convert to Kubuntu on my desktop. My desktop is a dual boot with windows and ubuntu. How do I completely switch to the KDE environment? I have been told in the past that you can do this without reformatting and loosing my information on the windows side. Any advice that would help me? Thank You.

---

### Post by wolfen69 on 2008-06-19
ctrl-alt-F1. you will then be in a terminal session. do ```
sudo apt-get remove ubuntu-desktop
``` then ```
sudo apt-get install kubuntu-desktop
``` then alt-F7 to get back to a GUI.

---

### Post by luvr on 2008-06-19
Just install the **kubuntu-desktop** package (and all its dependencies), using either Synaptic or by running the following command:
```
sudo apt-get install kubuntu-desktop
```
Afterwards, on reboot, you will be offered the option of logging in to either KDE or GNOME.

---

### Post by wolfen69 on 2008-06-19
he asked: > How do I ***completely*** switch to the KDE environment? that means removing gnome.

---

### Post by jualin on 2008-06-19
I always had that question and but never asked it thanks dude, i learned something new today.

---

### Post by Landscapeman on 2008-06-19
Thanks for the advice everyone. I have ubuntu on three computers and I figured I would use the KDE on one.

---

