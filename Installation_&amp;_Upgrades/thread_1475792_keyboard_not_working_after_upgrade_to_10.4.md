---
title: "keyboard not working after upgrade to 10.4"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Marcel Diallo on 2010-05-07
After upgrading to 10.4 from 9.8, my keyboard wouldn't work on the startup menu, I then went to the console and it worked perfectly. I'm new to Linux so don't know a lot about it. I also tried to reinstall it using 
> sudo dpkg-reconfigure -phigh -abut it always stops and return "This page is not dpkg-info anymore, but GNU install info
See the main page for ginstall-info for command line arguments
install-info:No dir file specified; try --help for more information."

---

### Post by dino99 on 2010-05-07
sudo apt-get update
sudo apt-get install -f
sudp dpkg --configure -a

---

### Post by kio_http on 2010-05-07
In terminal

```
sudo dpkg-reconfigure xserver-sorg
```

This will give you some options to set keyboard settings.

---

### Post by dino99 on 2010-05-07
sudo dpkg-reconfigure xserver-xorg

---

### Post by spirytusick on 2010-05-07
I have exactly the same problem. I have a dual monitor setup with two separate screens (LCD Monitor and a HD TV) configured through the xorg.conf. The config file worked fine with auto configuration of input devices on the fly in 9.10. From what I can gather from the logs, the evdev does not load any drivers and the autoconfiguration does not happen. Booting from livecd, everything works fine.

---

### Post by spirytusick on 2010-05-08
Ok, I have managed to trace the problem and solve the issue.
It my case it was caused by a custom udev rule in /etc/udev/rules.d/60-persistent-input.rules which overrided the settings from /lib/udev/rules.d/60-persistent-input.rules After I changed the the order in which those files were processed the problem went away.

Silly little thing.

---

