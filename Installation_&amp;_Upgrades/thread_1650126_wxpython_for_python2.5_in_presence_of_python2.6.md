---
title: "wxpython for python2.5 in presence of python2.6"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Nebelhom on 2010-12-21
Hi folks,

I would like to install wxpython2.8 for python2.5, which I installed as an alternative version in the presence of the standard python2.6 using xubuntu 10.04 lucid lynx (see the [end of this thread for how I did it]("http://ubuntuforums.org/showthread.php?t=1649523")).

how would I do this without the installation going for the standard 2.6 version?

I found some notes to that on the web:

[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

[http://groups.google.com/group/wxpython-users/browse_thread/thread/bf7b53e9028ef8c1](http://groups.google.com/group/wxpython-users/browse_thread/thread/bf7b53e9028ef8c1)


I tried those, but somehow my wxpython installation got borked and would not do anything afterwards. so I completely removed and re-installed it, which solved that. The error messages suggested that it tried to install on top of my python2.6 installations and got confused (sorry, I don't have the exact error messages anymore)

I am still a beginner in the field and the command line is still a bit alien to me, so please don't assume great feats of knowledge. I am, however, able to use google quite well and know the basics, so any pointers as to how I could do this, would be very nice.

Thanks for the help.

---

### Post by Nebelhom on 2010-12-21
bump.

Anyone?

Any help or thoughts are appreciated

---

### Post by dino99 on 2010-12-21
[https://launchpad.net/~fkrull/+archive/deadsnakes](https://launchpad.net/~fkrull/+archive/deadsnakes)

---

### Post by Nebelhom on 2010-12-21
thanks for your input, but I think you misunderstood me. I have python2.5 already installed. The problem arises when I am trying to **install wxpython2.8 into python2.5**.

I cannot get it to install into 2.5 rather than 2.6 (the standard installation)

---

### Post by dino99 on 2010-12-21
> **Nebelhom said:**
> thanks for your input, but I think you misunderstood me. I have python2.5 already installed. The problem arises when I am trying to **install wxpython2.8 into python2.5**.

I cannot get it to install into 2.5 rather than 2.6 (the standard installation)

dont know if you can workaround dependencies conflicts, might be difficult without a custom compiled package.

---

