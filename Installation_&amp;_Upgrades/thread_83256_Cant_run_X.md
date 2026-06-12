---
title: "Cant run X"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by espanhol on 2005-10-28
Hi there, I'm just a noob with linux, and today after installing the ubuntu 5.10, when i booted id, i am unable do run X, it appears me an error screen and then the message is something like this:

(EE) No device detected

Fatal Server Error:
No screens found

My gfx is an ATI x800gt

any1 can help me out here?
thanks

---

### Post by Ali_Baba on 2005-10-28
You should do sudo dpkg-reconfigure xserver-xorg.That worked for me :) and select Ati on driver list just for sure.

---

### Post by espanhol on 2005-10-28
It didn't work :( still can't detect the device

---

