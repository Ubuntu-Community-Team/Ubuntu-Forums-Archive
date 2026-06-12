---
title: "Unable to connect to VPN"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by appumail on 2008-05-26
Hi,
Installed Cisco Systems VPN Client Version 4.8.01 and patched it. Install process went fine.
Now,disabled the firewall and tried to connect to VPN.Got the following error,

#########################################################
Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.
#########################################################

Any clues what could be wrong? Terribly stuck up with this.

thanks a lot,
Murugesh

---

### Post by duli on 2008-07-28
Hi Murugesh,

no solution, unfortunately ... I rather encountered the same problem and wanted to ask whether you have found a way to solve the problem?

Thanks!

Uli

---

### Post by appumail on 2008-08-05
Yes.
The problem was with the certificate. Run the appropriate cert file and the problem will go away.

thanks,
Murugesh

---

### Post by ee19921 on 2008-10-12
> **appumail said:**
> Yes.
The problem was with the certificate. Run the appropriate cert file and the problem will go away.

thanks,
Murugesh

How do I do that? I have the .cert file in /etc/opt/cisco-vpnclient/Certificates/, still I get the same exact error.

```

Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```

---

### Post by ee19921 on 2008-10-14
> **ee19921 said:**
> How do I do that? I have the .cert file in /etc/opt/cisco-vpnclient/Certificates/, still I get the same exact error.

```

Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```


Copying the certificate wasn't enough. I had to import the root certificate for it to work. 

```
cisco_cert_mgr -R -op import
```

---

