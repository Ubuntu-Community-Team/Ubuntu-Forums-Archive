---
title: "wpa_supplemets problem after upgrade"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bacil on 2009-07-25
Hi just tested upgrade of kubuntu to 9.10 and my wireless is in shreds with :
```
EVENT-DISCONNECTED - Disconnect event - [I]remove key
```
it* seems that *after upgrade even when psk was set and recorded it is not able to fulsh it and reuse.

Any advice ?

PS: i have read all wpa_supplements articles :)
[/I]

---

### Post by bacil on 2009-07-25
Right - problem got even wierder now

i have tested it with nm instead of knetworkmanager and it works no problem at all. i have now running system that can log in on to the network using nm or nm-applet but knetworkmanager and plasma-widget-network-manager cause  CTRL-EVENT-DISCONNECTED - Disconnect event - [I]remove key

Anyone with same experience ?

[/I]

---

### Post by taavikko on 2009-07-25
[https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593](https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593)

---

### Post by bacil on 2009-07-25
> **taavikko said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593](https://bugs.edge.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593)

yup seems simillar . not the same tho

my build is yesterdays :-) ..  anyway will have look to pwnm

---

