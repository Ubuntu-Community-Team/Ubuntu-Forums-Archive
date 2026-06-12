---
title: "cannot find headers"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by jchoot on 2010-01-27
I'm trying to install headers on my server that are needed to compile VMWare tools. 

I'm running a standard install of hardy heron on amd64.

$ uname -r
2.6.24-19-server

However, despite my search I cannot find the package anywhere:
Package linux-headers-2.6.24-19-server is not available, but is referred to by another package.
E: Package linux-headers-2.6.24-19-server has no installation candidate

---

### Post by pirateghost on 2010-01-27
sudo apt-get install linux-headers-`uname-r`

---

### Post by jchoot on 2010-01-28
> **pirateghost said:**
> sudo apt-get install linux-headers-`uname-r`

I tried that, it doesn't work. 
$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-19-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-headers-2.6.24-19-server has no installation candidate

[http://packages.ubuntu.com/lt/hardy-updates/devel/linux-headers-2.6.24-19-server](http://packages.ubuntu.com/lt/hardy-updates/devel/linux-headers-2.6.24-19-server) returns:
"no such package"

$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-26-xen 2.6.24-26.64
  linux-headers-2.6.24-26-server 2.6.24-26.64
  linux-headers-2.6.24-26-rt 2.6.24-26.64
  linux-headers-2.6.24-26-openvz 2.6.24-26.64
  linux-headers-2.6.24-26-generic 2.6.24-26.64
  linux-headers-2.6.24-26 2.6.24-26.64
  linux-headers-2.6.24-25-xen 2.6.24-25.63
  linux-headers-2.6.24-25-server 2.6.24-25.63
  linux-headers-2.6.24-25-rt 2.6.24-25.63
  linux-headers-2.6.24-25-openvz 2.6.24-25.63
  linux-headers-2.6.24-25-generic 2.6.24-25.63
  linux-headers-2.6.24-25 2.6.24-25.63
  linux-headers-2.6.24-24-xen 2.6.24-24.61
  linux-headers-2.6.24-24-server 2.6.24-24.61
  linux-headers-2.6.24-24-rt 2.6.24-24.61
  linux-headers-2.6.24-24-openvz 2.6.24-24.61
  linux-headers-2.6.24-24-generic 2.6.24-24.61
  linux-headers-2.6.24-24 2.6.24-24.61
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.

---

### Post by jchoot on 2010-01-28
nevermind, just updating the kernel instead

---

