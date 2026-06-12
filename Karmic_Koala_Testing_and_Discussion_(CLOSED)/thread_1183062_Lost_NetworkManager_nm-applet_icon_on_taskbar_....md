---
title: "Lost NetworkManager nm-applet icon on taskbar ..."
date: 2009-06-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-06-09
All of the sudden I've noticed that there is no NM icon on taskbar (or whatever is the name of upper bar). OK, I've resorted to turning it off in StartUp and generating interfaces and resolv.conf by myself but I'm interested in the way to get it back. Yes, I do not think much of NM on desktop machine without the wireless but it bugs me what happened and how to remedy that. Thank You for any idea ... :)
(Karmic with all updates and 2.6.30.999(daily), grub2)

---

### Post by afv on 2009-06-10
Hmm, doesn't "nm-applet --sm-disable" open it?

---

### Post by autocrosser on 2009-06-10
Interesting--I have noticed the same thing & no, nm-applet --sm-disable will just advise that the service is already started......

---

### Post by zika on 2009-06-10
What a beginners mistake I made. Somehow I lost Notification area ... :) I reinstated it and everything is OK, except I do not have NM anymore (because I removed it from the loop) like at the very start of 8.10 ... when it was impossible to use it. I do not care and do not plano to put it back. I like networking more without it ... :) (No, I did not uninstall it and I do not plan to, I it from boot with sysv-rc-conf and from StartUpApplications ... ) Sorry for false alarm ...

---

