---
title: "VPN broke on update"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by VirtualEdgar on 2008-10-24
Hi! I am using Intrepid Ibex Alpha 6 and when I installed the downloaded updates I cant use my VPN anymore using networkmanager pptp (gnome). Before the update it was ok. Here is what I found in the logs...

```
Oct 24 11:55:03 ubuntu NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Oct 24 11:55:03 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6838 
Oct 24 11:55:03 ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Oct 24 11:55:03 ubuntu NetworkManager: <info>  VPN plugin state changed: 1 
Oct 24 11:55:03 ubuntu NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: vpn-password-dialog.c.299 (nma_vpn_request_password): canceled. 
Oct 24 11:55:03 ubuntu NetworkManager: <info>  Policy set 'Auto xxx' (wlan0) as default for routing and DNS. 
Oct 24 11:55:15 ubuntu NetworkManager: <debug> [1224820515.766980] ensure_killed(): waiting for vpn service pid 6838 to exit 
Oct 24 11:55:15 ubuntu NetworkManager: <debug> [1224820515.767462] ensure_killed(): vpn service pid 6838 cleaned up 

```

Error: "The VPN connection 'x' failed because there were no valid VPN secrets"

I am using NM 0.7.0. I hope somebody can help me.

Thanks!

---

### Post by VirtualEdgar on 2008-10-25
Anyone please?

---

### Post by K.Mandla on 2008-10-25
Moved to Intrepid Ibex Discussions.

---

### Post by Sophont on 2008-10-25
Try to remove the password from the VPN dialog.

You should then get asked on connection for the password - that worked for some people (another thread in this forum).

Known problem.

---

### Post by Luffield on 2008-10-25
Try this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/2](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/2)

---

### Post by VirtualEdgar on 2008-10-25
> **Sophont said:**
> Try to remove the password from the VPN dialog.

You should then get asked on connection for the password - that worked for some people (another thread in this forum).

Known problem.

This one saved the day!

Thank you very much to those who helped!

---

