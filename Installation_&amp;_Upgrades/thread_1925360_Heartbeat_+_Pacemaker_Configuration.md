---
title: "Heartbeat + Pacemaker Configuration"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by gerr1t on 2012-02-14
Heya!

I recently followed a small tutorial setting up IP failover with Heartbeat + Pacemaker on Ubuntu.
It works like a charm!

I would like to expand my configuration, I want heartbeat to restart a service whenever the IP does a failover.

Right now my configuration looks like this;

root@machine1:/# crm configure show

```
node $id="60592209-652c-4a-909f-517754348251" machine1
node $id="d1e8edd2-c0d0-45-8b28-5193ba830418" machine2
primitive controller ocf:heartbeat:IPaddr \
    params ip="10.10.10.10" cidr_netmask="255.255.255.0" nic="eth0" \
    op monitor interval="40s" timeout="20s"
location controller_pref controller 100: machine1
property $id="cib-bootstrap-options" \
    dc-version="1.0.9-unknown" \
    cluster-infrastructure="Heartbeat" \
    stonith-enabled="false"
```Can anyone help me out on how to configure this? Maybe with some examples?

Thanks a bunch!

---

### Post by gerr1t on 2012-02-15
Heya!

Anyone got any clue? :)

---

