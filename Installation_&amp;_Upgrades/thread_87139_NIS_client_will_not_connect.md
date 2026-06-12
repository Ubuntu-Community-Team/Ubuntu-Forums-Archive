---
title: "NIS client will not connect"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by ejkeebler on 2005-11-07
I cannot for the life of me get my nis client to connect.

NIS Server (192.168.1.150)

/etc/default/nis
NISSERVER=master
NISCLIENT=false

domainname:
domain.net

/etc/defaultdomain:
domain

ypserv.securenets:
255.255.255.0        192.168.1.0

NIS Client (192.168.1.21)

yp.conf:
ypserver 192.168.1.150

domainname:
domain.net

/etc/defaultdomain:
domain


The client tries ypbind to domain and just hangs and never connects

---

### Post by axels22 on 2007-11-10
Just tryed setting NIS up on my test system and I had the same type of error. Couple of things I had to do to get it to work for me:

1. I found that I had the domain name setup wrong in the /etc/defaultdomain file. I had "domainname.local", but it should of just been "domainname"

2. I also had to add the server ip in the /etc/hosts.allow file.

Another thing I would do just to save in headache is to use just IP addresses instead of DNS names and add the static name entry in the /etc/hosts file. This can leave out DNS being an issue.

GOOD LUCK!

---

