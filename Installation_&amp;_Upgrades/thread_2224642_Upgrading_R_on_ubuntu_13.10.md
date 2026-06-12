---
title: "Upgrading R on ubuntu 13.10"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by ebarongo82 on 2014-05-17
I am following instructions as given here [http://ubuntuforums.org/showthread.php?t=2127394](http://ubuntuforums.org/showthread.php?t=2127394) to upgrade my R on Ubuntu 13.10 (Saucy) but I am not going any far with this code:
```
~$ sudo add-apt-repository "deb http://cran.mirror.ac.za/bin/linux/ubuntu/saucy/"
```

when I get:
```
'deb http://cran.mirror.ac.za/bin/linux/ubuntu/saucy/' invalid
```

What should I do?

---

### Post by Ubi_one_2014 on 2014-05-17
looks to me that you have to do:
```
sudo add-apt-repository "deb http://cran.stat.ucla.edu/bin/linux/ubuntu saucy/"
```

---

### Post by ebarongo82 on 2014-05-17
Thanks. It is solved.

---

