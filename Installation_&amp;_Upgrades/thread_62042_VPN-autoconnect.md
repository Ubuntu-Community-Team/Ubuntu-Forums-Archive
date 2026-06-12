---
title: "VPN-autoconnect?"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by Dethread on 2005-09-03
Hi!

I'm trying to my university's network via VPN, it works fine in Windows.
I use the following settings:

Hostname:172.x.x.x
Gateway:172.x.x.x
Username:MyName
Pwd:MyPwd

I can connect fine to the network itself, but can't establish a connection to VPN. 

I already tried vpnc with the following config-file:
IPSec gateway Gateway (see above)
IPSec ID Hostname (see above, is this right?)
Xauth username Username (see above)

When I execute vpnc-connect it asks for my password, which I enter, but then nothing happens. Are there some settings that are missing?

By the way: In Windows the CHAP-Protocol is used, but it doesn't use a password (see, I'm already connected to the LAN).

Any help is appreciated.
Thanks.

Dethread

---

