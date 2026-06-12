---
title: "E: Unable to locate package exotic-theme problem installing theme."
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by pawan98 on 2010-10-25
Hi, I use 10.10 and when I try to install the theme this is what comes up:

pawan@ubuntu:~$ sudo apt-get install exotic-theme
[sudo] password for pawan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package exotic-theme

Please help. I don't know what the problem is.

---

### Post by sikander3786 on 2010-10-25
<snip>

Sorry. Wrong post.

---

### Post by gmargo on 2010-10-25
Google tells me that the exotic-theme is part of the Bisigi Project.

You'll need to add some **ppa** information before you can install the **exotic-theme** package.

See:
[http://www.bisigi-project.org/?page_id=8&lang=en](http://www.bisigi-project.org/?page_id=8&lang=en)    (install instructions here)
[http://www.bisigi-project.org/?lang=en](http://www.bisigi-project.org/?lang=en)
[http://ubuntu-tweak.com/app/exotic-theme/](http://ubuntu-tweak.com/app/exotic-theme/)

(Ignore this if you're thinking of an even more exotic theme!)

---

### Post by pawan98 on 2010-10-25
Thanks gmargo, that helped it, and it worked :D

---

### Post by sikander3786 on 2010-10-25
It seems like you are using apt-get simultaneously with some other package manager like Synaptic or Software Center. Quit the other one and try again. If no other is running, reboot and try again.

Regarding the issue with exotic-theme installation, pay attention to gmargo's post above. But that will be possible only after you successfully update using

```
sudo apt-get update
```

and don't see the errors at the end. This one

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by pawan98 on 2010-10-25
Yep, Gmargos way worked easily, now I'm using the theme as I'm typing now.

---

