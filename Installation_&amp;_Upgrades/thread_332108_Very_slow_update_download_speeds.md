---
title: "Very slow update download speeds"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Tomber on 2007-01-05
Hi,
I'm upgrading my OS, and the download speeds for the updates are ridiculously low: 5-10k/s. When I started the upgrade, the speeds were 200k/s...then after about 400 (of 1032) files it slowed down.

Has anyone experienced something like this? I guess it's the ubuntu servers.

---

### Post by kidders on 2007-01-05
Hi there,

Try switching to a different mirror.

---

### Post by firezip on 2007-01-08
How do you do that?

---

### Post by kidders on 2007-01-09
You can modify the URLs in /etc/apt/sources.list. For instance, mine contains lines like **deb http://ie.archive.ubuntu.com/ubuntu/ edgy universe**.

---

