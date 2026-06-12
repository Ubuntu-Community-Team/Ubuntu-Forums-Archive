---
title: "Intel 537 driver not loading on reboot.. why?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by steve457 on 2008-03-24
I downloaded the latest version of the Intel 537 driver for Gutsy Gibbon and it installed no problem with no glitches whatsoever.  I then tested the modem using NCID (for callerID functions) and it worked great!  The problem I am having is that the drivers do not seem to load when I reboot the machine, and the modem cannot be found by other programs such as ncidd.   I checked and I do see the existence of /dev/537 and a link to that from /dev/modem.  I also notice some symbolic links in various rcX.d directories which point to /etc/init.d/537_boot.  If i do a reinstall of the driver (by running .deb file), then the driver gets reloaded and works again.  

Does anyone know why the driver does not seem to load after rebooting?  Is there anything I can check for or modify to fix the issue?

thanks.

---

### Post by steve457 on 2008-03-24
After further digging, it appears that maybe the intel driver did load, but for some reason is not working after reboot? 

% lsmod | grep 537
```
Intel537             4148880  0
```

if I look in /var/log/kern.log I could see messages stating that the driver loaded, so it would appear that the driver loaded succesfully.  If I then run the following command for the NCID program, however the modem is not found.

%ncidd -Dv3
```
Started: 03/24/2008 14:36
Server: ncidd 0.70
ncidd logfile: /var/log/ncidd.log
Processed config file: /etc/ncid/ncidd.conf
Configured to send 'cidlog' to clients.
Configured to send 'cidinfo' to clients.
Processed alias file: /etc/ncid/ncidd.alias
Verbose level: 3
Telephone Line Identifier: -
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile: /var/log/ciddata.log
TTY port opened: /dev/modem
TTY port speed: 19200
TTY lock file: /var/lock/LCK..modem
TTY port control signals enabled
No Modem Response
Try 1 to init modem: return = 2.
AT
Try 2 to init modem: return = 2.
 Z S0=0 E1 V1 Q0
Try 3 to init modem: return = 2.
No Modem Response
Try 4 to init modem: return = 2.
AT
Try 5 to init modem: return = 2.
 Z S0=0 E1 V1 Q0
Try 6 to init modem: return = 2.
No modem found: /dev/modem
Terminated:  03/24/2008 14:36
```

$ ls -l /dev/modem
```
lrwxrwxrwx 1 root root 8 2008-03-23 21:31 /dev/modem -> /dev/537
```

If I reinstall driver using .deb package then the modem can be found with the above command.  Any ideas what may be going on?

---

