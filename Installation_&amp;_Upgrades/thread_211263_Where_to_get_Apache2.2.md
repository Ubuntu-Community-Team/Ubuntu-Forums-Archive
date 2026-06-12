---
title: "Where to get Apache2.2"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by anatolik on 2006-07-08
Hi, All.

I am trying to install Rails+Mongrel on my Drapper server. And as described here [http://blog.codahale.com/2006/06/19/time-for-a-grown-up-server-rails-mongrel-apache-capistrano-and-you/](http://blog.codahale.com/2006/06/19/time-for-a-grown-up-server-rails-mongrel-apache-capistrano-and-you/) it is requires Apache2.2 (because of new mod_balancer)

But I cant find Apache2.2 in Ubuntu package repository. But why? Apache 2.2 have been existing for a long time already. Could anybody point me where to get package. In "testing" state ot in "unstable".

I dont want to build Apache from sources ](*,)

---

### Post by atoponce on 2006-07-08
> **anatolik said:**
> Hi, All.

I am trying to install Rails+Mongrel on my Drapper server. And as described here [http://blog.codahale.com/2006/06/19/time-for-a-grown-up-server-rails-mongrel-apache-capistrano-and-you/](http://blog.codahale.com/2006/06/19/time-for-a-grown-up-server-rails-mongrel-apache-capistrano-and-you/) it is requires Apache2.2 (because of new mod_balancer)

But I cant find Apache2.2 in Ubuntu package repository. But why? Apache 2.2 have been existing for a long time already. Could anybody point me where to get package. In "testing" state ot in "unstable".

I dont want to build Apache from sources ](*,) 2.2 was just released last December, and was not added to the Dapper repos.  Ubuntu Dapper isn't meant to be "bleeding edge", just current.  I bet it will be in Edgy.  You can get binaries off of the Apache site that are in tar.gz format.

---

