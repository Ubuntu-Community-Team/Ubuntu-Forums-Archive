---
title: "linux-image-2.6.35-27-genetic-pae will not update"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by Pantheraleo on 2011-03-05
I'm having problems with updating ubuntu 10.10, and I have tried everything I can think of. when dist-upgrade tries to download the package linux-image-2.6.35-27-gneric-pae_2.6.35-27.48_i386.deb, the download always stalls out indefinitely at 18% complete, and the connection eventually times out. This is the only package that is causing problems. All other packages upgraded fine. Here are the steps I have tried to resolve the problem:

- run apt-get update, and tried with apt-get --fix missing
- apt-get clean
- apt-get autoremove
- apt-get autoclean
- apt-get clean all

- Using a different server in sources.list
- Switching to ftp instead of http

- Rebooting the router the system is connected to.

No matter what I try, the package ultimately stalls at 18% downloaded, and eventually times out (connection failed with http, data socked timed out with ftp).

After that, attempting to run apt-get dist-upgrade again hangs indefinitely at 0% [Waiting for headers], unless I do apt-get clean. If I do that, it will attempt to download the package again, but again, it will reach 18% and then stall until the connection times out.

Any help would be greatly appreciated. I've tried everything I can think of to resolve this, and it's getting extremely frustrating.

---

### Post by Pantheraleo on 2011-03-05
Well, I've found out this is not an apt-get or even an Ubuntu problem. I tried to download the file in a Web browser on my Windows laptop, and it stalls out in the same place. It must be an ISP related problem.

---

