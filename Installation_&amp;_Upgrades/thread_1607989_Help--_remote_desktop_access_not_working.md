---
title: "Help-- remote desktop access not working"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-10-28
I have just installed linux 10.10, I want to use vnc on my another computer to access my desktop using remote access.
When I navigate to Remote esktop Preferences.

Your desktop is only reachable over the local network. Others can access your computer using the address localhost, no ip address.
this is not working.

---

### Post by endotherm on 2010-10-28
it looks like your network is not correctly configured. can you please post back the output of:
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route

```

---

### Post by hoboy on 2010-10-28
> **endotherm said:**
> it looks like your network is not correctly configured. can you please post back the output of:
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route

```

thks. nmmmmmm the compueter is at work I have access to it tomorrow :(

---

### Post by endotherm on 2010-10-28
ok, so to confirm, you want to use remote desktop across the internet, and the PC is on a business network?

that seriously complicates matters beyond the initial network configuration issue. 
to make it work, you will need administrative access to the companies Internet connection (their gateway/firewall router) so you can forward the ports, but more than that, it is not safe to expose VNC services to the web without taking some much heavier precautions like SSH or VPN tunneling. 

tell us a little about the work network you are dealing with

---

### Post by CharlesA on 2010-10-28
Make sure you have permission from the IT guys before doing anything. It could be considered a security risk.

---

### Post by hoboy on 2010-10-28
> **CharlesA said:**
> Make sure you have permission from the IT guys before doing anything. It could be considered a security risk.

Thanks guys, but the I had 9.04 on it and I worked, I have made a freshed installation of 10.10 today

---

