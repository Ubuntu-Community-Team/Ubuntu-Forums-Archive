---
title: "Repositories and proxies."
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Herks on 2006-06-29
Hi

Know this prob sounds a bit off, but I am having problems adding repositories, and doing updates. When I click on the reload button, i get: 

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 407 Proxy Authentication Required

I have put the proxy in Synaptic, (under settings/prefrences/network)but nowhere is there a space to put in authentication details. I have had a look around the system for various places to put it (theres a place in system/prefrences/Network Proxy and if I run gxonf-editor) but still I get the same error.

Please could some one tell me where I am going wrong here?

Thanks!

---

### Post by kostkon on 2006-06-29
Try to put in Synaptic in the Proxy field something in this form:

```
username:password@proxy
```

maybe it'll work.

EDIT: use of CODE tags.

---

### Post by Herks on 2006-06-29
[QUOTE=kostkon]Try to put in Synaptic in the Proxy field something in this form:

```
username:password@proxy
```

maybe it'll work.

EDIT: use of CODE tags.[/QUOTE]


Thanks! I tried different variations of it:
username:passwd@0.0.0.0
0.0.0.0:username:passwd
0.0.0.0@username:passwd

All with the same results.......Proxy Authentication required. Everything else works fine, internet, email,only the automated stuff like repositories and auto updates. Also had the same error message when trying to install new software through Add/Remove.Complains about the list being outdated, then gives me the same error.

---

### Post by Herks on 2006-07-07
Thanks for help. I tried it out but it didnt work. I ended up reinstalling Dapper and thats where I found the error of my ways!

During installation, I was asked to supply a proxy,username and password. I set those up and it all works fine now. It appears that the proxy I set up there is the /etc/apt file. When I first had the problem, I must have been putting in the wrong format or something in the apt file.

Anyways, its working, thanks for the awesome site!

---

