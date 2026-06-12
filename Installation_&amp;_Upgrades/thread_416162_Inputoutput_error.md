---
title: "Input/output error"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by albaine on 2007-04-20
Just upgraded by doing 

$ sudo do-release-upgrade

Now I have a problem when I ssh to the box:

$ vim
-bash: /usr/bin/vim: Input/output error
$ lsof
-bash: /usr/bin/lsof: Input/output error
$ wc junk.txt
-bash: /usr/bin/wc: Input/output error

And it's the same for every program in /usr/bin.  Any ideas?  Repeat, this is an ssh session.

Thanks,

Andrew

---

