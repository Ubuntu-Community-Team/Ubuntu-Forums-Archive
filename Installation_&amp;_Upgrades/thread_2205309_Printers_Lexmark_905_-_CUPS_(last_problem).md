---
title: "Printers Lexmark 905 - CUPS (last problem)"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by pawelmackowiak on 2014-02-13
Welcome. 
I spent the whole day in search of drivers for this printer model. 
Finally I succeeded. 
From: 
[http://support.lexmark.com/index?locale](http://support.lexmark.com/index?locale) ... M_PRO905 # 2 
Home demo, however, is not I print 
Here is the log: (UPDATE) 
Thank you for the tips that I do not like



```
E [13/Feb/2014:00:30:31 +0100] [Job 63] Stopping unresponsive job!
D [13/Feb/2014:00:30:31 +0100] Avahi entry group established for Lexmark_Pro800Pro900_Series @ pawel-K56CB
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Feb/2014:00:30:31 +0100] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:00:30:31 +0100] [Job 61] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 62] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 63] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 64] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 65] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 66] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Feb/2014:00:30:31 +0100] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:00:30:31 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username=""
D [13/Feb/2014:00:30:31 +0100] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [13/Feb/2014:00:30:31 +0100] cupsdCloseClient: 13
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAcceptClient: 13 from localhost (Domain)
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
I [13/Feb/2014:00:30:31 +0100] Installing config file "/etc/cups/cupsd.conf"...
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdCloseClient: 13
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdDeregisterPrinter(p=0x7fd901287ab0(Lexmark_Pro800Pro900_Series), removeit=1)
I [13/Feb/2014:00:30:31 +0100] Generating printcap /var/run/cups/printcap...
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [13/Feb/2014:00:30:31 +0100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive JobPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive JobPrivateValues on line 91 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive SubscriptionPrivateAccess on line 92 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive SubscriptionPrivateValues on line 93 of /etc/cups/cupsd.conf.
W  [13/Feb/2014:00:30:31 +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id  'Lexmark_Pro800Pro900_Series-Gray..' already exists
W  [13/Feb/2014:00:30:31 +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id  'Lexmark_Pro800Pro900_Series-RGB..' already exists
W  [13/Feb/2014:00:30:31 +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Lexmark_Pro800Pro900_Series' already exists
E [13/Feb/2014:00:30:31 +0100] Failed to update TXT record for Lexmark_Pro800Pro900_Series @ pawel-K56CB: -2
```

---

### Post by pawelmackowiak on 2014-02-13
Welcome. 
Ubuntu 12.04. OS LUNA
I spent the whole day in search of drivers for this printer model. 
Finally I succeeded. 
From: 
[http://support.lexmark.com/index?locale](http://support.lexmark.com/index?locale) ... M_PRO905 # 2 
Home demo, however, is not I print 
Here is the log:
Thank you for the tips that I do not like
```
E [13/Feb/2014:00:30:31 +0100] [Job 63] Stopping unresponsive job!
D [13/Feb/2014:00:30:31 +0100] Avahi entry group established for Lexmark_Pro800Pro900_Series @ pawel-K56CB
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Feb/2014:00:30:31 +0100] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:00:30:31 +0100] [Job 61] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 62] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 63] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 64] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 65] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] [Job 66] Loading attributes...
D [13/Feb/2014:00:30:31 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 POST / HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 1.1 Get-Jobs 1
D [13/Feb/2014:00:30:31 +0100] Get-Jobs ipp://localhost/printers/
D [13/Feb/2014:00:30:31 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: No authentication data provided.
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username=""
D [13/Feb/2014:00:30:31 +0100] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [13/Feb/2014:00:30:31 +0100] cupsdCloseClient: 13
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAcceptClient: 13 from localhost (Domain)
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 GET /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdAuthorize: Authorized as pawel using PeerCred
D [13/Feb/2014:00:30:31 +0100] cupsdIsAuthorized: username="pawel"
I [13/Feb/2014:00:30:31 +0100] Installing config file "/etc/cups/cupsd.conf"...
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdCloseClient: 13
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [13/Feb/2014:00:30:31 +0100] cupsdDeregisterPrinter(p=0x7fd901287ab0(Lexmark_Pro800Pro900_Series), removeit=1)
I [13/Feb/2014:00:30:31 +0100] Generating printcap /var/run/cups/printcap...
D [13/Feb/2014:00:30:31 +0100] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [13/Feb/2014:00:30:31 +0100] Unknown directive SystemGroup on line 4 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive JobPrivateAccess on line 90 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive JobPrivateValues on line 91 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive SubscriptionPrivateAccess on line 92 of /etc/cups/cupsd.conf.
E [13/Feb/2014:00:30:31 +0100] Unknown directive SubscriptionPrivateValues on line 93 of /etc/cups/cupsd.conf.
W  [13/Feb/2014:00:30:31 +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id  'Lexmark_Pro800Pro900_Series-Gray..' already exists
W  [13/Feb/2014:00:30:31 +0100] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id  'Lexmark_Pro800Pro900_Series-RGB..' already exists
W  [13/Feb/2014:00:30:31 +0100] failed to CreateDevice:  org.freedesktop.ColorManager.AlreadyExists:device id  'cups-Lexmark_Pro800Pro900_Series' already exists
E [13/Feb/2014:00:30:31 +0100] Failed to update TXT record for Lexmark_Pro800Pro900_Series @ pawel-K56CB: -2
```

---

### Post by pawelmackowiak on 2014-02-15
Use for more than 15 years of Windows. I installed Linux OS Lona and say wow. I immediately started using it and I became a fan of his until there arose a problem and a big - problem with the printer driver. After spending 24 hours on finding drivers finally installed them, but still the printer is not working. Is one of the forum can not write eg. Falling and so YOU do not help or get out. The entry remains without any echo. 
My office can not work - because I can not run a "dumb" device. 
Thank you in advance for any help in this matter.

---

### Post by pawelmackowiak on 2014-02-15
Use for more than 15 years of Windows. I installed Linux OS Lona and say wow. I immediately started using it and I became a fan of his until there arose a problem and a big - problem with the printer driver. After spending 24 hours on finding drivers finally installed them, but still the printer is not working. Is one of the forum can not write eg. Falling and so YOU do not help or get out. The entry remains without any echo. 
My office can not work - because I can not run a "dumb" device. 
Thank you in advance for any help in this matter.

---

### Post by howefield on 2014-02-15
Threads merged.

Have you tried [http://www.lexmark.com/en_US/about-us/company/contact-us.shtml](http://www.lexmark.com/en_US/about-us/company/contact-us.shtml)

---

### Post by pawelmackowiak on 2014-02-20
Thanks for bearing - write and let you know.

---

