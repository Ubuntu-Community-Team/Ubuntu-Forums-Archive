---
title: "ubuntu 11.04 wubi installation problem"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by sksravan960 on 2011-05-20
i have downloaded ubuntu 11.04(ubuntu-11.04-server-i386) and wubi also.When i start wubi it tries to download iso again.I put the two in same folder but it didn't worked .
When i created a usb installer and tried to install it,it shows that kernel image is not found.what should i do next?

---

### Post by linuxinstalledfromhdd on 2011-05-20
That sounds like a Wubi issue. 

Honestly, I recommend that people try to use a old fashioned cd to install Ubuntu. Wubi may work for some people. 

This page will help you out:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

And use the above do-to list after you get it installed. It takes some time to get through everything, but afterwards you will have a stable system.

---

### Post by Rubi1200 on 2011-05-20
> **sksravan960 said:**
> i have downloaded ubuntu 11.04(ubuntu-11.04-server-i386) and wubi also.When i start wubi it tries to download iso again.I put the two in same folder but it didn't worked .
When i created a usb installer and tried to install it,it shows that kernel image is not found.what should i do next?
Hi and welcome to the forums :-)

Make sure the wubi.exe and iso match:
> download both Wubi.exe and the required Desktop ISO from the same location (the release has to match): 

[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
[/LIST]
Copy both files into the same folder on the machine...and run the Wubi executable. 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

