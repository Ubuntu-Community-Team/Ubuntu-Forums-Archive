---
title: "Setting up apt proxy without using $http_proxy"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by NutMonkey on 2005-09-01
I just installed Kubuntu at work, behind an authenticating proxy.  Google shows that the way to get apt to work is to set the http_proxy environment variable.  I would prefer not to have my password in an environment variable, is there a config file alternative?  Also, my proxy username has a space in it, will that be a problem?

---

### Post by tonym on 2005-09-01
See the apt.conf [man page](http://www.die.net/doc/linux/man/man5/apt.conf.5.html)

---

### Post by NutMonkey on 2005-09-01
Well, I don't have an apt.conf file..  I created a file /etc/apt/apt.conf.d/01proxy with the contents:

Acquire {
  http::Proxy "http://user:pass@myproxy.com:8080/";
}

(of course with actual user,pass,proxy).  That seems to work, is that the "correct" ubuntu way to do it?

---

