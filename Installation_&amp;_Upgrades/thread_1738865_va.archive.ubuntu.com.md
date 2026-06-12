---
title: "va.archive.ubuntu.com"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by Lewis Cawte on 2011-04-25
I was looking through the server lists, and wondered if va.archive.ubuntu.com that server was for?

Is it for Virginia?

---

### Post by matt_symes on 2011-04-25
Hi

> **Lewis Cawte said:**
> I was looking through the server lists, and wondered if va.archive.ubuntu.com that server was for?

Is it for Virginia?

```
matthew@matthew-laptop:~$ sudo nslookup va.archive.ubuntu.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	va.archive.ubuntu.com
Address: 91.189.88.31
Name:	va.archive.ubuntu.com
Address: 91.189.88.30
Name:	va.archive.ubuntu.com
Address: 91.189.92.171
Name:	va.archive.ubuntu.com
Address: 91.189.92.170
Name:	va.archive.ubuntu.com
Address: 91.189.92.169
Name:	va.archive.ubuntu.com
Address: 91.189.88.46
Name:	va.archive.ubuntu.com
Address: 91.189.88.45
Name:	va.archive.ubuntu.com
Address: 91.189.88.40

matthew@matthew-laptop:~$ 

```

```
matthew@matthew-laptop:~$ whois 91.189.88.40
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: this output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '91.189.88.0 - 91.189.95.255'

inetnum:        91.189.88.0 - 91.189.95.255
netname:        CANONICAL-CORE
descr:          Canonical Ltd
country:        GB
org:            ORG-CAN1-RIPE
admin-c:        CAN-RIPE
tech-c:         CAN-RIPE
status:         ASSIGNED PI
mnt-by:         RIPE-NCC-END-MNT
mnt-lower:      RIPE-NCC-END-MNT
mnt-by:         CANONICAL-MNT
mnt-routes:     CANONICAL-MNT
mnt-domains:    CANONICAL-MNT
remarks:        rev-srv:        ns1.canonical.com
remarks:        rev-srv:        ns2.canonical.com
remarks:        rev-srv:        ns3.canonical.com
source:         RIPE # Filtered
remarks:        rev-srv attribute deprecated by RIPE NCC on 02/09/2009

organisation:   ORG-CAN1-RIPE
org-name:       Canonical Ltd
org-type:       OTHER
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
address:        United Kingdom
e-mail:         info@canonical.com
mnt-ref:        CANONICAL-MNT
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

role:           Canonical Ltd Admin
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
e-mail:         hostmaster@canonical.com
admin-c:        LJ974-RIPE
admin-c:        JT2256-RIPE
admin-c:        NM1806-RIPE
admin-c:        CJ1182-RIPE
admin-c:        SS8542-RIPE
tech-c:         LJ974-RIPE
tech-c:         JT2256-RIPE
tech-c:         NM1806-RIPE
tech-c:         CJ1182-RIPE
tech-c:         SS8542-RIPE
nic-hdl:        CAN-RIPE
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

% Information related to '91.189.88.0/21AS41231'

route:          91.189.88.0/21
descr:          Canonical Route Object
origin:         AS41231
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

matthew@matthew-laptop:~$ 

```

Kind regards

---

### Post by Lewis Cawte on 2011-04-25
So from what I understand of that, the IPs are registered in the Isle of Man?

---

### Post by matt_symes on 2011-04-25
Hi

> **Lewis Cawte said:**
> So from what I understand of that, the IPs are registered in the Isle of Man?

Seems to be the case. Whether the server is there or not is a different matter but ip's are allocated based on geography.

IIRC, that's how things like the BBC iplayer and others block content for different users in different countries.

[http://www.whois365.com/en/ip/91.189.93.3](http://www.whois365.com/en/ip/91.189.93.3)

Kind regards

---

