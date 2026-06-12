---
title: "Preseed and local mirror / apt-proxy"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by Lebowski1 on 2012-08-08
Hi,

im trying to install ubuntu using pxe an preseed, but i run in some problems while using approx as apt-proxy.

At first, preseed and apt-roxy worked for lucid. Approx is working also fine under 12.04, only in connection with preseed i got this problem.

Now i'm using

```

d-i mirror/country string manual
d-i mirror/http/countries string manual
d-i mirror/http/hostname string 10.0.2.101:9999  # aproy
d-i mirror/http/mirror    string    10.0.2.101:9999  # approx
d-i mirror/http/directory string /ubuntu/
d-i mirror/suite string precise 
d-i mirror/http/proxy string

```in my preseed-file.

After installation i used 'debconf-get-selections --install' to find the used values. So i could see, that 
```

d-i mirror/http/mirror

```ist overwritten with
```

d-i mirror/http/mirror  gb.archive.ubuntu.com

```How can i fix this?

---

