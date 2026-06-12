---
title: "Machine with 11.10 won't reboot consistently"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by KeithLM on 2011-10-25
Ever since upgrading to 11.10 from 11.04 I have had problems rebooting.  Most times after rebooting via shutdown -r or from the gui the computer goes through the bios sequence but stops before grub comes up.  Pressing ctrl-alt-del gets it to reboot and then grub comes up, but will not execute the default option, it just sits there and doesn't prompt me to do anything.  I hit enter then it carries on.  

I'd say about 9 times out of 10 it goes through this process.  Only rarely have I seen it reboot correctly.  Also after a reboot failure samba doesn't start automatically. 

I found the following messages logged multiple times:
```

Oct 25 21:05:09 Holly acpid: waiting for events: event logging is off
Oct 25 21:05:09 Holly cron[1212]: (CRON) INFO (pidfile fd = 3)
Oct 25 21:05:09 Holly kernel: [   20.346593] init: failsafe main process (1076) killed by TERM signal
Oct 25 21:05:09 Holly kernel: [   20.347265] init: smbd main process (1150) killed by ABRT signal
Oct 25 21:05:09 Holly kernel: [   20.347285] init: smbd main process ended, respawning
Oct 25 21:05:09 Holly kernel: [   20.347440] init: apport pre-start process (1199) terminated with status 1
``` 

I can also see that NetworkManager and dhclient starting after ntpd which means ntpd fails to find the ntp pools and this all happens after the smbd errors. Although ntdp does seem to start again later on. 

Is there someway to reorder the startup processes?  And why doesn't this thing boot correctly?

---

