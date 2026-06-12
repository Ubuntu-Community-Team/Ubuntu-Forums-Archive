---
title: "cloud init and providing multiple search domains"
date: 2021-11-09
forum: Installation &amp; Upgrades
---

### Post by godfather007 on 2021-11-09
I'm not sure if i should post this here as well.


In the foreseable future we want to spin VM's automated on our hypervisor and through cloud-init provide it with it's IP-settings (manual or DHCP)


Unfortunately multiple DNS search suffixes end up with "044"  in between and thus not working (multiple mDNS needed).



Any idea how to get this to work? A special seperator character which does not create the 044 or other number.


Thanks in advance

---

### Post by godfather007 on 2021-11-09
Sorry, it feels there is a proxmox problem.

Whenever the setting is published on a " per VM "  base, it works. Using the "use host server" settings, it doesn't (using manual IP)

---

