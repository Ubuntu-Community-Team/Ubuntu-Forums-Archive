---
title: "Ubuntu 12.10 systematically ask for admin password when shutting down"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by SanA333 on 2013-03-27
I have recently upgraded to Ubuntu 12.10 from 12.04. Every time I want to reboot or shut down Ubuntu asks for the root password. It even happens if I shut down just after restarting (which means there are no admin application running).

I have tried to see if several sessions were opened, using [COLOR=#0000ff][FONT=courier new]ck-list-sessions[/FONT][/COLOR]. Here what I see: 

```
Session2:
    unix-user = '1000'
    realname = XXXXXXXXXX
    seat = 'Seat1'
    session-type = 'x11'
    active = TRUE
    x11-display = ':0'
    x11-display-device = '/dev/tty7'
    display-device = '/dev/tty7'
    remote-host-name = ''
    is-local = TRUE
    on-since = '2013-03-26T20:29:30.297477Z'
    login-session-id = '4294967295'
```

It seems there is only one session, although it says 'Session2' 

Any idea how to sort this out?

Cheers

---

