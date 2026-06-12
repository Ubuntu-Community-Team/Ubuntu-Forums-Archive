---
title: "NetworkManager not started"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2017-10-20
After upgrading 17.04 -> 17.10, the NetworkManager was not running.
Systems:Networking: 'NetworkManager not running'

SO doing:
'sudo systemctl enable NetworkManager.service' 

fixed this, and after a reboot, the change persists.
I hope this helps someone else.

---

