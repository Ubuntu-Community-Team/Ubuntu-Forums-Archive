---
title: "I can't find Wine..."
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by 1337 Killer on 2006-09-03
I just installed the wine package from Synaptic Package Manager and I can't find it in my "Applications" menu. Can anyone help me? I've even tried installing it with my Terminal.

---

### Post by orb9220 on 2006-09-03
It is not a program per sa so much as a command to run.
Hit alt-f2 and enter wine config for configuring to install a windows  program is done by the command line like: sudo wine dvdshrink32.exe would start the the install process.

---

### Post by 1337 Killer on 2006-09-03
Thanks alot for the quick response

---

### Post by orb9220 on 2006-09-03
sorry that should be winecfg in a term or alt-f2

---

### Post by 1337 Killer on 2006-09-03
Alright, I installed STEAM, but when i click on the ink file, it says it can't display it. I tried saving it into my other hard drive where Linux is but it said it had to be in C:.

---

### Post by orb9220 on 2006-09-04
all Programs installed by wine must go in the default file structure it creates. It creates a fake windows directory structure to handle things. 

That is why you have to use wine to install the app in the first place.
Hope this helped.

---

