---
title: "Networkmanager and ipsec VPN"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xens on 2009-07-21
Has anybody tried to install the network-manager-strongswan plugin ? I'm really looking forward to it, hope one day to have a simple solution to connect to my VPN without using home made scripts.

The error:

The following packages have umet dependencies:
network-manager-strongswan: Depends: strongswan-nm but it is not installable
Broken packages.

Please support this bug report: [https://launchpad.net/+search?field.text=strongswan-nm](https://launchpad.net/+search?field.text=strongswan-nm)

Thanks, Romain

---

### Post by pferraro on 2009-07-21
Try the packages from this ppa:
[https://launchpad.net/~strongswan/+archive/ppa](https://launchpad.net/~strongswan/+archive/ppa)

---

### Post by xens on 2009-07-22
mhhh theses packages are for intrepid and jaunty, and no updates since march. You think I should try theses.

---

### Post by pferraro on 2009-07-22
> **xens said:**
> mhhh theses packages are for intrepid and jaunty, and no updates since march. You think I should try theses.

Why not?  If they don't work, how would you be worse off?  You can always remove them.

---

### Post by Starks on 2009-07-22
Speaking of VPN, was Cisco NAT traversal ever fixed?

---

### Post by alphacrucis2 on 2009-07-22
Can someone explain the difference between Strongswan and Openswan?

---

### Post by pferraro on 2009-07-22
> **Starks said:**
> Speaking of VPN, was Cisco NAT traversal ever fixed?

What was wrong with it?  I'm using vpnc NAT traversal with no issue.

---

### Post by xens on 2009-07-23
Ok installed with the ppa !

But I can't configure the VPN connexion using a passphrase, have to provide a certificate?

---

