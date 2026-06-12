---
title: "DNS not working after upgrade"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by awacs on 2010-04-28
after apt-get upgrade on Karmic, I'm having trouble with name resolution. Main problem now is that the 'order hosts, bind' directive in /etc/host.conf is not respected. A side symptom is this error:

# dig +trace mail.egps.com

; <<>> DiG 9.6.1-P2 <<>> +trace mail.egps.com
;; global options: +cmd
.                       486236  IN      NS      d.root-servers.net.
.                       486236  IN      NS      f.root-

[...]

;; Received 500 bytes from 127.0.0.1#53(127.0.0.1) in 4 ms

dig: isc_socket_create: address family not supported

Eh?

---

### Post by awacs on 2010-04-28
> **awacs said:**
> after apt-get upgrade on Karmic, I'm having trouble with name resolution. Main problem now is that the 'order hosts, bind' directive in /etc/host.conf is not respected. A side symptom is this error:

# dig +trace mail.egps.com

; <<>> DiG 9.6.1-P2 <<>> +trace mail.egps.com
;; global options: +cmd
.                       486236  IN      NS      d.root-servers.net.
.                       486236  IN      NS      f.root-

[...]

;; Received 500 bytes from 127.0.0.1#53(127.0.0.1) in 4 ms

dig: isc_socket_create: address family not supported

Eh?

/etc/nsswitch.conf:

[...]
hosts:          files dns
[...]

---

