---
title: "Ntop webinterface not working."
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2013-01-04
Hey guys. 
I just installed a plugin for cacti called Ntop. 10.60.1.10:3000 should work when I want to access the web interface but it does not.

root@TLS-AMS-MON-10:~# netstat -ntlp | grep -i ntop
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      13580/ntop

It says it listens to port 3000?? Why cant I access the web interface?

Many thanks.

---

### Post by dino99 on 2013-01-04
inside gufw, check that port is opened

[https://help.ubuntu.com/community/Ntop](https://help.ubuntu.com/community/Ntop)

---

### Post by MocroNL on 2013-01-04
I have used that howto to install Ntop but no succes.
Adding port 3000 to iptables did not work. I have disabled the ubuntu firewall (ufw) but still no succes with accessing the web interface. And I tried Access from an external network with apache reverse proxy but still no succes....

---

### Post by dino99 on 2013-01-04
maybe you need to debug ntop: install ntop-dbg first

is ping giving a result ?

[http://manpages.ubuntu.com/manpages/hardy/man8/ntop.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/ntop.8.html)

---

### Post by MocroNL on 2013-01-07
tls@TLS-AMS-MON-10:~$ sudo ntop -K
Mon Jan  7 09:24:29 2013  NOTE: Interface merge enabled by default
Mon Jan  7 09:24:29 2013  Initializing gdbm databases
Mon Jan  7 09:24:29 2013  ntop will be started as user nobody
Mon Jan  7 09:24:29 2013  ntop v.4.0.3 (32 bit)
Mon Jan  7 09:24:29 2013  Configured on Jun 13 2011 12:51:23, built on Jun 13 20                                   11 12:51:47.
Mon Jan  7 09:24:29 2013  Copyright 1998-2010 by Luca Deri <deri@ntop.org>
Mon Jan  7 09:24:29 2013  Get the freshest ntop from [http://www.ntop.org/](http://www.ntop.org/)
Mon Jan  7 09:24:29 2013  NOTE: ntop is running from 'ntop'
Mon Jan  7 09:24:29 2013  NOTE: (but see warning on man page for the --instance                                    parameter)
Mon Jan  7 09:24:29 2013  NOTE: ntop libraries are in '/usr/lib/ntop'
Mon Jan  7 09:24:29 2013  Initializing ntop
Mon Jan  7 09:24:29 2013  Checking eth0 for additional devices
Mon Jan  7 09:24:29 2013  Resetting traffic statistics for device eth0
Mon Jan  7 09:24:29 2013  Initializing device eth0 (0)
Mon Jan  7 09:24:30 2013  DLT: Device 0 [eth0] is 1, mtu 1514, header 14
Mon Jan  7 09:24:30 2013  Initialized events [mask: 0][path: ]
Mon Jan  7 09:24:30 2013  Initializing gdbm databases
Mon Jan  7 09:24:30 2013  VENDOR: Loading MAC address table.
Mon Jan  7 09:24:30 2013  VENDOR: Checking for MAC address table file
Mon Jan  7 09:24:30 2013  VENDOR: File '/usr/share/ntop/specialMAC.txt' does not                                    need to be reloaded
Mon Jan  7 09:24:30 2013  VENDOR: ntop continues ok
Mon Jan  7 09:24:30 2013  VENDOR: Checking for MAC address table file
Mon Jan  7 09:24:30 2013  VENDOR: File '/usr/share/ntop/oui.txt' does not need t                                   o be reloaded
Mon Jan  7 09:24:30 2013  VENDOR: ntop continues ok
Mon Jan  7 09:24:30 2013  Fingerprint: Loading signature file
Mon Jan  7 09:24:30 2013  Fingerprint: Checking for Fingerprint file... file
Mon Jan  7 09:24:30 2013  Fingerprint: Loading file '/usr/share/ntop/etter.finge                                   r.os'
Mon Jan  7 09:24:30 2013  Fingerprint: ...loaded 1765 records
Mon Jan  7 09:24:30 2013  Database support not compiled into ntop
Mon Jan  7 09:24:30 2013  Initializing external applications
Mon Jan  7 09:24:30 2013  THREADMGMT[t3043265392]: SFP: Started thread for finge                                   rprinting
Mon Jan  7 09:24:30 2013  THREADMGMT[t3034872688]: SIH: Started thread for idle                                    hosts detection
Mon Jan  7 09:24:30 2013  THREADMGMT[t3034872688]: SIH: Idle host scan thread st                                   arting [p11271]
Mon Jan  7 09:24:30 2013  THREADMGMT[t3026479984]: DNSAR(1): Started thread for                                    DNS address resolution
Mon Jan  7 09:24:30 2013  THREADMGMT[t3043265392]: SFP: Fingerprint scan thread                                    starting [p11271]
Mon Jan  7 09:24:30 2013  THREADMGMT[t3018087280]: DNSAR(2): Started thread for                                    DNS address resolution
Mon Jan  7 09:24:30 2013  THREADMGMT[t3009694576]: DNSAR(3): Started thread for                                    DNS address resolution
Mon Jan  7 09:24:30 2013  Calling plugin start functions (if any)
Mon Jan  7 09:24:30 2013  **ERROR** GeoIP: unable to load file GeoLiteCity.dat
Mon Jan  7 09:24:30 2013  **ERROR** GeoIP: unable to load ASN file GeoIPASNum.da                                   t
Mon Jan  7 09:24:30 2013  THREADMGMT[t3018087280]: DNSAR(2): Address resolution                                    thread running
Mon Jan  7 09:24:30 2013  SSL is present but https is disabled: use -W <https po                                   rt> for enabling it
Mon Jan  7 09:24:30 2013  THREADMGMT[t3026479984]: DNSAR(1): Address resolution                                    thread running
Mon Jan  7 09:24:30 2013  INITWEB: Initializing web server
Mon Jan  7 09:24:30 2013  INITWEB: Initializing TCP/IP socket connections for we                                   b server
Mon Jan  7 09:24:30 2013  THREADMGMT[t3009694576]: DNSAR(3): Address resolution                                    thread running
Mon Jan  7 09:24:30 2013  **ERROR** INITWEB: binding problem - 'Address already                                    in use'(98)
Mon Jan  7 09:24:30 2013  Check if another instance of ntop is running
Mon Jan  7 09:24:30 2013  or if the current user (-u) can bind to the specified                                    port
Mon Jan  7 09:24:30 2013  **FATAL_ERROR** Binding problem, ntop shutting down...
Mon Jan  7 09:24:30 2013  CLEANUP[t3077630448]: ntop caught signal 2 [state=2]
Mon Jan  7 09:24:30 2013  ntop is now quitting...


This is what I get when Debugging. And how do you ping a port? Pinging the server IP address is no problem.

---

### Post by MocroNL on 2013-01-07
tls@TLS-AMS-MON-10:~$ sudo netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      8909/mysqld
tcp        0      0 127.0.0.1:9102          0.0.0.0:*               LISTEN      24925/bacula-fd
tcp        0      0 127.0.0.1:9103          0.0.0.0:*               LISTEN      24877/bacula-sd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      15082/apache2
tcp        0      0 10.60.1.10:53           0.0.0.0:*               LISTEN      28644/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      28644/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2052/sshd
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      3959/ntop
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      28644/named
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      28769/master
tcp6       0      0 :::53                   :::*                    LISTEN      28644/named
tcp6       0      0 :::22                   :::*                    LISTEN      2052/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN      28644/named
tcp6       0      0 :::25                   :::*                    LISTEN      28769/master
udp        0      0 0.0.0.0:514             0.0.0.0:*                           24501/rsyslogd
udp        0      0 10.60.1.10:53           0.0.0.0:*                           28644/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           28644/named
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2022/dhclient3
udp        0      0 0.0.0.0:59498           0.0.0.0:*                           24501/rsyslogd
udp        0      0 10.60.1.10:123          0.0.0.0:*                           22575/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           22575/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           22575/ntpd
udp6       0      0 :::514                  :::*                                24501/rsyslogd
udp6       0      0 :::53                   :::*                                28644/named
udp6       0      0 ::1:123                 :::*                                22575/ntpd
udp6       0      0 fe80::20b:dbff:fe93:123 :::*                                22575/ntpd
udp6       0      0 :::123                  :::*                                22575/ntpd





Ntop is using port 3000 so why is it not working???

---

### Post by robp2175 on 2013-11-22
know this thread is somewhat old, but I think I know why you can't see the ntop interface and it might help other users whom come upon this. I am guessing that the problem could likely be that apache2 is running. Stop the apache2 service by doing
```
service apache2 stop
```

Then check ntop again. Ntop and apache2 can not be used at the same time without using proxypass. If this solves your problem, then stop apache2 from starting at boot
```
sudo update-rc.d -f apache2 disable
```

---

