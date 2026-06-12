---
title: "ubuntu 10.04 keyboard not working"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by luapnor on 2010-09-12
hello all,

just did an upgrade from 9.10 to 10.04 and now my dell keyboard does not work anymore. when i do a safemode startup there s no problem. so now i am ticking this thread via the onboard app. grr..

did some googling already but could not find the answer. 
anyone has an idea?

---

### Post by clrg on 2010-09-12
Are there any log entries in /var/log/messages that  could shed some light on it? Maybe something saying it doesn't recognize a device?

Have you tried disconnecting and reconnecting the keyboard? Also, do the lights (NumLock, CapsLock, ScrollLock) light up when you press those keys?

---

### Post by luapnor on 2010-09-12
hi, thanks for your reaction


> rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="861" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

?thats the content of var/log/messages

there is no light on any key...

this is the keyboard part of /etc/default/console-setup

> XKBMODEL="SKIP"
XKBLAYOUT="U.S. English"
XKBVARIANT=""
XKBOPTIONS="lv3:ralt_switch,grp:alts_toggle"

---

