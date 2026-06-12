---
title: "64 bit installs but 32 bit wont"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by nwFpXmk on 2013-09-05
Hello I am trying to install kubuntu 13.04 on my Alienware Aurora R3 and I have an odd problem. I can install the 64 bit kubuntu 13.04 no problem but I wanted 32 bit for various reasons but when I tried to boot the 32 bit, it stays on the loading screen then a command line thing pops up saying "udevd timeout" and I left it for 10 minutes and 3 more of them popped up and then nothing else happened. The only way out was to power down. Could someone tell me how to fix this?

---

### Post by tgalati4 on 2013-09-05
*[udevd]("http://http://manpages.ubuntu.com/manpages/hardy/man7/udev.7.html")* is a daemon (background process) for detecting your hardware.  It's not happy about something.  Boot a Live DVD or USB session and look for log files in /var/log--assuming it got that far in the installation.

Otherwise, pull everything out of the machine, except one hard disk, and try again.  Pay attention to any messages during the install.

Why can't you use 64-bit?

---

### Post by varunendra on 2013-09-06
Is EFI enabled in its BIOS/setup ?

I'm not aware of exactly what kind of error it'll give, but as far as I know, you can't boot 32 bit in EFI mode. Change it to 'legacy' (or BIOS) mode if it is enabled, then try again.

---

