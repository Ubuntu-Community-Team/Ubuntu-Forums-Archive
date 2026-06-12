---
title: "Installing CGAL 4.4 on Ubuntu 14.04"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by onur-cagirici on 2014-06-27
I've been struggling with this issue for 2 days.

I'm trying to install CGAL-4.4 library by following the instructions [here]("http://doc.cgal.org/latest/Manual/installation.html").

However, when I'm trying to execute an example code provided in the site, I get lots of **undefined reference **errors.

Here's what I've tried:

```
cd CGAL-4.4
cmake .
make
```

Since it did not work, I've tried using the options [here]("http://doc.cgal.org/latest/Manual/installation.html#title38"). But still, same errors.

How can I install CGAL 4.4 and use it with Code::Blocks?

---

### Post by steeldriver on 2014-06-27
Do you need 4.4 specifically? 4.2 appears to be available from the Trusty repository

Beyond that, it's hard to suggest what might be wrong without knowing more about the exact errors you're getting (i.e. what symbols are undefined)

---

