---
title: "HOW TO: Setup apt to use an internet proxy"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by draxbear on 2008-05-14
During the installation of Ubuntu Server (Heron) I was prompted to supply an HTTP address string for my local proxy (I'm behind a firewall).

I didn't know what my proxy was at the time so just pressed enter and the install completed successfully.

Unfortunately, I couldn't find anywhere that would tell me how set the proxy up post-installation so figured a few words here says thanks to Ubuntu.

After a lot of [_digging_]("http://ccrma.stanford.edu/planetccrma/man/man5/sources.list.5.html") around I found that this can be set with an environment variable: http_proxy

Example Error from "apt-get update":
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2)  Unable to connect to security.ubuntu.com http:

Solution:
export http_proxy='http://domain\userid:password@crapwinxproxy:80/'

I now am successfully able to acquire updates and patches. If you don't have a crummy windows proxy server you can probably omit the domain name in front of your userid.

---

### Post by decarlo on 2008-06-03
[QUOTE=

Example Error from "apt-get update":
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2)  Unable to connect to security.ubuntu.com http:

Solution:
export http_proxy='http://domain\userid:password@crapwinxproxy:80/'
[/QUOTE]

Im having the same problem with being behind a firewall. Im a noobe here so be nice. lol   Where would i use the "export"? 

Im an intern this summer and they have this Old Sun server laying around and i was told to see what i can do with it but i cant update at all. I installed ubuntu 6.06 server. I can ping google.com and my computer but when i do the apt-get update i get the same error as you did. 

any help would be thankful..

---

