---
title: "gcc-4.5.2 in 10.04"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by tanyeun on 2011-02-09
my current gcc version is 4.4.3
follow this [link]("http://superuser.com/questions/236372/how-to-build-g-4-5-2-on-ubuntu-10-04")
I tried to compile gcc-4.5.2
after I finished
> $gcc --version
it was still my previous version
where can I find gcc-4.5.2?

---

### Post by tanyeun on 2011-02-11
I found the answer :popcorn:
[http://gcc.gnu.org/install/finalinstall.html](http://gcc.gnu.org/install/finalinstall.html)
I went to the default path: /user/local/bin
and do the following
> 
$ sudo mv g++ g++-4.5.2
$ sudo mv gcc gcc-4.5.2

Since my shell will search /usr/bin first
and /usr/bin is where my previous gcc locates
as a result,
my new installation will not in effect if I don't change 
the name

---

