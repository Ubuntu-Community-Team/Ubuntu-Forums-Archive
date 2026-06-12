---
title: "need to forward ports when using debtorrent?"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by robertbub on 2010-10-24
I set up debtorrent on all my machines on my LAN, which is a varied mix of machines, including one Karmic, one Lucid, and a Debian Squeeze.  These are behind a NAT-based firewall.  I'm not sure if I'm getting any benefits from the bittorrent peer-to-peer features because I am not forwarding any ports.

So, here are my questions.[LIST=1][*]Does anyone have a similar configuration?
[*]How does one deal with debtorrent on multiple machines?
[*]Does it really help if ports are forwarded?
[*]If forwarding helps, does one need to segment the forwarded ports for each different machine?[/LIST]

Thanks.

---

### Post by cchhrriiss121212 on 2010-10-24
Port forwarding will help, but it is not strictly necessary for one off downloads. As you are looking to use debtorrent I assume you will want to seed a lot so I'd say it is a good idea. 
I'm not sure what you mean about segmenting. Create an open port exception for each machine in your firewall setup and then specify the port to use from within debtorrent. 

See here:
[http://debtorrent.alioth.debian.org/FAQ/#index3h3](http://debtorrent.alioth.debian.org/FAQ/#index3h3)

---

### Post by robertbub on 2010-10-24
> **cchhrriiss121212 said:**
> Create an open port exception for each machine in your firewall setup and then specify the port to use from within debtorrent.Does the port specified within debtorrent have to strictly match the port opened on the firewall device?  I.e., is this a viable solution?:[LIST][*]**Lucid machine**:
[LIST][*]local port 9988[*]firewall port 9988[/LIST]
[*]**Karmic machine**:[LIST][*]local port 9988[*]firewall port 9989[/LIST]
[*]**Debian machine**:[LIST][*]local port 9988[*]firewall port 9990[/LIST]
[/LIST]Or, must the local port match the externally visible port?

Thanks.

---

### Post by cchhrriiss121212 on 2010-10-24
> **robertbub said:**
> Or, must the local port match the externally visible port?

It's this one. What I do is have a separate port opened for each machine, so desktop A will use 7889, and desktop B will use 7888.

---

### Post by robertbub on 2010-10-25
Hopefully, my final questions: what about the "ip" variable in the configuration file */etc/debtorrent/debtorrent-client.conf*?  If my assigned ip address dynamically changes, what do I do?

Thanks.

---

### Post by cchhrriiss121212 on 2010-10-25
Hopefully that will not happen, and if it does it should not occur too often. I can't say I've had any of my IPs changed in the last few years.
If it does happen you will need to edit the config.

---

