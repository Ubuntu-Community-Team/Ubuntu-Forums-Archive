---
title: "Session management error"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by janboen on 2005-07-24
Hello there,

I'm trying to get MythTV and what goes with to work on my newly installed Ubuntu system.

This is an error which has already popped up a couple of times:
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed

This is an example of when it happens:
root@ubuntu:/home/jan # mythfilldatabase --manual
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
###
### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
----------------- Start of XMLTV output -----------------
nice: tv_grab_nl: Onbekend bestand of map
------------------ End of XMLTV output ------------------
Error in 1:1: unexpected end of file
Updating icons for sourceid: 1
Updated programs: 0  Unchanged programs: 0
Failed to fetch some program info
root@ubuntu:/home/jan #
root@ubuntu:/home/jan #
root@ubuntu:/home/jan #
root@ubuntu:/home/jan # Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
bash: Session: command not found
root@ubuntu:/home/jan #

Any idea how I can fix it?

Thanks


Jan

---

### Post by djSHY on 2005-07-28
i have the same problem :(

---

### Post by Nexu on 2006-03-02
install xmltv-util package \o/

(just replying if anyone is looking for this again)

---

