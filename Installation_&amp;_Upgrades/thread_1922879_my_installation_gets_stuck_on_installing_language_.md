---
title: "my installation gets stuck on installing language packets"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by ADIO85 on 2012-02-09
i have tried rebooting and restarting the installation but the same thing keeps happening. the installation gets stuck on installing language packs. it gets stuck at about 30% i tried leaving it but after 2 hrs nothing.....plz help

---

### Post by ADIO85 on 2012-02-09
this is my first time trying ubuntu or any linux os

---

### Post by ConServis on 2012-03-15
Hi,
I'm putting this in all instances where I find something abojut the "Installing languages" crash.

I had the same, time after time, until ......

- Start from CD/DVD/USB installing device
- DISCONNECT FROM YOUR INTERNET CONNECTION *** MOST IMPORTANT STEP
- Switching off all automatic updating during install > do this after it's properly installed (automatically)
- Not installing the Fluendo extra drivers > do this after the install: sudo apt-get install ubuntu-restricted-extras
- Start install
- Restart computer
- do above-mentioned updates (momentarily some 380 Mb) and Fluendo install.

Doing it this way (disconnect from Internet BEFORE install) already made it possible to install 2 times where before it crashed on the language install.

Good luck and enjoy Oneiric,
Hans

---

### Post by winh8r on 2012-03-15
When the Ubuntu installer is running , there is a "SKIP" button on the screen above the progress bar when language packs are being downloaded, just click it and the process will skip downloading the extra language packs and continue with the installation.

---

