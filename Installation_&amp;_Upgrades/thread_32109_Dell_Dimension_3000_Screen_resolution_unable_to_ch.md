---
title: "Dell Dimension 3000 Screen resolution unable to change"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by gpapam on 2005-05-06
Hi there all,
              I made an installation yesterday of Hoary 5.04 on my Dell Dimension 3000 desktop but it is unable to apply my correct screen resolution although it is detected and is first in resolution lists in '/etc/X11/xorg.conf'

I changed the memory of the graphic card from 1Mb to 8Mb with no results. I ran the 'gft'  and put the result in 'Monitor' section plus the conservative things of course including reconfiguration of the xserver using dpkgconfig, etc. 

It still sucks...  :mad: 
Any more ideas??
Thanks a lot.

-gp

---

### Post by wh0rd on 2005-08-07
I had the same issue.

Well here's my solution to my 3000 Dell Dimension with 15" LCD Monitor. From just being able to set resolution to 640x480, I can now change my resolution to 1024x768.

In terminal type: gedit /etc/X11/xorg.conf

In /etc/X11/xorg.conf under the line Option “DPMS” (use the find option) just add:

HorizSync 28-49
VertRefresh 43-72

Save and reboot your system.

Here's where i found the post for the solution:
[http://fluideye.com/blog/2005/06/28...-in-resolution/](http://fluideye.com/blog/2005/06/28...-in-resolution/) 

This should definitely work. Happy Linuxing!

---

### Post by kevinat0r on 2005-08-25
Sorry to bump this, but I'm having the exact problem, I've been working all day with an experienced Debian user and we haven't been able to fix it. I tried what you suggested, still no luck.

It would be nice if you could IM me, MSN [email]nowarranty@gmail.com[/email], AIM K3v1nator

---

