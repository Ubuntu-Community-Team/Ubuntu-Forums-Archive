---
title: "Problem with apt-get update"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by qmaq23 on 2011-03-26
Hi,

I am having an issue using apt-get update, I keep getting the error: 407 proxy authentication required. Here is everything I have tried:

1. Set proxy settings in Firefox, and providing the username and password.
2. Changed bash.bashrc in /etc by inserting the line: 
export http_proxy='myusername:mypassword@proxyaddress: portno'
3. Changed proxy settings from System->Preferences->Network Proxy. 
4. Changed proxy settings from Synaptic packet manager.

Also, upon running echo $http_proxy, I get the correct username/password/proxy info. But still I am unable to run apt-get update.

What am I missing here? Any help is greatly appreciated. Thanks.

---

