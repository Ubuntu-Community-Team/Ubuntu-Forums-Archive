---
title: "Connection time out to in.archive.ubuntu.com"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by aasthakm on 2011-04-05
Hi,

I am not able to install some software using apt-get install command. The reason is a failure to download from the repositories. Following is one of the messages I receive upon failure:

Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main tk8.5 i386 8.5.8-1
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)

I pinged 111.91.91.37. The ping statistics showed that the server was running, as expected. My network settings are also fine and I am using net on my laptop right now.

I can't understand where the problem is then. Could someone help in this regard?

Thanks,
Aastha.

---

### Post by mörgæs on 2011-04-05
You could try selecting another mirror in Software Sources and reload the package list.

---

