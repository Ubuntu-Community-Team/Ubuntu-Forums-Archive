---
title: "New Video Card - No Internet"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by hecter on 2008-03-25
Alright, so I've installed a new video card, it works fine in Vista but when I tried to boot up Ubuntu, it flipped out on me and all I got was a black terminal screen with white font and I have no idea what to do. Also note that I have no internet connection as of yet because I have failed to get ndiswrapper working. How do I install the video card? I have the disk and an internet connection on a different OS (same comp, two OS's) as well as a memory key to put any downloaded files incase the driver on the disk won't work in the linux environment...

---

### Post by unoodles on 2008-03-25
at the terminal screen simply type:

sudo dpkg-reconfigure -phigh xserver-xorg

then reboot by typing:

sudo shutdown -r now

---

### Post by hecter on 2008-03-25
Didn't work, told me I had conflicting instructions.

---

### Post by hecter on 2008-03-26
Bump?

---

### Post by hecter on 2008-03-27
So... Can anybody help? Please...

---

### Post by zvacet on 2008-03-28
```
sudo dpkg-reconfigure xserver-xorg
```

when you get to the drivers stage select **vesa** driver and continue to the end.After reboot you should have basic graphic and then you can go for your card driver.

---

### Post by hecter on 2008-03-28
Thanks a lot :D Both of you, turns out I was putting in dpkg -reconfigure rather than dpkg-reconfigure :roll:

---

