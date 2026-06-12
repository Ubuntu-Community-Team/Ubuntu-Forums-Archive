---
title: "snap store proxy in a semi air gapped network"
date: 2024-02-22
forum: Installation &amp; Upgrades
---

### Post by simonjcarr on 2024-02-22
our main network has a proxy server that provides access to the internet. We also have a private network where most machines can not communicate with the main network. There is however one machine on the private network that is running squid and has the main network proxy as a peer.
I have create a ubuntu 22.04 VM on the airgapped network and set it up to use the Squid proxy and have installed snap-store-proxy and postgres following these instructions [https://docs.ubuntu.com/snap-store-proxy/en/install](https://docs.ubuntu.com/snap-store-proxy/en/install)

When I check connections "[COLOR=#333333][FONT=monospace]snap[/FONT][/COLOR][COLOR=#333333][FONT=monospace]-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]proxy[/FONT][/COLOR][COLOR=#A71D5D][FONT=monospace]check[/FONT][/COLOR][COLOR=#333333][FONT=monospace]-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]connections"[/FONT][/COLOR] I get the following DNS Errors

```
sudo snap-proxy check-connections
http: https://dashboard.snapcraft.io: FAILED (dashboard.snapcraft.io:443) dns lookup error
http: https://login.ubuntu.com: FAILED (login.ubuntu.com:443) dns lookup error
http: https://api.snapcraft.io: FAILED (api.snapcraft.io:443) dns lookup error
postgres: localhost: OK
Not all connections are accessible

```

I have set the environment variables in /etc/systemd/system/snapd.service.d/snap_proxy.conf to point to the squid proxy and restarted snapd

[COLOR=#333333]sudo[/COLOR] [COLOR=#333333]snap[/COLOR] [COLOR=#333333]install[/COLOR] [COLOR=#333333]snap[/COLOR][COLOR=#333333]-[/COLOR][COLOR=#333333]store[/COLOR][COLOR=#333333]-[/COLOR][COLOR=#333333]proxy worked OK through the squid proxy[/COLOR]
Does Snap Store Proxy require full DNS resolution even when it has access to a http proxy server?

---

### Post by coffeecat on 2024-02-22
Duplicate of [https://ubuntuforums.org/showthread.php?t=2495538](https://ubuntuforums.org/showthread.php?t=2495538)

Closed.

---

