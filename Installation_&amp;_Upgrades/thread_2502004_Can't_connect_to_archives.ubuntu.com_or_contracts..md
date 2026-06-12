---
title: "Can't connect to archives.ubuntu.com or contracts.canonical.com"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by jmk1984 on 2024-10-29
I am getting these errors after a non-networking / fresh installation of Ubuntu Jammy 22.04.  This is preventing cache update and installation of downstream packages.  I notice lots of apparmor denied and errors connecting to contracts.canonical.com.  However, I can telnet / curl to any of the sites over port 443 which means my firewall is working - I just can't curl any canonical site.  Any help is appreciated?


[COLOR=#2FFF12][FONT=&quot]root@hercules:/var/log# apt-get update -y[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]0% [Waiting for headers] [Waiting for headers]^C[/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&quot]root@hercules:/var/log# [/FONT][/COLOR]

---

