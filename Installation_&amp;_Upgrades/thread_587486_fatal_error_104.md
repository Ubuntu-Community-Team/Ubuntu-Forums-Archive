---
title: "fatal error 104"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by InGunsWeTrust on 2007-10-22
First off, I am an Ubuntu fanatic. I love Ubuntu, I love the things they have done with linux, but this is the most ridiculous error I have ever seen. Let me run you through this:

1. Ubuntu 7.04 works great.I have been using it since it came out.
2. I am on an Ubuntu 7.10 live CD right now. Everybody works. Clearly my hardware is supported or it would not have started.
3. After the install mysteriously GDM fails to start. If I log in and do startx I get fatal error 104 blah blah blah.

Why would the livecd work but not a real installation. Also why would it work in 7.04 but not 7.10, generally new distributions mean improvements.

I have an Intel 945 inegrated graphics card fyi (a VERY common graphics card).

If anybody has any ideas I would be very grateful.

---

### Post by Pumalite on 2007-10-22
With integrated graphics I'd recommend the Alternate CD for the installation. You might have to fix your xserver at the end of the installation anyway, but would be no problem. Come back when you are there.

---

### Post by InGunsWeTrust on 2007-10-23
I ended up solving it with

> sudo dpkg-reconfigure xserver-xorg

for some odd reason the graphic install was picking the wrong driver

---

