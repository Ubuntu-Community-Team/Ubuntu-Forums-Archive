---
title: "No icon confirming VPN connection"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2015-11-13
I just upgraded from Lubuntu 15.04 to 15.10. I run it from a thumb drive on a Dell desktop. I connect to my virtual private network via OpenVPN.  In the previous install, whenever I connected to my VPN, the ordinary icon in the task bar showing the wired connection would change to one confirming that the VPN connection had been made.  Now in 15.10, the wired connection icon remains unchanged after the VPN connection is made.  Can this be fixed?

---

### Post by dave205 on 2015-11-13
sounds like your vpn isnt working. just curious, have you went to a site to verify that its working?  privateinternetaccess will detect and tell you if "youre protected" or not.  

as for how to fix it, I don't know. PIA has install scripts so I didnt have to configure openvpn

---

### Post by steve169 on 2015-11-15
The VPN connection s fine. It's just there's no icon indicating that in the taskbar. I can live without it.

---

### Post by dave205 on 2015-12-28
I have found that if I run openvpn from a terminal then I do not get the icon either. I only get the icon if I use the network config manager to connect to the vpn.

(ubuntu 15.10)

---

### Post by sammiev on 2015-12-28
Hi,

lubuntu does not show the vpn lock in 16o4 but if you check the IP address it shows you are connected as well as the vpn panel.

---

