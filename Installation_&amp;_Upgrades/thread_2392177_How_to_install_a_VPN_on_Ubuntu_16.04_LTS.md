---
title: "How to install a VPN on Ubuntu 16.04 LTS"
date: 2018-05-17
forum: Installation &amp; Upgrades
---

### Post by brickhouseblues on 2018-05-17
Can anyone help me with advise on what VPN I can install on my Unbuntu OS?... 

I am operating;
Pentium(R) Dual-Core CPU T4400 @ 2.20GHz × 2 
64-bit

I was looking at "Shrew Soft VPN Access Manager" and "Software Token (small)" but they seem to be complicated.

Thanks :confused:

---

### Post by TheFu on 2018-05-18
There are a few.
tinc, openvpn, ssh, libreswan.  These are all servers you'd run on your system, so you could connect from anywhere in the world.

Just depends on what you need, what you plan to do with it, and how the clients will connect.

For quick access or as a SOCK Proxy when away from home, I'll use ssh. ssh is how Unix systems communicate and how pretty much all network servers and network devices are managed remotely.

If I'm on android or need all network ports and protocols sent through the VPN, then I use openvpn with AES-256.
I've never used tinc or libreswan.

Whatever you do, don't touch any pptp VPNs. They've been totally hacked since 2002.

If you just want to be a client and connect to a commercial VPN provider, that is a different question.  Lots of "Best VPN" guide articles on the internet.  TheWireCutter has a fairly new one, though I find, since they get kickbacks, that they recommend more expensive products. But their what to look for is usually very good.

---

