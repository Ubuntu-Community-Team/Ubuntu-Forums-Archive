---
title: "Wubi boot failure after kernel upgrade"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by Kurofune on 2010-11-27
I've been running Ubuntu 10.04 AMD64 on our home theater PC through a wubi installation. Yesterday the system update installed a new kernel and today there is a problem booting the computer so I'm reluctantly using Windoze to type this.

Sadly there isn't much information: the computer has always booted fine before the kernel update. When I select Ubuntu in the boot menu the screen goes black and the computer restarts. No error messages, no GRUB menu, just a blank screen before restart.

Computer: Dell Hybrid 140G, Intel Core 2 Duo T5800, 4GB RAM

---

### Post by Rubi1200 on 2010-11-27
Hi and welcome to the forums :)

See here for a description of the problem and possible solutions:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

If you have any questions, feel free to ask first.

---

### Post by GottaGoMedia on 2010-11-27
[http://ubuntuforums.org/showthread.php?t=1631945](http://ubuntuforums.org/showthread.php?t=1631945)

---

### Post by Kurofune on 2010-11-27
The post from Rubi1200 was the solution to this problem. This requires nominal bash/terminal skills.

As a note to anyone trying the same thing: for my wubi install the disk was most easily located under the places menu as a disk called OS. This made the first few mounting steps of the process unnecessary. After that clearing the grub.cfg file did the trick right away. Also, I wasn't seeing any errors before the reboot but that may be because my screen takes a while to turn on at first (It's a large LCD TV connected through HDMI).

This is why Ubuntu has had success: an active and helpful community. Thanks guys.

---

### Post by Rubi1200 on 2010-11-27
You are more than welcome :)

The real credit goes to forum member bcbc who has worked tirelessly to help users with Wubi installs.

---

