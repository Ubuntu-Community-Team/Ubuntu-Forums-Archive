---
title: "missing: init once was lost, but now is found"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by lusth on 2007-01-08
Hi all,

I upgraded from dapper to edgy and my /sbin/init file went missing for some reason. After much frustration, I figured out to boot off my Dapper Live CD, mount my hard drive, and then copy the Live CD /sbin/init to my hard drive's /sbin/init. Rebooted from the hard drive and, viola (or bassoon), I was up and running!

Question: does having a Dapper Drake init (from an earlier kernel) mixed in with my Edgy Eft distro pose any problems? If so, what is the easiest path to getting the correct init?

john

---

### Post by hal10000 on 2007-01-08
You should install the upstart package, which provides the new init system for edgy.

---

