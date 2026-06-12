---
title: "Err http://archive.ubuntu.com lucid/main Packages 404 Not Found"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by jj5 on 2011-12-01
Getting a whole heap of 404 errors when I run

 # apt-get update

e.g.

Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  404  Not Found

Is this a temporary problem and I can expect the package repository to be available and online again soon? I tried running apt-get update from another box that uses the same configuration and had no problem.

Wondering if this could be related to the fact that I've just installed the unattended-upgrades package?

---

### Post by jj5 on 2011-12-01
Nevermind. It was a DNS issue which I've resolved.

---

### Post by crazy bird on 2011-12-01
How did you resolved it? It's nice to provide us with the solution to help out other users with similar issues.

---

### Post by raja.genupula on 2011-12-01
> **jj5 said:**
> Getting a whole heap of 404 errors when I run

 # apt-get update

e.g.

Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  404  Not Found

Is this a temporary problem and I can expect the package repository to be available and online again soon? I tried running apt-get update from another box that uses the same configuration and had no problem.

Wondering if this could be related to the fact that I've just installed the unattended-upgrades package?

change the update manager server going to solve the issue

---

### Post by jj5 on 2011-12-10
> **crazy bird said:**
> How did you resolved it? It's nice to provide us with the solution to help out other users with similar issues.

I forget now. The problem was basically a problem with my DNS server. It wasn't setup to forward queries properly, so when it was queried for "archive.ubuntu.com" it didn't forward the query, rather it matched it to the wild-card DNS record in my DNS zone and then returned the IP address of one of my servers.

---

