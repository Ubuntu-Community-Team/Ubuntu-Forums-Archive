---
title: "/usr/sbin/ntpd process in complain mode"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by itsjareds on 2009-09-30
When I boot up Ubuntu, I get a warning that flashes somewhat quickly, so I don't get a chance to read it. I didn't catch much of it, but it was about apparmor and /usr/sbin/ntpd in complain mode. I ran 'aa-status' and got: 

```
$ sudo aa-status
apparmor module is loaded.
11 profiles are loaded.
10 profiles are in enforce mode.
   /usr/lib/connman/scripts/dhclient-script
   /usr/share/gdm/guest-session/Xsession
   /usr/bin/evince-previewer
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /usr/bin/evince-thumbnailer
   /usr/bin/evince
   /sbin/dhclient3
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
1 profiles are in complain mode.
   /usr/sbin/ntpd
3 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (2270) 
   /usr/sbin/cupsd (1683) 
1 processes are in complain mode.
   /usr/sbin/ntpd (2627) 
0 processes are unconfined but have a profile defined.
```

How do I fix the /usr/sbin/ntpd complain mode warning? It doesn't keep me from booting into Ubuntu but it still takes me out of the splash screen.

---

### Post by itsjareds on 2009-10-01
bumparoo

---

### Post by Gourgi on 2009-10-01
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles)

> 
NTP (ntpd): A complain-mode only profile was provided in the apparmor-profiles package in Ubuntu 9.04 and earlier 


it is supposed to be that way by default.

---

### Post by itsjareds on 2009-10-02
Ok, sounds great, so is there currently a way to ignore this warning at boot so I can continue through the splash screen?

---

