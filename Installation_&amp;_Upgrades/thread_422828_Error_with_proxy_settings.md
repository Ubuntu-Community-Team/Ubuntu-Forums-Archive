---
title: "Error with proxy settings"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by abrdats on 2007-04-25
I'm just have installed Ubuntu server (version 7.04) I also installed the SSL Server.

When I'm using the command apt-get update the following error message is showing up:

Proxy Error ( The ISA Server denies the specified Uniform Resource Locator (URL).  )

I'm looking for several hours, but cannot find anything useful

In the file /etc/apt/apt.conf the following line is set:

Acquire::http::Proxy "http://domain\user:password@proxy.xxx.xxx:portnumber/";

Please help me to get my connection from the server

---

