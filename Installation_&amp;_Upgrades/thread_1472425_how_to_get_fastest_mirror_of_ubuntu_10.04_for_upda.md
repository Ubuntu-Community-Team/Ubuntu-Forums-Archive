---
title: "how to get fastest mirror of ubuntu 10.04 for update and upgrade?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by feige on 2010-05-04
you can edit the so-called source list file:

/etc/apt/source.list 

manually or run "sudo software-properties-gtk" to test mirror by response speed and choose the fastest.

I recommend a better way to get fastest mirror which not just by response speed but also by average download speed(mirror's throughput),the defect is that this testing may taking more time and more network flow.

[http://www.ubuntu9.com](http://www.ubuntu9.com) is a website aims to get fastest mirror for Ubuntu but searching available mirror in network and testing them by download speed .

Noted that this site's in US,so the speed testing result would be more useful if you're in US. You can simply just download the fastest mirror's source list file and copy it to /etc/apt/source.list (or overwrite it but remember backup original file).

---

