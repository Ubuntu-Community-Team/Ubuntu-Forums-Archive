---
title: "problem with personal repository"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by kaviresabz on 2010-09-12
hello everyone
when i update the system that did not connect the Internet with my personal repository and restart my computer, i saw the below error!
------------------------
[COLOR=DarkRed]udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
   -Boot args (cat /proc/cmdline)
      -Check rootdelay= (did the system wait long enough?)
      -Check root= (did the system wait for the right device?)
   -Missing modules (cat /proc/midules; ls /dev)
ALERT! /dev/disk/by-uuid/50277f44-ee1f-4f33-aa75-823834057214 does not exist. 
Dropping to a shell![/COLOR]
------------------------ 
i use Ubuntu 10.4.
how can i solve this problem.
i do not want to setup Ubuntu again.
note that i can not connect to the Internet.

---

### Post by ronnielsen1 on 2010-09-12
> [COLOR=DarkRed]ALERT! /div/disk/by-uuid/50277f44-ee1f-4f33-aa75-823834057214 does not exist. [/COLOR]

Shouldn't that be /dev/disk?

---

### Post by kaviresabz on 2010-09-12
thank for your reply. yes you are right. but what i can do now.
is any way that i can rescue my system.

---

### Post by ronnielsen1 on 2010-09-12
I guess I need more info about what you're doing. If this is synaptic and the [COLOR=DarkRed]/dev/disk/by-uuid/50277f44-ee1f-4f33-aa75-823834057214 [/COLOR] is your repository because you're not connected to the internet, you should be able to [COLOR=Blue]gksudo gedit /etc/apt sources.list[/COLOR] in a terminal and fix your problem

---

