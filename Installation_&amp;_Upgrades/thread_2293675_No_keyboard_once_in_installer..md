---
title: "No keyboard once in installer."
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by sayre on 2015-09-06
Hi Everyone,

I am trying to install ubuntu server 14.04.3 LTS however when I get to the install guide screen I get no Wireless USB keyboard support. 

It works at this screen:
[ATTACH=CONFIG]264283[/ATTACH]

Then I choose install and go to this screen and the keyboard will not work:
[ATTACH=CONFIG]264284[/ATTACH]


USB legacy is already enabled. I can't find anything else in the bios that would fix this issue. I have also tried booting the install with the keyboard mapping to english but still didn't work.  I don't have a wired one and really need to get this installed.

Thanks


Details:
Gigabyte H77N-WIFI motherboard
Logitech K360 wireless keyboard

---

### Post by QIII on 2015-09-06
Hello!

Do you have your receiver in a USB 2.0 port or a USB 3.0 port?

Many Gigabyte boards display an oddity with the USB 3.0 ports until a setting is changed.

Try doing your installation with your receiver in a USB 2.0 port and let us know how that goes.

---

### Post by sayre on 2015-09-06
Thanks for your reply, I tried every single usb port (2.0 and 3.0) and none worked. I ended up trying an older version 12.04 and it's working with my keyboard just fine. Must be the distro for some reason..

---

### Post by VMC on 2015-09-06
see if any errors message appear in the logs:
```
grep -i keyboard /var/log/syslog
and
grep -i keyboard /var/log/kern.log
```

edit: I just realized that 1) your using an install disk, 2) those logs will disappear on re-boot.

---

