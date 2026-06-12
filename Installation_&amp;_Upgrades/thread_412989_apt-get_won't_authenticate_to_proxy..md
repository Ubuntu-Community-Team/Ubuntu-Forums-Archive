---
title: "apt-get won't authenticate to proxy."
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Kelmar on 2007-04-18
I've tried everything I can find and a few variations, but I cannot get Synaptic or apt-get to authenticate to our proxy server.

Here's what I've tried:
In Synaptic, I've tried setting the HTTP and FTP proxy fields to the same values of:
windomain\user:password@ipaddress
windomain%5Cuser:password@ipaddress
user:password@ipaddress
ipaddress

I've also tried the equivalent settings in the /etc/apt/apt.conf file, as well as the http_proxy and ftp_proxy environment variables.

I have also tried removing the FTP proxy settings, or changing the case of the domain name and user name to various combinations, and this doesn't seem to work either.

The system is running Xubuntu 6.10, and is behind an IPCop Proxy server.  Firefox is able to connect to the apt-get URLs fine, as is my Windows machine; so I know its not a matter of me simply being locked out.

Thanks for the help.

---

