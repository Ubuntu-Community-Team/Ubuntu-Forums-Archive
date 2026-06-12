---
title: "Odd errors with VPNC and NetworkManager"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-04-06
I've installed network-manager-vpnc to try to connect to my universities vpn service. I previously successfully did this with intrepid. When I click VPN Connections > Configure VPN the dialog box for VPN is greyed out.

When started through the terminal I got:```
jamie@jaunty-laptop:~$ nm-connection-editor 

(nm-connection-editor:5247): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

** (nm-connection-editor:5247): WARNING **: nm_connection_list_new: failed to load VPN plugins: Couldn't read VPN .name files directory /home/asac/local_nma/etc/NetworkManager/VPN.
```I don't have a user called asac on my system; I think s/he might be a maintainer of nm. I don't know how to get vpnc to work. I tried symlinking /home/asac/local_nma/etc/NetworkManager with /etc/NetworkManager/VPN and chmodding it to a+r, but this didn't seem to work.

EDIT: This is now solved for me. It is possible that it was solved in the latest round of updates, as I saw some for network-manager-*

---

