---
title: "do-release-upgrade stopped working"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by tobby on 2011-10-15
Hi

I tried to do a do-release-upgrade on my homeserver to update from 11.04 to 11.10.

But it stopped working at
```
openssl (1.0.0e-2ubuntu4) wird eingerichtet ...
Neue Version der Konfigurationsdatei /etc/ssl/openssl.cnf wird installiert ...
ca-certificates (20110502+nmu1ubuntu5) wird eingerichtet ...
Clearing symlinks in /etc/ssl/certs...done.
Updating certificates in /etc/ssl/certs... WARNING: Skipping duplicate certificate IGC_A.pem
WARNING: Skipping duplicate certificate IGC_A.pem
WARNING: Skipping duplicate certificate UbuntuOne-Go_Daddy_Class_2_CA.pem
WARNING: Skipping duplicate certificate UbuntuOne-Go_Daddy_Class_2_CA.pem
156 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
```

It doesn't continue since 7 hours.

What can I do now?

Greets Tobias

---

### Post by gppixelworks on 2011-10-15
FWIW, I've experienced the same on a desktop system.  Attempted to upgrade from 11.04 to 11.10 (64bit).

The upgrade stalled at various places yet indicates it's still downloading and there is a flow of data down from the 'Net while it's stalled.  Aborted several times after leaving it stalled anywhere from overnight to a couple hours.

Wish I could help both of us.  	](*,)

---

