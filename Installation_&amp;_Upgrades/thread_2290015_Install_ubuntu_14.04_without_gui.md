---
title: "Install ubuntu 14.04 without gui"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by avdija on 2015-08-08
Hello,

I have an old eeepc 701 and I want to install command line only Ubuntu 14.04 on it. Previous LTS had an "Alternative CD" that could be used to install command line only system, but that is not available on 14.04. Is there any other method that I can use? Installing full version and then removing gui is not an option.

---

### Post by Bucky Ball on 2015-08-08
Welcome. You want the minimal install. You need to be able to get online with a cable, though, so not sure if your machine has the socket.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
(You'll find 14.04 LTS here)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you get a tasksel screen, don't choose a profile, just continue (you'll know what I mean if you get one), and when finished and rebooted you will end up at a login cursor. Login and that's it. Whatever you install is up to you. You have the Ubuntu base kernel running. :)

---

### Post by avdija on 2015-08-08
i have tried MinimalCD but it will not boot at all on this eeepc 701

---

### Post by Bucky Ball on 2015-08-08
What's it doing when you try?

---

### Post by avdija on 2015-08-08
it boot to "Installer boot menu" and hangs, if I install either "Install" or "Command-line install". I am using 32 bit version.

---

### Post by avdija on 2015-08-08
I have tried "expert install mode" and it seems to be working :)

---

### Post by Bucky Ball on 2015-08-08
Excellent. :)

Guess you know where you're going with it, but once installed you can install whatever else with 'sudo apt-get install <app>' where <app> is the name of the software to be installed. Good luck.

---

