---
title: "Upgrading from 9.04 to 9.10"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by markinmadison on 2010-04-03
I have tried to upgrade from 9.04 to 9.10. I install the upgrade to 9.10. When I go to restart the computer, I come to the sign in page and sign in. After I sign in ubuntu 9.10 tries to build the desktop. This is where I come to a blank white screen. The arrow is configured, but there is no desktop. Just white space. I have tried this twice. Am I doing something wrong? 

I am on an:
Intel(R) Pentium(R) 4 CPU 1.80 GHz

Available disk space: 30.7 GiB
Memory 1002.1 MiB

Can someone help?

---

### Post by Naitsirhc Hsem on 2010-04-03
try going to ctrl+alt+F6 and login.  try to update the computer or create a new user

---

### Post by markinmadison on 2010-04-03
I did log in from the command line, but then I didn't know what to do from there...I feel very stupid...

---

### Post by kblft on 2010-04-03
This sounds like it might be a video driver issue

Can you specify which graphics card you're using ? and which screen?

Also, if you can login from terminal - can you please post your /etc/X11/xorg.conf file?

---

### Post by markinmadison on 2010-04-03
That is exactly what it was. It was actually the video card that put into the puter before I bought it. It is a nvida card. I replaced it with a older card from one of my other puters....thanx for all of the help!!!

---

