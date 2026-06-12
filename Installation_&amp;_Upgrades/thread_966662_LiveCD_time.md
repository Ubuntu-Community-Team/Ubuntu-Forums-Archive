---
title: "LiveCD time"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by nick_white on 2008-11-01
Why doesn't the LiveCD read the system time (from the CMOS)? It shows the time with 2 hours backwards (if now is 10:00 it shows 8:00).

Ubuntu 8.10 release

---

### Post by MoebusNet on 2008-11-01
It is my belief that the LiveCD gets its time information from the Internet (from a time-server or some such). The default time zone is set to UCT (Universal Coordinate Time; feel free to correct me if I used the wrong term). This used to be known as Greenwich Mean Time, which is the time in Greenwich, England.

If you want to change your time zone, you can click the "Day, Date, Time" button in the upper right hand corner of the desktop (Ubuntu 8.04) which will drop a menu containing a calendar and a "Locations" button. Click the "Locations" button and a map of the world will drop down which should allow you to select a city in your time zone to set the time zone.

If you install, there will be a similar process during install to set your time zone.

---

