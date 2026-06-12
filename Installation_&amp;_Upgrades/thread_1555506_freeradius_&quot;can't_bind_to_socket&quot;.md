---
title: "freeradius &quot;can't bind to socket&quot;"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2010-08-18
Latest error while trying to get freeradius working:

"Failed binding to /var/run/radiusd/radiusd.sock"

The debug output quotes the following configuration that does not exist:

 listen {
         type = "control"
  listen {
         socket = "/var/run/radiusd/radiusd.sock"

Per-socket clients are not enabled. 
This just suddenly appeared. The server only had some SSL/cert-related issues before. Where is this configured? How do I fix this?

I'm compiling freeradius to get PEAP (EAP-TLS) support. 
One barrier after another!

---

### Post by jcoles on 2010-08-18
This one was easy. 

There was no /var/run/radiusd directory on my machine, so I created one. It's strange that freeradius wouldn't do that itself. 

The new error occurred because I solved the SSL-related one and the app was ready to actually run. Progress!

---

