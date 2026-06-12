---
title: "Installing NRPE in Ubuntu 9.10"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Abast_BCN on 2010-01-27
Hi all!

I'm trying to install NRPE on ubuntu 9.10. My Nagios' server is xxx.xxx.xxx.208 and this nrpe client is xxx.xxx.xxx.69 IP.

Well, I'm following the original Nagios' documentation, but when I arrive to check's pass, I recived an error.

When I do this...:

```
sudo iptables -I RH_Firewall-1-INPUT -p tcp -m tcp -dport 5666 -j ACCEPT
```...I recive this message:

```
Bad argument `5666'
Try `iptables -h' or 'iptables --help' for more information
```Someone could help me?

Thanks in advance!:D

**EDIT**

Sorry! The previous code is wrong! it's for Fedora system's. So, I used this code:
```
sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5666 -j ACCEPT
```And it works!


**Edit2**:

I have an other problem. When I install nrpe plugin on Nagios server and I do this:
```
/usr/local/nagios/libexec/check_nrpe -H xxx.xxx.xxx.69
```

Well, it appears a socket time out. Someone know what happens?

Thanks for all!

---

