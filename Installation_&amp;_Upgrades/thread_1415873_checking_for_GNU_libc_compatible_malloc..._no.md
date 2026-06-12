---
title: "checking for GNU libc compatible malloc... no"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by nicolas902 on 2010-02-25
Hi,

I have been trying to fix this problem for 3 days, any ideas before I jump through the window (not the bill gates one)?

I am using ubuntu 9.10 and running a ./configure.

Many thanks

> 
checking for GNU libc compatible malloc... no


---

### Post by gmargo on 2010-02-26
Have you installed the **build-essential** package?

---

### Post by nicolas902 on 2010-02-26
yes

---

### Post by nicolas902 on 2010-03-03
Here is the solution:

./configure CFLAGS="-m32" CXXFLAGS="-m32

---

