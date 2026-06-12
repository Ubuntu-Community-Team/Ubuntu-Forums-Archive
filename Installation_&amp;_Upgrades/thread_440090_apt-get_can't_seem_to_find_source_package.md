---
title: "apt-get can't seem to find source package"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Daniel_Walker on 2007-05-11
Here's a curious one. While trying to build a customised php5-mssql package, following these steps:
[http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/](http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/)
... the job runs fine, on one server, but on another server, on the same network, with the same set of repositories in the sources.list, I get *'E: Unable to find a source package for php5'* when I run *'apt-get source php5'*. I run an apt-get update on it and I see it connecting to the server where it should be finding the source package.

It's clearly been a long day, and my brain is fried. Any suggestions as to what I'm missing?

---

### Post by mazirian on 2007-05-11
So, you're sure you have a "deb-src" prefixing the relevant repository?  Ok, that sounds cheeky, but it's worth double checking. Ok, so that's a problem that needs fixing, but you could always copy over the downloaded source package fom the server that was able to obtain it.

---

### Post by Daniel_Walker on 2007-05-14
Thanks for the reply. Still no fix, so it has to be a network problem.

> **mazirian said:**
> you could always copy over the downloaded source package fom the server that was able to obtain it.

Unoftunately, that would have worked, in that it gives me the source code, but the apt-get 'build-dep' stage still needs to be able to access the online source repository, as far as I can see.

---

