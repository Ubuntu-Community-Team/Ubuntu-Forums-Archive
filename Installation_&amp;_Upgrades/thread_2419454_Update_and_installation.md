---
title: "Update and installation"
date: 2019-05-22
forum: Installation &amp; Upgrades
---

### Post by cemce-1 on 2019-05-22
Hi guys, this is my first post as I'm in a bit of a rush.
I've installed a apt-mirror for a local repository as the main point. The thing I'm missing is via server, downloading any kind of package, and the same package to be installed in the client. 
Ex: Installing google chrome in server, and then automatically downloading it in the client.

Thanks!

---

### Post by deadflowr on 2019-05-22
Please expand on what you've already done and any guides you have followed.
Also which release of Ubuntu will be useful.

There is simply not enough information to go on.

---

### Post by TheFu on 2019-05-22
I use **[B]apt-cacher-ng**[/B], not apt-mirror.  All the clients point to the caching package server via:
/etc/apt/apt.conf.d/

```
/etc/apt/apt.conf.d$ more 02proxy 
Acquire::http { Proxy "http://istar:3142"; };

```
"istar" is the DNS name for the caching server host.  It automatically pulls requested packages and caches them for other clients. It keeps different releases and different repos separate. If a package isn't requested, then it never gets downloaded.
Every month or so, an expire package task is run to remove unreferenced packages and clean up storage.  Most of my systems are snowflakes, all different, so the cache gets hit only about 65% of the time.

The clients have to request that any package be installed. There isn't any automatic push with this. If you want that, check out ansible or puppet or you can write a custom ssh script like we did in them-thar-olden-days around 1995.

Perhaps wait another day, so someone using apt-mirror can respond?

---

