---
title: "Problems with Xserver while upgrading to 6.06"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by girionis on 2006-06-15
Hello, I tried to upgrade from 5.10 to 6.06 and 14 minutes before the upgrade was finished I was presented with an error message that was telling me to report a bug. Then the upgrade process exited. I tried to report the bug but I wasn't able to open any firefox, or in fact any other programme. I rebooted my computer and now it cannot load the xserver. I followed all the instructions of the sticky thread about xserver but to no avail. When I try to reconfigure xserver by doing 

dpkg-reconfigure xserver-xorg

I get the error message that xserver is broken. I cannot do an apt-get upgrade because my internet connection does not work and I do not know how to configure it from the command line.

Any help on configuring the internet connection or how to solve the xserver issue is appreciated.

Regards

---

### Post by Kibbo on 2006-06-15
Getting your internet connection to work is probably the first step.
What's the output of ifconfig from the command line?
What's your network setup like?  Are you wired or wireless?  Using a router? DSL or Cable or Dial up?

---

### Post by girionis on 2006-06-16
Ok, I downloaded xserver from windows, burned it on a cd, restarted into Ubuntu and then I copied to my hard drive. Then I installed it and xserver loads up properly again. Now I have another problem, I do not have sound at all, I will look into it. Meanwhile any ideas are welcome (sorry if I get off topic).

Regards

Panos

---

