---
title: "nm-applet not showing up in tray (Intrepid)"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Prendi on 2008-10-28
Hi,

I installed the Intrepid RC. Most things work fine, but from the start the nm-applet did not show up in the notification area. Does anybody know a fix for this? 

I got an active Notification Area panel item (Pidgin shows up there) and according to "ps aufx | grep applet", the "nm-applet --sm-disable" is started. But even killing it ("killall nm-applet") and starting it from the console does not help. It just sits at the console, not terminating but also not giving any error messages. I strace'd it and the final lines in the trace are
```
read(14, 0x84d51b0, 2048)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x81985d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1225181021, 14873}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=9, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN}, {fd=4, events=POLLIN}, {fd=14, events=POLLIN}], 9, 0) = 0
read(3, 0x81985d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1225181021, 15673}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=9, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN}, {fd=4, events=POLLIN}, {fd=14, events=POLLIN}], 9, 0) = 0
read(3, 0x81985d4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1225181021, 16206}, NULL) = 0
poll(

```


It worked in the final alpha of Intrepid, but disappeared when I upgraded it for the first time.

I got a static IP, could that have anything to do with it? I need that static IP for wired networks, but need the nm-applet to configure wireless and vpn connections.

---

