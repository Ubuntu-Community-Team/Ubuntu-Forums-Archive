---
title: "Cluster PC's"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2007-05-03
How hard would it be to cluster a laptop with a desktop? ; if at all possible? Are there any how'tos for this.?

---

### Post by mozetti on 2007-05-03
I don't think you're going to gain a whole lot with a 2 PC cluster. Clustering is usually done several magnitudes larger than this. I don't know much about it or how to do it, but I wanted to point that out. Now, if you're doing it just for fun, COOL!

I'd suggest searching for some info about beowulf.

---

### Post by raffytaffy on 2007-05-03
i wanted to try for experience factor...to learn. ty for your suggestion

---

### Post by iammeagain on 2007-05-16
I was wondering sorta the same thing, only like 2 to 4 pcs. It is a little project for school, just for the experience of setting up clusters. Have you found anything helpful on how to cluster pcs?

---

### Post by tutomlin on 2007-06-11
If you plan to write your own cluster aware programs check out 
[http://www.clustermonkey.net/](http://www.clustermonkey.net/)

otherwise I'd look into OpenMosix or Kerrighed, which will migrate processes from overloaded computers to those with more free resources.  

[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
[http://openmosix.sourceforge.net/](http://openmosix.sourceforge.net/)

OpenMosix is still stuck in 2.4 kernel land which apparently doesn't really play well with the recent releases of Ubuntu, but as far as I know Kerrighed should do fine. (Kerrighed SMP release is slated for july so if you have a dual core you might want to wait till then)

Hope that helps

Tucker

---

