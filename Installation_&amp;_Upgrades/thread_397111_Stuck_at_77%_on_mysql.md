---
title: "Stuck at 77% on mysql"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by bodeman72 on 2007-03-30
I'm setting up a lamp server on the dapper drake server distro, and am trying to get mysql installed on it the problem is i've tried to get version 5 on and the deb files client,common,shared libraries, headers and libraries download fine but the download of server gets stuck at 77%, the bit rate starts to nosedive from 147kb once it gets to 75%. So i tried to download mysql 4 but the same problem occurs only with the client deb instead of the server deb. Since this is a remote server and im using putty on my local winbox ive even downloaded the debs to my winbox and tried to ftp them from my winbox to the server, still the same situation mysql4 client gets stuck and mysql 5 server gets stuck. 

Ps. I'm downloading the debs directly because apt-get is throwing timeouts on 1 out of every 15 files.

   The remote server machine's nic is hooked directly to T1 tranciever, there are no proxies.

---

