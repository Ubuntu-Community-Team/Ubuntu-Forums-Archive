---
title: "apt cache using approx, apt-proxy and dapper or edgy - Work around"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by moopere on 2006-08-12
Trying to use apt-proxy, approx or other similar local cache systems to update all your machines?  Can't get it to work on new installs of Dapper or Edgy but it _does_ work on warty, hoary, breezy or Dapper upgrades?

Theres a problem with new installs of dapper and edgy - I found the answer (work around) only by scouring the dev pages of approx.

Open a terminal as root, type export http_proxy=

This will clear out a problem with fake/wrong http proxy setting in the environment (or the bash interpreter I'm not sure).  You can't see anything in the environment (by using set anyway) but its there.  Clearing the http_proxy will let you use

apt-get update

with a sources.list pointing to your local cache again.

Note, if you have your sources.list pointing at an actual repository you won't even know the above problem exists as it works normally.  This will only affect those users trying to cache .deb packages by one of the common caching mechanisms (approx, apt-proxy).

Cheers and good luck,
Craig

---

### Post by Skerit on 2008-03-25
To use something like approx or apt-proxydon't all the systems have to be using the same version?

So, should I have a gutsy & a heron machine things would probably go wrong, right?

Edit: Ohw, apparantly they won't.. Smart system

---

