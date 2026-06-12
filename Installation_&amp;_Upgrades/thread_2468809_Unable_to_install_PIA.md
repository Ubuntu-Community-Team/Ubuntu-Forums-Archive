---
title: "Unable to install PIA"
date: 2021-11-10
forum: Installation &amp; Upgrades
---

### Post by unknown_user on 2021-11-10
I have downloaded PIA for Ubuntu from the official PIA site.
When it downloads it is in a .run file
There are no instructions on how to install PIA on my 21.04 system.

Can anyone help?

---

### Post by ActionParsnip on 2021-11-10
Mark it as executable and run in a terminal. I assume you mean this
[https://www.privateinternetaccess.com/download/linux-vpn](https://www.privateinternetaccess.com/download/linux-vpn)

---

### Post by TheFu on 2021-11-10
I've used PIA previously.  I just install the normal openvpn package, then download the openvpn .ovpn settings .tgz file (filled with all the different exit nodes w/ 4096 ca crt and crl PEM files from PIA) and use that directly.  openvpn is openvpn.

I understand they have wireguard support too, but never tried that.

---

