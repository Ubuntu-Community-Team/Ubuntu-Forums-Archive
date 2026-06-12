---
title: "Libreoffice documents with db connection won't start"
date: 2019-03-05
forum: Installation &amp; Upgrades
---

### Post by angalan on 2019-03-05
Hi everybody,

after switching from Lubuntu 18.4 to 18.10 all my documents that have a connection to a database need an awful lot of time to start. After they eventually start, if I try to access the database Libreoffice  crashes.
I'm speaking of serial letters connected to a Calc sheet with addresses. Simple documents without db connection work perfectly.
The Calc sheet with the addresses has a lot of macros. It needs about 5 Minutes min. to load. When it's loaded it works, even if slower than before the switch.

I googled around and tried different approches:
[LIST]
[*]created a new user profile for Libreoffice 
[*]checked the jre, removed and reinstalled it 
[*]purged and reinstalled Libreoffice 
[*]installed Libreoffice 6.2.0.3 
[/LIST]

Absolutely nothing changed.

I appreciate any help!

Thank you very much

---

### Post by angalan on 2019-03-06
After many more hours of searching I found out that the document that served as DB is broken. I didn't find out exactly what's problem, but opening a new one and copying the data - which was not easy because it was always crashing, than replaced the old one with the new one and everythink worked again.

---

