---
title: "https websites not working with sqid3"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by x.knight on 2009-12-12
HI all

i have configured squid3 with ubuntu 9.10 sucessfully all http websites are working fine but i m unable to browse https websites please help me in this regards

---

### Post by Barriehie on 2009-12-12
> **x.knight said:**
> HI all

i have configured squid3 with ubuntu 9.10 sucessfully all http websites are working fine but i m unable to browse https websites please help me in this regards

Do you have the https ports enabled in squid.conf???

Barrie

---

### Post by x.knight on 2009-12-12
yes i have enabled 443 port

---

### Post by x.knight on 2009-12-12
below lines are in my squid.conf

acl SSL_ports port 443 563      # https News
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 873         # rsync
acl Safe_ports port 1025-65535  # unregisted ports
acl Safe_ports port 631         # cups
acl Safe_ports port 901         # swat

---

### Post by Barriehie on 2009-12-12
Try adding this to your squid.conf file, or uncomment it if it is.  I'm running 2.6 so my .conf file may be diff. from yours.

```

acl SSL method CONNECT

```

Barrie

---

### Post by x.knight on 2009-12-13
still not working

---

### Post by Barriehie on 2009-12-13
Well, since https is transparent to squid you could tell your browser to not use the proxy server for https connections.

Barrie

---

### Post by Barriehie on 2009-12-18
Did you get it?  Redirect the browser?

Barrie

---

