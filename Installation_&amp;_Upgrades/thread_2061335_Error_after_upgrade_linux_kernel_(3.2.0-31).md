---
title: "Error after upgrade linux kernel (3.2.0-31)"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by coder_1340 on 2012-09-22
I got lots of error such as
 - [Ibus]("http://en.wikipedia.org/wiki/Ibus") can't start 
 - [Weather Indicator]("https://launchpad.net/weather-indicator") can't start
 - Firefox always crash when i start it so I can't not access the internet (Now I'm using another OS)
I tried to start the previous version in the grub menu. But the error still happen. 
Can anyone tell me how to fix it? :confused:

p/s: Tell me if you need more information.

---

### Post by jerrrys on 2012-09-22
Hi coder :)  Did you do a partial update?  Sounds like you have limited access, so...

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And post the errors

---

### Post by coder_1340 on 2012-09-22
Hi jerrys, you can see the error [here ]("http://paste.ubuntu.com/1220578/")

---

### Post by jerrrys on 2012-09-22
Your PPA's are messing you up.  Are you using them?  I suggest commenting them out for the moment.  Lets take a look at your sources in terminal:

cat -n /etc/apt/sources.list

---

