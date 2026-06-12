---
title: "Jaunty hang before logging"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dino99 on 2008-11-29
hi all,

when i start Jaunty, the boot process first powered down my ethernet port !!! and then, of course, it hang to find eth0 during 30 seconds.
Without doing anything, port is powered up and the boot process can end normally.
It's an upgrade from Hardy, without compiz or network manager, system up to date. Can't find any errors in log to explain that trouble: if someone has an idea, he's welcome

---

### Post by ktp on 2008-11-29
Do you use /etc/network/interfaces to config your network card?  If you do, then the new NM in interpid did not honor interfaces file so something was "added" to read and honor the file to config the network.  But when I had interfaces file, boot would hang for while configuring the newtork.  I removed interfaces, even thought now I can't configure bridge network, and boot was fast/normal.

---

