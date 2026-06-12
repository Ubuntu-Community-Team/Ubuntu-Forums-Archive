---
title: "apt-get autoremove does not behave like apt-get  remove"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by adityakavoor on 2008-06-01
**apt-get remove <package name>**

If the user forgets the package name, he can type 2 letters and press <tab> and then apt-get completes it.

Why does'nt **apt-get autoremove <package name>** behave in the same manner ?

This is so irritating ?

Any solution for this ?:(

---

### Post by zvacet on 2008-06-01
> Any solution for this ? 

No,because these are two different commands.I will quote **man apt-get**

>  remove
           remove is identical to install except that packages are removed
           instead of installed. If a plus sign is appended to the package
           name (with no intervening space), the identified package will be
           installed instead of removed.


>  autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by aysiu on 2008-06-01
Maybe file a bug report?

---

### Post by kerry_s on 2008-06-01
never mind

---

### Post by kellemes on 2008-06-01
> **adityakavoor said:**
> **apt-get remove <package name>**

If the user forgets the package name, he can type 2 letters and press <tab> and then apt-get completes it.

Why does'nt **apt-get autoremove <package name>** behave in the same manner ?

This is so irritating ?

Any solution for this ?:(

autoremove doesn't need a packagename..
it's run like so..
```
apt-get autoremove
```

It's purpose is explained by zvacet.

---

### Post by adityakavoor on 2008-06-01
So does this qualify to be a valid bug ?

---

### Post by adityakavoor on 2008-06-01
Everywhere in this forum, *autoremove* is suggested in place if using 

*remove* since it would remove all unwanted dependencies. So, not many 

people would be using *remove*.

So, it would really help if this is fixed.

---

