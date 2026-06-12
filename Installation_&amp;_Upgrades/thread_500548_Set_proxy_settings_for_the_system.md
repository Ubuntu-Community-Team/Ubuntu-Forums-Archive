---
title: "Set proxy settings for the system"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by rpjanaka on 2007-07-14
i am using Ubuntu 7.04 version and i  am behind a proxy. 
i want to configure my SVN proxy settings. but still i was unable to do it.

in this way for each and every applications i have to set the proxy settings. instead of this are there any way to set the proxy for the system (independent of the application)...?

---

### Post by etank on 2007-07-26
I am behind a proxy server too and am trying to do updates on my system. I can access the internet with pings and firefox but not with apt-get. I have seen some docs point to making changes in /etc/apt/apt.conf but that file does not exist on my system.

---

### Post by etank on 2007-07-26
I found this link [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by Trail on 2008-01-21
You can set an environmental variable, http_proxy, that most CLI applications respect.
Like this:

[http://192.168.1.1:80](http://192.168.1.1:80)

Doesn't work with SVN though :|

---

### Post by torgrot on 2008-01-21
You have tried System Administration Synaptic preferences Network and set the proxy server there?  Or System Preferences Network Proxy?  Do you know what the proxy settings are for your network?  Do you have privileges or an account to access outside web sites?  If you have a windows box that can browse the internet can you see the proxy setting there? 

torgrot

---

