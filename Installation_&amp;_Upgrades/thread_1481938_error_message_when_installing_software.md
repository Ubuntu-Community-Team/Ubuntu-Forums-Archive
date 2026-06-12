---
title: "error message when installing software"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by absolute beginner on 2010-05-13
I'm getting an error message while trying to install new software with the software centre. the message says the previous installation failed and that i have to repair it before i can install or remove any programs and i don't know how to do it can anyone help?

---

### Post by dino99 on 2010-05-13
instead of using "software center" goto : system admin synaptic and select your package from there

how to repair with a console (ctrl+alt+f2):

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by redshoes702 on 2010-05-13
Dino99 - I have same problem and have tried to follow your advice, but I cannot find the opgrade package. How do I find it? The sudo commands does not lead til upgrade! Thanks for your help. Per

---

