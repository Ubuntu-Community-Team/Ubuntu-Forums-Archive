---
title: "Cisco VPN Client. Plz help"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by de049 on 2005-08-04
Hi all,

i have just setup my Cisco VPN client for linux on my Ubuntu 5.04 laptop

When i use the *vpnclient connect <profile>* command, it returns this:

Initializing the VPN connection.
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
bind: Address already in use
bind: dst addr 0.0.0.0 port 500
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

**Could someone please explain where i'm going wrong or what i need to modify?**

Thanks!

---

### Post by movies1978 on 2005-08-24
Hi,
have you tried **sudo**  *vpnclient connect <profile> command*.

This sounds to me like a rights problem?

Best regards 
Mathias

---

### Post by charles.regan on 2005-11-30
samething here but with Breezy. running as sudo.

even VPNC is saying port 500 in use. ???

---

