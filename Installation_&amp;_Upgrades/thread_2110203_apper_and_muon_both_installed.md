---
title: "apper and muon both installed"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by monkblah on 2013-01-29
Hi,

Using kubuntu. Since I did a dist-upgrade to 12.04, somehow I now have both apper and muon installed on my system for some reason. 

I would like to remove one of them. How can I safely do so? Presumably apt-get remove apper would work, but can I also remove kpackagekit? Are there any other packages I can remove?

---

### Post by monkblah on 2013-02-04
Any ideas?

---

### Post by monkblah on 2013-02-21
Just an update to help anyone else who has this problem -- I ended up doing

sudo apt-get --purge remove apper

which automatically also removed kpackagekit, so now I just have muon doing the updating job.

---

### Post by csillva on 2013-02-23
I like updating my system manually from the command line. I actually use aptitude for the job, it has a nice ncurses interface, lets you easily explore what packages are installed, depend on others, are upgradeable, etc. 
> sudo aptitude
I only mention this because you can actually remove muon, and all Ubuntu related update packages.

---

