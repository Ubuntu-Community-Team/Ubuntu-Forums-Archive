---
title: "No PXEBoot After upgrade from 12.10 to 13.10"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2014-08-02
I figured i go ahead and perform the upgrade from 12.10 to 13.10,Once i was completed and a checked for errors , i see the PXEboot no longer functions.  The client receive a DHCP address  and then hand on  we the error "  PXE=E32: TFTP open timeout "I have manually restarted the service and checked to ensure the TFTPD  service is up. xbmc@PlexOne:~$ sudo service tftpd-hpa restart tftpd-hpa stop/waitingtftpd-hpa start/runningxbmc@PlexOne:~$ ps aux | grep tftpxbmc     12454  0.0  0.0   9452   940 pts/0    S+   18:50   0:00 grep --color=auto tftpxbmc@PlexOne:~$SYSLOG (Attached)  reports one error ([https://www.dropbox.com/s/a24cmlh24sx039x/syslog)Aug](https://www.dropbox.com/s/a24cmlh24sx039x/syslog)Aug) 2 18:50:48 plexone in.tftpd[12517]: Address :: is not in address family AF_INCCan anyone provide info on how to fix?

---

### Post by Frogs Hair on 2014-08-02
Closed Duplicate

---

