---
title: "Upgrade Problems - 404 File Not Found"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by dr_d on 2006-08-23
Hey there... wow, this is my second run-in with a bug in 2 days... after running ubuntu for over a year with no problems... Recently I got completely hosed by the synaptic bug, and as a result I had to reinstall linux...

Anyways, to the problem at hand: I'm getting a 404 File Not Found when I try to update my system.

```

The following packages will be upgraded:
  xserver-xorg-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3531kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://au.archive.ubuntu.com dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4
  404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb  404 Not Found

```

I read the sticky thread on the xserver bug, and I can't help but wonder if this problem is related... Anyhow, my question is should I just wait for this file to become available or do I have to actually do something to fix the problem??

much appreciated,
dr d

---

### Post by rovernaut on 2006-08-23
I am in the same boat as you. I tried all the web solutions and I get the 404 error.
 I've tried using Aptitude as SU and it starts but then gets the 404 error.
I also tried dselect and it gives me the 404 error.
 And Apt-get also gave me the 404 error.
I hope some one comes up with another fix as I spent a lot of time getting Kubuntu the way I like it and have stuff saved on it.](*,)

---

### Post by dr_d on 2006-08-23
it's all good lads, after like 1/2 hour, it's working without any intervention on my part.

cheers.

---

### Post by mdr on 2006-08-23
I too had this - but changed sources from .au to the US i.e. plain old archive.ubuntu.com.

All then went fine - just a slow mirror issue I would expect....

---

