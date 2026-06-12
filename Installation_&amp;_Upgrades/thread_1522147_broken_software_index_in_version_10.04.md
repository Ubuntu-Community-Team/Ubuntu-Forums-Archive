---
title: "broken software index in version 10.04"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by akhanna7 on 2010-07-01
The "Update Manager" on my laptop reports a "broken software index." I tried
sudo apt-get install -f
to fix the problem, but I get the following error:
dpkg: error processing graphviz-cairo (--remove):
    subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried
sudo aptitude update
   and the partial upgrade option,
but neither seems to work.
Deleting graphviz-cairo through synaptic doesn't work either,
and I feel stuck through all possible ways.

---

### Post by akhanna7 on 2010-07-02
Solved via


sudo rm /var/lib/dpkg/info/graphviz-cairo.post*
sudo  aptitude remove -f graphviz-cairo
 

due to Jon Smith.

---

### Post by akhanna7 on 2010-07-02
Miscredited above. Real credit:


[http://ubuntuforums.org/archive/index.php/t-349486.html](http://ubuntuforums.org/archive/index.php/t-349486.html)

---

### Post by azenquor on 2010-10-24
I installed xplico on Ubuntu 10.04 and when I tried to use sudo apt-get install -f
I get the following result:

```
Removing xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg: error processing xplico (--remove):
 subprocess installed post-removal script returned error exit status 100
Errors were encountered while processing:
 xplico
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Help me please? :confused:

---

### Post by azenquor on 2010-11-10
[SOLVED] Hey, I solved the problem...

Search for the package (search from the File System)  that's giving the problems and then delete them all!

The easiest way is to access the root user!

Happy Blah and God Bless!!

:popcorn:

---

