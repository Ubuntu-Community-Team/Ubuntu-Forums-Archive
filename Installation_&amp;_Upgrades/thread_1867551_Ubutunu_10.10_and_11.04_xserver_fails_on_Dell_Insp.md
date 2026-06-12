---
title: "Ubutunu 10.10 and 11.04 xserver fails on Dell Inspiron 1545"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by rabilon on 2011-10-23
I was running Ubuntu 10.04 on a Dell Inspiron 1545 with an Intel mobile 4 video chipset. Under 10.04, the graphics are perfect (1366 x 768). I set up a dual boot and in the other partition I installed Ubuntu 11.10 which also works perfectly. So I went and tried to upgrade 10.04 to 10.10 (update manager) but then there was no X display. Using the command line I then updated to 11.04. Now I have an X display but it is a much lower resolution. I cannot tell what xserver it is using (as there is no xorg.conf file).

I don't understand how the graphics work fine under 10.04 and 11.10 (and always worked under earlier versions since 8.04 up until 10.04) but won't work with 10.10 or 11.04. How can you find out what Ubuntu is using as the xserver? I've tried creating xorg.conf files which Ubuntu tries to use, but they never produce a usable display. I would like to get the 11.04 partition working with the appropriate xserver. (I needed to upgrade from 10.04 to a newer version so I could migrate by Evolution mail and settings - could not go from 10.04 to 11.10).

---

