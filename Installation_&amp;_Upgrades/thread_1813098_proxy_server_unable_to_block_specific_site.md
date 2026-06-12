---
title: "proxy server unable to block specific site"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by amitley on 2011-07-27
I have installed proxy server on ubuntu.I have done every process which is needed to establish proxy server.internet is also working fine through proxy but the sites which needs to be blocked it is not blocking.it is opening.I have made entry of sites which i needed to be blocked in block_dstdomain file in proxy.

 will anybody tell me solution of this?

---

### Post by dino99 on 2011-07-27
you may block a range of urls for the same site
iplist/moblock & /etc/denyhosts are other ways to do it, and of course ufw too.

---

