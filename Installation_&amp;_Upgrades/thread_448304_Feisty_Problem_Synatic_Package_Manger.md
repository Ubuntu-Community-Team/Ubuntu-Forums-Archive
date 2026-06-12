---
title: "Feisty Problem Synatic Package Manger"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by ReapeX on 2007-05-19
I was following the guide to install automatix2 at
[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p6)

but now when I try updating in terminal I receive the following error:

E: Type 'wget' is not known on line 48 in source list /etc/apt/sources.list
E: Couldn't read list of package sources

I also recieve this error when going to synaptic package manager.
I was also told to report the problem and I doing so now hehe.

Any ideas to correct the problem?  I can reinstall if need be.

---

### Post by ReapeX on 2007-05-19
nevermind just fixed the problem
I went in and viewed the list file 'sources.list'

there were extra entries in the file at the bottom (- line 48 -)  :
"wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

wget http://www.getautomatix.com/keys/automatix2.key"

I removed those entries and I can now update again.

(can't believe I was willing to format lol)

---

