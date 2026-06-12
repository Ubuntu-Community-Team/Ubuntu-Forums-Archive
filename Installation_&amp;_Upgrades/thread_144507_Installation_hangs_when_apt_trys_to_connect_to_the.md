---
title: "Installation hangs when apt trys to connect to the internet"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by kevykev on 2006-03-14
Hi, 

Im trying to install ubuntu on a vmware server running on windows. When
apt tries to connect to the network, the installer hangs. Presumably this
is because i'm behind a firewall and all external network access is through
a proxy server. So I was wondering if it is possible to set the proxy server
for the installation (or to disable apt trying to connect to the internet 
until after installation). 

Can you set the proxy server by doing an "expert" install, grabbing a shell
and setting http_proxy in some file somewhere, or by passing it to 
the bootloader or something like that?

Thanks for any help,
Kevin

---

### Post by kevykev on 2006-03-15
To answer my own question, the expert install actually prompts you for a proxy server.. nice. The regular installer probably shouldn't crash when it cant access the repository though...

---

