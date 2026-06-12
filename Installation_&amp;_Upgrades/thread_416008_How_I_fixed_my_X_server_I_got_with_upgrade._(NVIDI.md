---
title: "How I fixed my X server I got with upgrade. (NVIDIA)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by B3Nji on 2007-04-20
After it had install all of the bits and bobs to upgrade my system it rebooted. Then I was greeted with a nice X failier screen. All I did was

sudo nano \etc\X11\xorg.conf

changed the device driver from "nvidia" to "nv"
rebooted the pc again. X worked. 

Installed the new version of Automatix and got it to install the new nvidia driver for me.. all went well. 

Now I am happliy using the new ubuntu with wonderful compiz enabled :)

Its all good. 

You have to expect a few teething problems with any upgrade I think..

Have fun!!

---

