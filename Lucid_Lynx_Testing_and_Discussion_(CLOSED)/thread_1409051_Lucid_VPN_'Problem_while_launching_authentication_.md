---
title: "Lucid VPN 'Problem while launching authentication dialog'"
date: 2010-02-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-17
When attempting to connect to VPN in Lucid, I get the following error in a pop-up:
```
**Cannot start VPN Connection 'VPNConnection'**
There was a problem while launching authentication dialog 
for VPN connection type 'org.freedesktop.NetworkManager.pptp.'  
Contact your system administrator.
```

Any advice?

---

### Post by SevenMachines on 2010-02-17
i see 2 different types of pop up error,
1. pptp 'invalid' - need to install network-manager-pptp
2. problem launching authentication dialog for pptp - need to install network-manager-pptp-gnome

you might be having the second one, i agree its not exactly the most informative message or obvious cause of a missing package. might be worth a try though

---

### Post by JCoster on 2010-02-17
Awesome- install network-manager-pptp-gnome fixed it.

Worked in Karmic before I upgraded but at least it's sorted now!

Cheers for your help.

---

