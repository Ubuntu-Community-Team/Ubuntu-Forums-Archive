---
title: "apt-get - Main Ubuntu Servers or Ones from Your Region"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by krisdotca on 2011-05-09
Other than the fact that the servers may be closer to you, is there any advantage / disadvantage to using the main Ubuntu servers over the ones in your geographic region?

While troubleshooting a problem on a server, I recently changed all of the references to the ca servers to the main servers - a couple of the old and new lines are shown below.

I'm wondering if I should switch them back or leave them at the main ones.


=== old sources.list ===
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted

=== new source.list ===
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

---

### Post by zvacet on 2011-05-09
Your local server should be faster,but if you are satisfied how main server works for you stay with it.

---

### Post by satanselbow on 2011-05-09
It can on occasion be handy to have a backup - I use the FR or DE servers sometimes and have found them to be faster than the (my default) GB ones.

Won't do any harm - apart from a bit of head scratching if you make a typo :popcorn:

---

### Post by krisdotca on 2011-05-09
Can I safely switch back and forth between the main and regional servers? The specific servers for me would be the CA and main ones.

---

### Post by satanselbow on 2011-05-09
Yep! You can flip about as much as you like to get the best speeds on any given day ;)

You can do it simply through **synaptic > settings > repositories** and choose anywhere in the world you like ;)

---

