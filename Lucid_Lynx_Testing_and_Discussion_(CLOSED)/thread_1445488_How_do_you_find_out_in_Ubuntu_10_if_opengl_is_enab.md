---
title: "How do you find out in Ubuntu 10 if opengl is enabled and functioning?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 3junior on 2010-04-02
How do you find out in Ubuntu 10 if opengl is enabled and functioning?  How do I change my video card settings?  There is no more xorg.conf

---

### Post by webme on 2010-04-02
if you haVe nvidia card, check system/administration/nvidia x server settings/x server display configuration and change rezolution, refresh rate,etc!!!
if you don't have nvidia x server settings installed, go to prefferences/hardware drivers, activate the recomended nvidia driver!!! THIS IS ONLY FOR NVIDIA!!!
after you install nvidia drivers, check again system/administration/hardware drivers, and make sure THE DRIVER IS ACTIVATED AND CURENTLY IN USE---that mean you have opengl active!!!!

a personal advice(use with carefullness) after you sellect rezolution,redresh rate, etc don't save to xorg.conf ---this has worked for me(i don't know about others_

---

### Post by Starks on 2010-04-02
> **3junior said:**
> How do you find out in Ubuntu 10 if opengl is enabled and functioning?  How do I change my video card settings?  There is no more xorg.conf
glxinfo

---

### Post by 3junior on 2010-04-02
I have instated ubuntu as a guest os in virtualbox

---

### Post by dcstar on 2010-04-02
> **3junior said:**
> I have instated ubuntu as a guest os in virtualbox

3D graphics are a rarity in VM environments.

---

### Post by ratcheer on 2010-04-02
1) Install package mesa-utils

2) glxinfo | grep "OpenGL renderer string"

Tim

---

