---
title: "Install local packages using aynaptic"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by MBG1987 on 2010-06-17
hello
I wonder if i can install packages that already exist in local directory using synaptic
for example:

I downloaded a set of programs with there dependencies and stored them in whatever folder, and i'd  reinstalled my distro and i need to install just google chrome browser for instance, it's will be very difficult to install it among other packages.

it will be very useful if i forced synaptic to install chrome locally instead of downloading and installing them from the internet.

if some one tell me how to accomplish these approach i will be very grateful to him
Thank you in advance

mahmoud

---

### Post by leorolla on 2010-06-18
You can copy the .dev files to /var/cache/apt/archives
Run
```
sudo apt-get install chromium -s
```
and see what it wants to download. If it is fine, remove the -s.

---

