---
title: "Install went great - x-server issues"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by brykatwags on 2006-03-10
I am a linux noobie and am running off of a compaq v2000 notebook.  Install went great - booted ubuntu for the first time through grub.  was almost done with first boot and it "failed to start x server"  Any suggestions on how to get past this? I really want to get this up and running

---

### Post by sarcasticfrench on 2006-03-10
Hmm... I don't know if the keyboard combo is the same on your comp as mine (I'm on an ibook g3) but try hitting ctrl-alt f1, logging in, and typing "startx". This happened to me once when I tried to boot without my Ethernet cable connecting me to the LAN. If that still doesn't work, maybe try reinstalling. I'm also using Kubuntu, not Ubuntu, so that might not work. but it's worth a try though.

---

### Post by dermotti on 2006-03-10
Prolly detected the wong video driver. You do

A. type: sudo nano /etc/X11/xorg.conf
find where place where it has your video driver, and change it to "vesa"

B: type: sudo dpkg-reconfigure xserver-xorg
and when it asks for a video driver, select vesa

---

### Post by brykatwags on 2006-03-10
Vesa worked - thanks!!!

---

