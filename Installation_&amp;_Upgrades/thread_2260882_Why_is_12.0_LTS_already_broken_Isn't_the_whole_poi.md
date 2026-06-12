---
title: "Why is 12.0 LTS already broken? Isn't the whole point of an LTS just that -- to work?"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by bbiandov on 2015-01-14
Why is 12.04.5-server-amd64 LTS already broken? Isn't the whole point of an LTS just that -- to work for an extended period of time?

I am talking about the 64bit Server ISO: ubuntu-12.04.5-server-amd64.iso; fresh install; good luck installing MySQL using apt-get

Fake errors all over when doing simple MySQL install. 

The 32bit ISO still loads MySQL using apt-get

Good work there!

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-client-5.5 (>= 5.5.40-0ubuntu0.12.04.1) but it is not going to be installed
                    Depends: libdbi-perl but it is not installable
                    Recommends: libhtml-template-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by kerry_s on 2015-01-15
so do "sudo apt-get -f install"

---

