---
title: "cupsdAuthorize: No authentication data provided"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by samjh on 2010-03-26
I'm currently running Lucid Lynx beta-1 with the latest updates, and am unable to print.

My printer is a Brother HL-1440 with a basic USB connection.  No network sharing, etc.  I've tried various different drivers, but to no effect.

When I print, I'm getting an error dialog with an offer to diagnose the problem using some kind of a trouble-shooting wizard.  Here is the debugging log (my user name has been replaced by * symbols):

```
D [27/Mar/2010:13:05:29 +1000] cupsdReadClient: 16 POST / HTTP/1.1
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Active clients and dirty files
D [27/Mar/2010:13:05:29 +1000] cupsdAuthorize: Authorized as ***** using PeerCred
I [27/Mar/2010:13:05:29 +1000] Saving job cache file "/var/cache/cups/job.cache"...
I [27/Mar/2010:13:05:29 +1000] Saving subscriptions.conf...
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Active clients
D [27/Mar/2010:13:05:29 +1000] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [27/Mar/2010:13:05:29 +1000] Get-Job-Attributes ipp://localhost/jobs/41
D [27/Mar/2010:13:05:29 +1000] [Job 41] Loading attributes...
D [27/Mar/2010:13:05:29 +1000] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/41) from localhost
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Not busy
D [27/Mar/2010:13:05:29 +1000] cupsdReadClient: 16 POST / HTTP/1.1
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Active clients
D [27/Mar/2010:13:05:29 +1000] cupsdAuthorize: Authorized as ***** using PeerCred
D [27/Mar/2010:13:05:29 +1000] cupsdReadClient: 16 1.1 Cancel-Subscription 1
D [27/Mar/2010:13:05:29 +1000] Cancel-Subscription /
D [27/Mar/2010:13:05:29 +1000] cupsdIsAuthorized: username="*****"
D [27/Mar/2010:13:05:29 +1000] cupsdMarkDirty(-----S)
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Active clients and dirty files
D [27/Mar/2010:13:05:29 +1000] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [27/Mar/2010:13:05:29 +1000] cupsdSetBusyState: Dirty files
D [27/Mar/2010:13:05:30 +1000] cupsdAcceptClient: 15 from localhost (Domain)
D [27/Mar/2010:13:05:30 +1000] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1
D [27/Mar/2010:13:05:30 +1000] cupsdSetBusyState: Active clients and dirty files
D [27/Mar/2010:13:05:30 +1000] cupsdAuthorize: No authentication data provided.
```

Any ideas?  Should I file an official bug report?

---

