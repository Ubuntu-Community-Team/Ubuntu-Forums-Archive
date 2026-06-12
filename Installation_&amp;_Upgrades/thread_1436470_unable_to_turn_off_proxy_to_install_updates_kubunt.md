---
title: "unable to turn off proxy to install updates kubuntu"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by ILuvMontyPython on 2010-03-22
I have Kubuntu 9.10 and i cant update anything because I have a proxy set up. and I cant figure out how to turn it off. I did turn it off through synaptic but its still turned on. 

this is what comes out when I try to install updates through kpackagekit

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.4ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.4ubuntu2.1_i386.deb) Could not resolve 'proxy.name.org'

---

### Post by lemming465 on 2010-03-25
Two semi-random stabs in the dark:

1) check that you don't have an http_proxy environment variable, e.g. "echo $http_proxy" should be empty.  Do "unset http_proxy" if you have something.

2) check that /etc/apt/ doesn't have "http:Proxy" statements somewhere, e.g. "egrep -i -r http:Proxy /etc/apt shouldn't return any hits.  Put a comment character ("#") in front of any you do find with your favorite text editor (kate? nano? vim? emacs?).

---

### Post by fufyr4ik on 2010-03-25
I have the same problem since quite some time and still could not figure out how to solve it! Any advice would be highly appreciated! The suggestions by lemming465 didn't work. No proxy entries anywhere.

---

### Post by meadmarc on 2011-10-04
THANK YOU!   

I did a 

unset http_proxy

on the command line, and I have synaptic back.  Thanks, thanks, thanks, messing around with squid, uninstalled it, and could never get rid of the settings with the GUI in Gnome.

---

