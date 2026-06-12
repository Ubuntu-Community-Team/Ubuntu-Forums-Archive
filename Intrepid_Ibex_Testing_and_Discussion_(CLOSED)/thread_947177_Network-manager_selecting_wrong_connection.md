---
title: "Network-manager selecting wrong connection"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Benjamin_Lebsanft on 2008-10-14
I moved /etc/network/interfaces to /etc/network/interfaces.bak, so that network-manager works again, I created my dorm connection, named it "dorm" and selected "connect automatically". After reboot there was an "auto eth0" connection, using DHCP, which won't work here, because we need specific IPs, so I deleted that connection, after reboot it was there and again the default. After removing "connect automatically" and rebooting, no changes, the box is ticked again, grr. Sometimes network-manager uses the right connection, but most of the times it doesn't. Is there anything I can do against that?

---

