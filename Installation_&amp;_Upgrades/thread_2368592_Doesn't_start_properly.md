---
title: "Doesn't start properly"
date: 2017-08-12
forum: Installation &amp; Upgrades
---

### Post by Alexboy on 2017-08-12
I've restarted my PC once using a physical button and since then, Ubuntu doesn't load properly.
I've reinstalled Ubuntu and even switched to 17.04, but it doesn't load at all.
The funny thing is, Live USB gets it to load properly, but once Ubuntu is installed, it doesn't load.
I've copied the info from "systemctl -xb". 
After the GRUB, the logo appears, but after a second it enters the "Emergency mode".
Later on, I've found a way to bypass black screen by typing "mount -a", then "mount" and "exit" in the end.
Here is the log:
[http://paste.ubuntu.com/25299222/](http://paste.ubuntu.com/25299222/)
How do I fix it?

---

### Post by Autodave on 2017-08-13
I am NOT an expert at reading those logs, but it appears to me that you may have a RAM problem. I would suggest running a memory test and see what that reports. You can do this from the live USB stick.

---

