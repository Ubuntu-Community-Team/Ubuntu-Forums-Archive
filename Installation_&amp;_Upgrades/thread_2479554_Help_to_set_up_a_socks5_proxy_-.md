---
title: "Help to set up a socks5 proxy -"
date: 2022-09-28
forum: Installation &amp; Upgrades
---

### Post by jordanyguedes on 2022-09-28
Hi guys, I created a VM on Google Cloud (Ubuntu System) and I'm trying to configure Socks5 proxy

How to solve this error  [https://ibb.co/PhvxByT](https://ibb.co/PhvxByT)

"danted.service: Control process exited, code=exited status=1
danted.service: Failed with result 'exit-code'.
Failed to start SOCKS (v4 and v5) proxy daemon (danted).
Unit danted.service has begun starting up.
danted.service: Failed to parse PID from file /var/run/danted.pid: Inval"

[IMG]https://ibb.co/PhvxByT[/IMG]
[IMG]https://ibb.co/PhvxByT[/IMG]

---

### Post by TheFu on 2022-09-29
For 1 user, you can use ssh in tunneling mode.

For lots of users, you'll want to use a proxy server and create PAC files for them, so they don't know much about the proxy.  The normal proxy on Unix is squid.  Plenty of how-to guides on that tool.

I've posted a script in these forums for using ssh as a proxy to a web browser a few times. Search for it and you will find it. "thefu socks proxy" should find it.  The last time was 1-3 yrs ago, I'm guessing.

---

