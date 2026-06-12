---
title: "libstdc++ installation problem"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by nikhilneela on 2011-09-03
Hi All,
       when i use sudo apt-get install libstdc++ i get the following error. How can i fix this? I am using ubuntu 10.10 Maverick Meerkat.


nikhil@nikhil-Inspiron-N5010:~/AndroidPro$ sudo apt-get install libstdc++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libstdc++6' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-doc' for regex 'libstdc+'
Note, selecting 'libstdc++2.10-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.8-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-glibc2.1-dev' for regex 'libstdc+'
Note, selecting 'libstdc++3.0-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-pic-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' instead of 'libstdc++6-armel-dcv1'
libstdc++6 is already the newest version.
libstdc++6-4.4-dev is already the newest version.
libstdc++6-4.5-dbg is already the newest version.
libstdc++6-4.5-dev is already the newest version.
libstdc++6-4.3-dev is already the newest version.
libstdc++6-4.3-dev set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libstdc++6-4.4-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.4-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.5-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.4-14ubuntu5 is to be installed
 libstdc++6-4.5-dbg-armel-cross : Conflicts: libstdc++6-4.4-dbg-armel-cross but 4.4.4-14ubuntu4 is to be installed
 libstdc++6-4.5-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-doc but 4.4.4-14ubuntu5 is to be installed
E: Broken packages

---

### Post by agillator on 2011-09-03
Try using synaptic to install the version you need and see if you get the same or similar errors. I suspect trying to install ALL versions is your problem. Looking at synaptic you will see there are many versions available and I'll bet some conflict with others.

---

