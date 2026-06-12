---
title: "Opengl?"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by TheCadaver on 2011-04-20
I'm just wondering, is there any simple way to get opengl on ubuntu 10.10? I've read some posts but they weren't on maverick, and were years old. I just want opengl for high performance graphics on games. that's all ;)

---

### Post by mikewhatever on 2011-04-20
It would have been great if you could install some OpenGL packages, and then could run the latest games on an old Intel GPU, but it's not that simple. Do you have a graphics card that supports opengl? Can you post the model?

---

### Post by tensor9000 on 2011-04-20
You can install allegroGL package to use opengl in ubuntu.

---

### Post by TheCadaver on 2011-04-25
> **mikewhatever said:**
> It would have been great if you could  install some OpenGL packages, and then could run the latest games on an  old Intel GPU, but it's not that simple. Do you have a graphics card  that supports opengl? Can you post the model?

My Graphics card does support opengl. model is by HIS, "ATI Radeon HD 4670".

> **tensor9000 said:**
> You can install allegroGL package to use opengl in ubuntu.

Also, I can't seem to find AllegroGL. Where is it, in the synaptic package manager?

---

### Post by TheCadaver on 2011-06-09
bump

---

### Post by TheCadaver on 2011-06-15
bump..

---

### Post by TheCadaver on 2011-06-23
bump.

---

### Post by foresthill on 2011-06-23
You might have to revert to 10.04 for Opengl support:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by urbentom on 2011-07-16
im having the same problem of trying to install OpenGL yes my graphics card supports it and it tells me to download a file (which is called 'NVIDIA-Linux-x86_64-275.19.run') but what do i do now?

---

### Post by Mr. Shannon on 2011-07-16
You should first make sure that you have the proprietary drivers installed (use Additional Drivers in Ubuntu).  OpenGL should work at this point but an easy way to make sure everything is pulled in (including dev files) is to install freeglut (through the repository).

---

