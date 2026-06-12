---
title: "apt-get noproxy for local addresses"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by pratik.ac on 2007-12-18
there are local repositories in my college. The proxy server doesnot work for local addresses. I got synaptic working by setting ftp.iitb.ac.in under noproxy list. I created /etc/apt/apt.conf with the following lines:
  ACQUIRE{
       http::Proxy "http://usrname:passwd@netmon...:80/";
  }
i need to tell apt-get not to use proxies for ftp.iitb.ac.in.
Can anyone suggest something??
Thanks

---

