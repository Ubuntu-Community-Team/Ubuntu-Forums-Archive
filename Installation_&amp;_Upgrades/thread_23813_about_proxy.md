---
title: "about proxy"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by wxm505 on 2005-04-04
I live in uni and use proxy.
When I upgraded from warty to hoary by synaptic
I can connet all the http servers but ftp.
When I chose apt-get update , I can connect all the
ftp servers but http.
There may be something wrong about the proxy setting.
I did set the proxy correctly because I can access internet
successfully. 
Any help??

---

### Post by ymeyer on 2005-04-07
install and configure tsocks

then:

sudo tsocks apt-get .....

or

sudo tsocks synaptic

---

