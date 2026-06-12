---
title: "synaptic package manager is unable to connect to the net"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by falcon_whiz on 2007-11-04
hi all, i am able to connect to the internet in mozilla firefox but the synaptic packet manager or for that matter the add/remove program feature is unable to connect to the internet and download new archives. The problem code is: '407 Proxy Authentication' required. I access internet through a proxy server in my institute and i have entered all the proxy details in the connection settings(including the username and password) but still the problem is persisting. Morever the network settings is showing two ips, one for ipv4 and another for ipv6. how can i remove the ipv6.
and i am using feisty 7.04

---

### Post by dcstar on 2007-11-04
> **falcon_whiz said:**
> hi all, i am able to connect to the internet in mozilla firefox but the synaptic packet manager or for that matter the add/remove program feature is unable to connect to the internet and download new archives. The problem code is: '407 Proxy Authentication' required. I access internet through a proxy server in my institute and i have entered all the proxy details in the connection settings(including the username and password) but still the problem is persisting. Morever the network settings is showing two ips, one for ipv4 and another for ipv6. how can i remove the ipv6.
and i am using feisty 7.04

There are separate proxy setting in Synaptic, you have to set those as well.

---

### Post by falcon_whiz on 2007-11-04
hi, i have entered the proxy settings alongwith my username and password, inside the synaptic network settings but still the following problem crops up -
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required

---

### Post by dcstar on 2007-11-04
> **falcon_whiz said:**
> hi, i have entered the proxy settings alongwith my username and password, inside the synaptic network settings but still the following problem crops up -
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 407 Proxy Authentication Required
........

Try a reboot.

---

### Post by djpc on 2008-06-02
I have this problem as well and I cannot find where to enter a password except in Firefox and in the network proxy settings and I need to connect to the internet as I have nothing not even codecs

---

