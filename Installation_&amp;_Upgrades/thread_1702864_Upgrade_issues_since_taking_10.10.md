---
title: "Upgrade issues since taking 10.10"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by ScriptMaverick on 2011-03-08
Since upgrading to Ubuntu 10.10 I can nolonger get access to the wireless network.
I've updated the /var/lib/NetworkManager/NetworkManager.state file to true and the /usr/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

When I reboot I lose these settings. I have tried these using sudo gedit /path and as root but the changes are lost on reboot.

---

