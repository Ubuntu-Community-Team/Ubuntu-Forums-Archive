---
title: "[SOLVED] Sound Drivers from Creative"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by Tom11235 on 2008-11-30
Hi, 
I am trying to install sound drivers for my X-fi Xtreme Gamer sound card from creative on ubuntu. I am confused about the instructions included in the readme, and have found that most threads state that OSS or ALSA must be installed in order for the sound card to be used. I was wondering if anyone could help me resolve this matter. The instructions in the Readme were as follows: 

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install



I would really appreciate it if someone could explain the installation process to me. Thanks in advance.

---

### Post by oldos2er on 2008-11-30
Use "cd" to change directory to where the source code is. Then type these commands one at a time:

sudo make

sudo make install

---

### Post by Tom11235 on 2008-11-30
Thank you, sound works fine now.

---

### Post by oldos2er on 2008-11-30
Glad you got it working!

---

