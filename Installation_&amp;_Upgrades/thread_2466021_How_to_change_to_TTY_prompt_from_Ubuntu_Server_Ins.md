---
title: "How to change to TTY prompt from Ubuntu Server Installer GUI?"
date: 2021-08-17
forum: Installation &amp; Upgrades
---

### Post by fixapc on 2021-08-17
How to change to TTY prompt from Ubuntu Server Installer GUI?

I believe i have done this before but i need to know how to do this to do a custom btrfs install first before installing the OS.

---

### Post by TheFu on 2021-08-18
Choose a different TTY (or ptty) by using <cntl><alt>-F1 thru F8

I use this just after starting a fresh install, but when I want the target storage to be very specific types and sizes that are 1000x harder to setup in the installation GUI.  Of course, inside the install GUI, I still have to point it at the (now) existing partitions for specific purposes.  In 20.04 server, I've been offered during the install to download an use a new installer. I always accept that choice.

If you want a better answer, provide the Ubuntu Release, since different releases have different installers and different capabilities.

---

### Post by MAFoElffen on 2021-08-18
In the Ubuntu Server 20.04 "Live Installer" environment, (which you said you are in), to get to a console, press <Alt><F2>

---

