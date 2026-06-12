---
title: "Dual boot, outdated guides."
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by zarilion on 2007-05-06
Im trying to install Ubuntu 7.04 Desktop with dual boot on the same drive. But all the guides have another partition window then the one i get :confused: 

Thank's on advance :)

---

### Post by hessiess on 2007-05-06
use gparted to srink the windows partition (is it windows?) by about 5 to 10 gig. then start the instaler select create partitons manualy. make a ext3 with / as mount point and a swap partiton and it should install ok.

at lest, this is what i did

---

### Post by ajgreeny on 2007-05-06
When you get to the partitioning part of the install, the easiest way is to let ubuntu use the "Resize and use the freed space" option.  Then when you move to the next page you can reduce your win partition and use that space for ubuntu.  Have a look at:-
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
which should answer all your questions.  If not, come back and enquire again about anything you don't understand.

---

