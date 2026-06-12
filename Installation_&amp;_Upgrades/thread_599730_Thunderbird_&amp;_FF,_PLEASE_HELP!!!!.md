---
title: "Thunderbird &amp; FF, PLEASE HELP!!!!"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by HoudiniWater on 2007-11-01
After updating to 7.10 both Firefox and Thunderbird do not work. I can pink everything in Internet, but FF can not show any web site, Thunderbird doesn't send e-mails.
Searching the web I learn that for FF problem is in ipv6: false
But still what to do for Thunderbird.
I'll explain more exactly:
I have 2 computers, both with Thunderbird as mail client, same version. After updating Ubuntu's Thunbird can not recieve anything from server for too long, and shows error: time is up. This time Thunderbird on Windows works fine.

Please help!

---

### Post by ddrichardson on 2007-11-01
If you mean disabling IPv6 in Firefox solved the problem then disable it system wide. Open a terminal and type```
gksudo gedit /etc/modprobe.d/aliases
```Then find the following line```
alias net-pf-10 ipv6
```Change it to:```
alias net-pf-10 off
```Then reboot the system.

---

### Post by ddrichardson on 2007-11-01
If you mean disabling IPv6 in Firefox solved the problem then disable it system wide. Open a terminal and type```
gksudo gedit /etc/modprobe.d/aliases
```Then find the following line```
alias net-pf-10 ipv6
```Change it to:```
alias net-pf-10 off
```Then reboot the system.

---

### Post by ddrichardson on 2007-11-01
Wow no idea why that posted twice.

---

