---
title: "Failed to fetch url: 404  Not Found [IP: 91.189.88.30 80]"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2012-01-14
I am trying to add a ppa for Ubuntu-Remix-Tools and I get the same IP address error. I added the key as well so I am at a loss what I need to do?

Actually I just noticed although I added the PPA it's to download the packages from 

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe 

Any help please?

---

### Post by dino99 on 2012-01-14
maybe that ppa is down, check it with google

whois 91.189.88.30

---

### Post by Old_Grey_Wolf on 2012-01-14
Assuming that the url you posted is close to correct, the url should be ```
http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/
```.

You are missing the "/dists" part.

I'm not sure this will help. I couldn't find "Ubuntu-Remix-Tools" using a Google search.

---

