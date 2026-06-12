---
title: "Dell Latitude D610: After 14.04.1 install, no GUI."
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by john184 on 2014-09-27
Hello,

Novice user.
I have tried to install Xubuntu 14.04.1 on an old Dell Latitude D610
The USB drive install kept hanging part-way through installation, so I abandoned it.
I tried the MinimalCD install, I chose Xubuntu Desktop and install seemed to go fine.
But when I now boot, I get no GUI, just Command line "Ubuntu 14.04.1 LTS ubuntuclare tty1"
I can login ok, but I don't know what's happened or how to proceed

thanks,
John

---

### Post by mörgæs on 2014-09-28
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by john184 on 2014-09-28
Thanks for reply. I already reinstalled, unchecking option for 3rd party downloads and the install seems to have run fine. I,m back in GUI. Now researching lack of wireless...

---

### Post by mörgæs on 2014-09-28
Good, chances are you have a Broadcom 431x, so I would begin here:
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by john184 on 2014-09-28
indeed. i suspect that was the same issue spoiling the install. i'm now sorted. thanks again

---

### Post by mörgæs on 2014-09-28
Good, please mark the thread solved using 'thread tools'.

---

