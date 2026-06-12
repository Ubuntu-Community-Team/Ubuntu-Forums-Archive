---
title: "Adding sources for apt-get"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by pratzabrat on 2006-06-09
I have tried to tip toe along some tutorials, but some of the crucial apt-get install commands dont work. As an error message I get this:
> This may mean that the package is missing, has been obsoleted, or
is only available from another source
So I feel there are other sites where I can dl the packages from. If so how do I configure it. Thanks.

---

### Post by taurus on 2006-06-09
Make sure you remove the # sign in front of universe & multiuverse in /etc/apt/sources.list.  If you are not sure about a package, use synaptic to search for it...  You can get to synaptic by System -> Administration.

---

