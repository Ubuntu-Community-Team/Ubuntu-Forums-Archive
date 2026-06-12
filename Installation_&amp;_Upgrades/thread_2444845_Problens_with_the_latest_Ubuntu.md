---
title: "Problens with the latest Ubuntu"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by chris-herrnberger on 2020-06-05
Greets 

Not sure what broke but having issues with latest Ubuntu and clueless how to fix it. Have tried, several  instruction sets but nothing seems to clean up the system . Any advise would be appreciated. Many thanks in advance for the help. Best regards



Errors were encountered while proces
sing:
 cups
 cups-bsd
 tzdata
 apparmor
 ca-certificates
 libpam-systemd:amd64
 xserver-xorg-legacy
 google-chrome-stable
 ubuntu-minimal
 network-manager
 ubuntu-standard
 network-manager-config-connectivity-ubuntu

Now this error message  has persisted over serveal jupdate. Cant remove individual packages as affraid may break the system. 

Thanks

---

### Post by lazyteddy on 2020-06-05
What happens if you do
```
sudo dpkg --configure -a
```
?

---

