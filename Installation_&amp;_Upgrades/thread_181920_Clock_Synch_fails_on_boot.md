---
title: "Clock Synch fails on boot"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by Out The Window on 2006-05-25
On Ubuntu/XP (new install of Ubuntu), when I boot to Ubuntu, the GNU won't start - only text. Clock synch is the only module that fails. Is this referring to the sys clock? Os clock? In setup, I set it to local time instead of GMT (as suggested for dual boot), what gives? :-k 

Presario sr1820nx Athlon 64 3400+, 704MB PC3200, 160G Seagate(XP), 80G Seagate (Linux).

---

### Post by simonn on 2006-05-25
Is your inernet connection up when you boot?

Your PC is trying to synch to an ntp server which requires that it has internet access.

---

### Post by nalmeth on 2006-05-25
did you just do a server install? 
as previously asked, do you have an internet connection?

a server install will give you only a virtual terminal

try typing 
sudo apt-get update (exclude this if you have no internet connection)
sudo apt-get install ubuntu-desktop

---

### Post by Out The Window on 2006-05-25
Yes, I have internet connection. In fact I rebooted to windows :-?  and joined this forum to learn more about it.  The site that linux boot tries to connect to is: ntb.ubuntulinux.org. Thanx for the suggestions, will give them a try...

---

### Post by Out The Window on 2006-05-25
Also, no i did not do a server install.

---

