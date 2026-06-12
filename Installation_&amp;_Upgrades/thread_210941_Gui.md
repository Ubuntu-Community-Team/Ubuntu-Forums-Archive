---
title: "Gui"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by jayser on 2006-07-07
Hello all,

I just installed the server version of 6.06 and an not very savy on the terminal. I installed this because I would like to test out the FTP server part as well as Apache.

How can I get into/install a GUI on this? I still need to apply IP info and all that good stuff before i test it out.
Thanks,
Jayser

---

### Post by aysiu on 2006-07-07
Do you want a full GUI or just a minimal one?

---

### Post by jayser on 2006-07-07
maybe just a full one. I am very new to Linux and just want to view it all.

Is there a big difference though?
Thanks,

---

### Post by aysiu on 2006-07-07
Sometimes people want a minimalist GUI because they have 64 MB or less of RAM, and their systems can't handle a full GUI. Sometimes older computers (in addition to having little RAM) don't have that much hard drive space, too. I have three GUIs installed, and my whole Ubuntu installation is only 3.5 GB, but for some older computers 3.5 GB of hard drive space is just about all there is!

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
``` should do the trick.

---

