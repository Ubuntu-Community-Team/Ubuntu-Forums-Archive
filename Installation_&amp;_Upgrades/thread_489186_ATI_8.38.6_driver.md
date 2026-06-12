---
title: "ATI 8.38.6 driver"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by cddot on 2007-07-01
Has anyone tried installing this? 

According to the instructions from the download page, all you need to do is run the script: sh ./ati-driver-installer-8.38.6-x86.x86_64.run, and a window should pop-up for you to select a few options. But I don't get any windows? It does run and display some info about uncompressing etc and that's it. And no window. Where has the window gone?

---

### Post by Pumalite on 2007-07-01
In general, before attempting to install graphics driver, you should have: kernel-headers matching your kernel, make, automake, autoconf, latest gcc. And also try 'sudo apt-get install build-essential' Also make sure you have your driver in /home/<username>, and when you install, you do it as root: 'sudo sh xxxx'

---

