---
title: "Getdeb"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by Achilles124 on 2012-02-17
I once tried to install programs from the website getdeb. That worked. 

But I encountered this problem. It automatically updated all my programs I had on my system. And this is something I don't want.

Was that normal? Is there something I can do to prevent that? Is there a way I can download single .deb programs from getdeb?

---

### Post by ottosykora on 2012-02-17
I had quick look at this, and it seems to do what you report.

Either you have to install the getdeb package or install their ppa by hand.

By doing that the the ppa will be included in updates and so what ever they keep in their repo will be updated.
(deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps)

Hmm, not so nice, they could supply single deb files, directly on the website, but this seems not to be the intention for some reason.
To say is also, that distributing single deb packages is not  good practice for some people, as the origin is not known. repos have gpg public key, so one can at least know it came from that repository. But that is about all.

You can disable the ppa entry in your install sources.

---

### Post by Achilles124 on 2012-02-18
Yes, that could be a solution. Thank you for your answer. :)

---

### Post by ottosykora on 2012-02-18
and leave such website out next time...

---

