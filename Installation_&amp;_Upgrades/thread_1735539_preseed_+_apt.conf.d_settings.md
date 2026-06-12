---
title: "preseed + apt.conf.d settings"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Paul Weaver on 2011-04-21
When I build boxes, I do a network boot, and use a preseed file pointing to a local apt-cacher proxy.

This makes my sources.list file look like this:
```
deb http://10.11.14.115:3142/security.ubuntu.com/ubuntu lucid-security universe

```

That generally works fine, however I sometimes get a problem with downloading of release.gpg from one site or another. APT goes into an infinite loop.

The workarround is the following
```

echo 'Acquire::http::Pipeline-Depth "0";' >> /etc/apt/apt.conf.d/99http

```
Which I do as part of the install. Unfortunatly in many cases the install won't complete, because of the infinite loop. 

Is there any way of using the preseed script to pass
"Acquire::http::Pipeline-Depth "0";"

Something like 
```
d-i apt-setup/acquire/http/pipeline-depth 0
```

thanks

---

