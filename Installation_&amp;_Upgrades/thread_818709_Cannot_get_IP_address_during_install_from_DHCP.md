---
title: "Cannot get IP address during install from DHCP"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by pixelfest on 2008-06-04
Hello, I have Googled this one and have not found anything that works/helps.

The situation is that I am installing the latest Ubuntu server edition on a Proliant DL 360 with 3x Intel network cards. I come to the bit which lets me choose my network adapter and it fails to get an IP address via DHCP

After it fails, on my Windows 2003 box I check my DHCP leased addresses and it is filled with "Bad address"

If I manually configure the IP settings on Ubuntu i have no network connectivity when Ubuntu is installed.

As it stands now Ubuntu is not installed as I am waiting for more light on the issue. 


Many Thanks

Steve

---

### Post by jimv on 2008-06-04
I can't think of a reason why you would need to get a DHCP address during install anyway.  That can be configured afterwards in the /etc/network/interfaces file.

---

