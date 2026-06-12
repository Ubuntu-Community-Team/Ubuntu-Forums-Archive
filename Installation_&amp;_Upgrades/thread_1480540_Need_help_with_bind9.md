---
title: "Need help with bind9"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by ferditji on 2010-05-11
Well for the better part of the last two hours I've tried to figure out what is actually wrong, but I can't seem to find anything obvious to me.

What I'm trying to do is setup my DNS for say(per example) domain.com.
This should include two NS records, namely ns1.domain.com and ns2.domain.com.
With that there should be a mail record, as well as a CNAME record for www.

I've been trough roughly 20 how to's in the last two hours, rewrote everything from scratch four times and I still can't seem to find whats wrong.
My only suspicion to this might be two things; the error I get from the bind9 daemon when I stop the service, and the named.conf file. 

The error I get from the bind9 daemon when stopping the service is:
```
* Stopping domain name service... bind9                                        rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.

```
I honestly doesn't know what this means, apart from the key defined in /etc/bind/rndc.key that's not in the named.conf file(yes, I did try to add it to no avail).

Here's all the zone files, and configuration files; [http://208.77.101.5/bind9/](http://208.77.101.5/bind9/)

If anyone could help, it would be greatly appreciated.

---

