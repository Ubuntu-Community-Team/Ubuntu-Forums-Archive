---
title: "Whats this daemon?"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by Insanely on 2005-03-22
Scan log from nmap:

sudo nmap -sS -v -v -p 1-65535 -O -sV 127.0.0.1

8021/tcp open  ftp     Medusa Async ftpd 1.23 [experimental]

I went to synaptic only to find I haven't got this package installed. I'm a little lost finding information about the package. I also can't work out why this service is running on port 8021. Can someone please turn of their firewall and confirm that there is a service on this port running. I did a ps -aux and could not find this service running. Sadly my linux skills end here.

Thank you for any help

uname -a
Linux hoary 2.6.10-5-386 #1 Tue Mar 15 14:43:37 UTC 2005 i686 GNU/Linux

---

### Post by Insanely on 2005-03-22
I should probably warn you guys I installed plone which i think also installs zope. 

If that has anything to do with it?

---

### Post by nocturn on 2005-03-22
[QUOTE=Insanely]I should probably warn you guys I installed plone which i think also installs zope. 

If that has anything to do with it?[/QUOTE]

You can check which process uses the port with:
```
sudo netstat -lp 
```

---

