---
title: "New perl breaks some scripts with segfault"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2010-10-12
I got some perl scripts that are broken by the new maverick perl version. I am trying to downgrade without success:
```
pmatos@pm18pc01:~/$ sudo apt-show-versions -a -p perl
perl 5.10.1-12ubuntu2 install ok installed
perl 5.10.1-8ubuntu2  unknown  gb.archive.ubuntu.com
perl 5.10.1-12ubuntu2 maverick gb.archive.ubuntu.com
perl/maverick uptodate 5.10.1-12ubuntu2
pmatos@pm18pc01:~/$ sudo apt-get install perl=5.10.1-8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version ‘5.10.1-8’ for ‘perl’ was not found
```

What am I doing wrong?

---

