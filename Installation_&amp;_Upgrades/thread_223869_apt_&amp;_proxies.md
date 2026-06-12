---
title: "apt &amp; proxies"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by burwaco on 2006-07-27
Hello everyone !

I'm a Ubuntu user scince a few weeks now and very happy about it !

But, I have a problem...

Here at work, we use a proxy with username/password to gain acces to the internet, and when I want to use apt to get some new packages, I can't connect. Also, every port exept 80 is blocked by the firewall, is this a problem ?

I'd really like apt to work because I'm missing some of the finest programs...

Thx for any help

burwaco

---

### Post by burwaco on 2006-07-27
I've found this nice tread in the forums:

> Define your connectivity options
--------------------------------------------
If you're connected behind a proxy, you'll need to specify it for Firefox, Synaptic and apt

Firefox: Tools -> options - general tab - network (same as Window Internet Explorer)
Synaptic: categories -> preference - network tab
(enter as username:Password@proxy.com if the proxy is password protected, proxy.com if not. Specify the port)
apt: sudo gedit /etc/apt/apt.conf
include the following (again, if the proxy is not password protected use proxy.com:Port syntax)
----------------------------------
ACQUIRE {
retries "3";
http {
proxy "http://username:Password@proxy.com:Port/";
}
};
----------------------------------
exemples
"http://JohnDoe:Secret@myproxy.com:8080/"
or
"http://myproxy.com:8080/"


The proxy we ise is issued by a proxy.pac, so I downloaded that file and retrieved the proxy url and put my l:p@proxy, but sypaptic nor apt can't resolve the hosts for updating.

What do I do wrong ?

---

### Post by sazu on 2006-07-27
Try this, it worked for me. Backup your /etc/apt/apt.conf and then open it with:

```
sudo nano /etc/apt/apt.conf
```

And remove whatever you have in it, then do apt-get update and try to install. I am behind a proxy as well in my university dorms' network, and the only thing that prevented me from downloading anything was faulty stuff in /etc/apt/apt.conf.

---

### Post by burwaco on 2006-07-27
My apt.conf looks like this:

```

ACQUIRE {
retries "3";
http {
proxy "http://login:password@proxy.com:8080";
}
};

```

I backed it up, empied it, same result: "couldn't resolve host ...ubuntu.org"

Synaptic doesn't work either... what port does synaptic operate on ?

---

### Post by burwaco on 2006-07-27
and...

```

Acquire::http::Proxy http://login:password@proxy.com:8080";

```

result in:

```

E: Syntax error /etc/apt/apt.conf:2: Extra junk at end of file

```

*edit*

there was a syntax error (""), but even without it it doesn't work...


I edited wget's config file, added my proxy in there, and wget works just fine... someone please help me with apt !

*edit*

Found a nice article in the forums about export http_proxy or something, now it works fine...

---

