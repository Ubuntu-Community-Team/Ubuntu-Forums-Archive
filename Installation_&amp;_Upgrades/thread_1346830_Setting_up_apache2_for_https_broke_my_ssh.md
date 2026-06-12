---
title: "Setting up apache2 for https broke my ssh"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by gravlax on 2009-12-05
Hello,

I installed ubuntu server 9.10 with the full lamp stack. I've added a few other apps including ssh. The ssh daemon was working fine. I could access the server via ssh from local hosts on the private network, and from the Internet using the public IP.

Today I installed MediaWiki, which included setting up apache for SSL. I created a self signed certificate, and can now access my wiki by visiting [https://servername/mediawiki](https://servername/mediawiki)

However, I can no longer ssh to the system from the Internet (public IP). I get the "cannot connect to port 22, connection refused" error. Surprisingly, to me, I can still connect using ssh from hosts on the local LAN. I've deleted the .ssh/known_hosts on my system, but still no luck.

Any ideas?

---

### Post by gravlax on 2009-12-05
Hmmm...still having issues. I've enabled telnet to I have a back door into the system in case I break the ability to ssh in locally. The firewall isn't passing telnet, so I am safe there.

I ran the command "sudo apt-get remove openssh-server" followed by "sudo apt-get install openssh-server". If I understand correctly, this should have uninstalled and reinstalled creating new keys and setting the configs back to default.

Any ideas on why a system would only allow local ssh access? (from its own subnet)

I am sure the firewall is open and NAT is configured correctly, since it used to work, and since it is available from the Internet via HTTP, HTTPS, FTP, etc.

---

