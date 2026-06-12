---
title: "Localhost Printer failure after upgrade to 14.04"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2014-04-22
I have just upgraded online from 13.10 to 14.04. (In fact this was a Xubuntu upgrade, but that should not effect the problem)

My localhost printer (it's from Samsung, but I doubt that is the problem) now will not work. The document print status shows 'stopped'. There is a popup entitled "Printer Error" with the text "There was a problem with document xxx". (And in case you are wondering, no I have not done anything with the printer or PC hardware, and the printer will still print a test page)

I have followed the Ubuntu troubleshooter which has produced the 2 files below.

To the naive user (me) it looks like a cups related issue

The troubleshooter error file is long and starts:

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Samsung-ML-4600 (default)>,
 'cups_instance': None,
 'cups_queue': u'Samsung-ML-4600',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/lp0',
                       'printer-info': u'Samsung ML-4600',
                       'printer-is-shared': True,
                       'printer-location': u'Atlas',
                       'printer-make-and-model': u'Samsung ML-4600 - CUPS+Gutenprint v5.2.9',
                       'printer-state': 3,
                       'printer-state-message': u'Rendering completed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8523796,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Samsung-ML-4600'},
 'cups_printer_remote': False,
 'is_cups_class': False,
```

and it ends:

```
      'D [22/Apr/2014:11:33:23 +0200] [Job 313] Removing document files.',
               'D [22/Apr/2014:11:33:23 +0200] cupsd is not idle any more, canceling shutdown.',
               'D [22/Apr/2014:11:33:23 +0200] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=30945, response=0x7f5e42873040(IPP_IDLE), pipe_pid=0, file=-1',
               'D [22/Apr/2014:11:33:23 +0200] [Client 17] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0',
               'D [22/Apr/2014:11:33:23 +0200] [Client 17] bytes=0, http_state=0, data_remaining=0',
               'D [22/Apr/2014:11:33:23 +0200] [Client 17] Waiting for request.',
               'D [22/Apr/2014:11:33:23 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [22/Apr/2014:11:33:23 +0200] cupsd is not idle any more, canceling shutdown.',
               'D [22/Apr/2014:11:33:24 +0200] [Client 18] PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"',
               'D [22/Apr/2014:11:33:24 +0200] [Client 18] Authorized as root using PeerCred',
               'D [22/Apr/2014:11:33:24 +0200] cupsdIsAuthorized: username="root"',
               'D [22/Apr/2014:11:33:24 +0200] cupsd is not idle any more, canceling shutdown.',
               'I [22/Apr/2014:11:33:24 +0200] Installing config file "/etc/cups/cupsd.conf"...',
               'D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"',
               'D [22/Apr/2014:11:33:24 +0200] [Client 17] Closing connection.',
               'D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'D [22/Apr/2014:11:33:24 +0200] [Client 18] Closing connection.',
               'D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"',
               'I [22/Apr/2014:11:33:24 +0200] Generating printcap /var/run/cups/printcap...',
               'D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"',
               'E [22/Apr/2014:11:33:24 +0200] Unknown directive JobPrivateAccess on line 85 of /etc/cups/cupsd.conf.',
               'E [22/Apr/2014:11:33:24 +0200] Unknown directive JobPrivateValues on line 86 of /etc/cups/cupsd.conf.',
               'E [22/Apr/2014:11:33:24 +0200] Unknown directive SubscriptionPrivateAccess on line 87 of /etc/cups/cupsd.conf.',
               'E [22/Apr/2014:11:33:24 +0200] Unknown directive SubscriptionPrivateValues on line 88 of /etc/cups/cupsd.conf.',
               "W [22/Apr/2014:11:33:24 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Samsung-ML-4600-Gray..' already exists"],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_GB',
 'user_locale_messages': 'en_GB'}
```

Full report at:
[http://pastebin.com/JimpJ2Lc](http://pastebin.com/JimpJ2Lc)

The error report looks similar and ends:

```
D [22/Apr/2014:11:33:23 +0200] [Job 313] Removing document files.
D [22/Apr/2014:11:33:23 +0200] cupsd is not idle any more, canceling shutdown.
D [22/Apr/2014:11:33:23 +0200] [Client 17] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=30945, response=0x7f5e42873040(IPP_IDLE), pipe_pid=0, file=-1
D [22/Apr/2014:11:33:23 +0200] [Client 17] Writing IPP response, ipp_state=DATA, old wused=0, new wused=0
D [22/Apr/2014:11:33:23 +0200] [Client 17] bytes=0, http_state=0, data_remaining=0
D [22/Apr/2014:11:33:23 +0200] [Client 17] Waiting for request.
D [22/Apr/2014:11:33:23 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Apr/2014:11:33:23 +0200] cupsd is not idle any more, canceling shutdown.
D [22/Apr/2014:11:33:24 +0200] [Client 18] PUT /admin/conf/cupsd.conf HTTP/1.1
D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Active clients and dirty files", busy="Dirty files"
D [22/Apr/2014:11:33:24 +0200] [Client 18] Authorized as root using PeerCred
D [22/Apr/2014:11:33:24 +0200] cupsdIsAuthorized: username="root"
D [22/Apr/2014:11:33:24 +0200] cupsd is not idle any more, canceling shutdown.
I [22/Apr/2014:11:33:24 +0200] Installing config file "/etc/cups/cupsd.conf"...
D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
D [22/Apr/2014:11:33:24 +0200] [Client 17] Closing connection.
D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [22/Apr/2014:11:33:24 +0200] [Client 18] Closing connection.
D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
I [22/Apr/2014:11:33:24 +0200] Generating printcap /var/run/cups/printcap...
D [22/Apr/2014:11:33:24 +0200] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
E [22/Apr/2014:11:33:24 +0200] Unknown directive JobPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [22/Apr/2014:11:33:24 +0200] Unknown directive JobPrivateValues on line 86 of /etc/cups/cupsd.conf.
E [22/Apr/2014:11:33:24 +0200] Unknown directive SubscriptionPrivateAccess on line 87 of /etc/cups/cupsd.conf.
E [22/Apr/2014:11:33:24 +0200] Unknown directive SubscriptionPrivateValues on line 88 of /etc/cups/cupsd.conf.
W [22/Apr/2014:11:33:24 +0200] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Samsung-ML-4600-Gray..' already exists
```

Full report at:
[http://pastebin.com/iGYmWk3L](http://pastebin.com/iGYmWk3L)

Thanks for any help you can offer

---

### Post by hans12345 on 2014-04-25
Bump

---

### Post by hans12345 on 2014-04-25
I looked at the job-printer-state-message for the stopped job. I saw this:

PPD version (5.2.9) not compatible with Gutenprint 5.2.10--pre2

Can this be an indication of my problem? Something new in 14.04 has caused a PPD failure?

---

### Post by hans12345 on 2014-04-27
Finally cracked it.

The key message was "PPD version (5.2.9) not compatible with Gutenprint 5.2.10--pre2"

I did some study of CUPS and found there was a web interface. I found my printer was not enabled and I could not enable it.

So I started again to install the printer, this time with the web interface. When I came to select the driver, the web interface gave me a long list starting with the Gutenprint one, which I probably would have chosen, except down the list there was :

   foomatic/pximono (recommended)

Since it was recommended I tried it. And it works!!

:D

---

### Post by ErniePort on 2014-04-27
Thank you, Hans. I've been trying to track down this problem since the Xubuntu 14.10 upgrade. I tried footmatic and it works perfectly.

---

### Post by alcarola on 2014-06-19
I did not have the foomatic option, but already deleting the printer and installing it again with the same driver solved the problem. I guess that is meant by footnote *1 on this page: [http://sourceforge.net/p/gimp-print/mailman/gimp-print-announce/](http://sourceforge.net/p/gimp-print/mailman/gimp-print-announce/)

---

