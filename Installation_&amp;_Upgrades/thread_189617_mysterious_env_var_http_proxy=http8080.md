---
title: "mysterious env var http_proxy=http://:8080/"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Emilis on 2006-06-05
Hi,

I've downgraded my system from Breezy to Dapper today.

Now Synaptic fails to connect to repositories. I am behind a proxy, but the configured proxy was working nicely in Synaptic.

I did some investigation and edited /etc/apt/apt.conf to include:
```
Acquire::http::Proxy "http://proxy:port";
```

It was failing even then. After some time I noticed that there was a mysterious environment variable:

```
http_proxy=http://:8080/
```

When I unset it via:

```
$ unset http_proxy
```

apt-get starts working, but not Synaptic.

](*,)

---

### Post by llamakc on 2006-06-05
Thanks for posting this all the same.

---

### Post by chasd on 2006-09-22
This is set by GNOME in the Preferences => Network Proxy. Set to "Direct Connection" to have that variable not set.

---

