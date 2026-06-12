---
title: "NFS mounting via OpenVPN fails during boot"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by Raimund Eimann on 2010-05-21
Hi,

I have my /home and a couple other filesystems on a remote openvpn server (tap device, i.e. bridged connection, not routed) via NFS. When I add the corresponding lines to /etc/fstab, then booting hangs, because the openvpn tunnel seems to start after NFS volumes are mounted.

In my case the openvpn tunnel must come up first. Can someone here tell me how to do this. Google was not my friend in this particular case...

Cheers,
Raimund

---

