---
title: "PHP5, mysql, and gd. Possible together?"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by lelnet on 2007-06-10
This may seem like a really stupid question, but I have to ask...is it possible to install php5 from apt-get in such a way that both the mysql extension and the gd extension are available at the same time? I know I can build it from source, but I'd like to keep as much as possible of the installed software within the apt system.

My problem is that, whenever I install php5-gd, it disables the mysql extension. And when I try to fix this by installing php5-mysql, it re-enables mysql but disables gd, despite the fact that php5-gd still shows as installed.

Am I missing a really obvious solution to this?

Anyone who's got a CAPTCHA-based antispam add-on to WordPress working on their [xk]ubuntu server must already know how to do this, because that's what I'm trying and failing to do.

---

