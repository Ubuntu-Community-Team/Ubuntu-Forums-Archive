---
title: "Upgrading to 9.10 makes all services FAIL on startup"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by stealthguitar on 2010-01-09
I upgraded from 9.04 to 9.10.  SSH, samba, LAMP server, etc etc etc are now failing to start when the os boots. I can start all of these services manually  but is a bit of an annoyance.  Maybe something simple but am not sure where to look to fix this. 
Thank you.

---

### Post by stealthguitar on 2010-01-11
Should I try reinstalling the packages? I'd prefer not to :(

---

### Post by SecretCode on 2010-01-11
Is this a server install?

What do the logs show, esp syslog, messages, dmesg, mysql.log, samba?

---

### Post by stealthguitar on 2010-01-12
Yes it is the server edition.  

I looked through syslog, messages, and dmsg logs you mentioned but I'm not sure what to look for.  The MYSQL log file was empty and I'm not sure I found the correct samba log either.  I'm sure that's not at all  helpful in troubleshooting this but I would like to learn more instead of reformatting again.

---

### Post by SecretCode on 2010-01-12
Maybe it's not an error preventing their startup - maybe it's something in initialisation that didn't migrate properly. I have a vague idea that 9.10 introduced new init directories and service handling.

Have a dig around your /etc/init* files and directories - and see if *man init* and *man service* give you any clues.

---

